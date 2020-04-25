# open-neis-api-python

**현재 급식,학교정보만 가져올수있습니다.**

Api키는 [이곳](https://open.neis.go.kr/)여기서 받으실수있습니다.

## Example

```py
import asyncio
from neispy import lunch, school, sort

key = "Api key paste here"
name="인천기계공업고등학교"

async def main():
    param = await sort.sort_reqarg(key)
    scinfo = await school.schoolinfo(param, name)
    AE, SE = await sort.sort_schoolcode(scinfo)
    lunchinfo = await lunch.lunchinfo(param, AE, SE, 20190102)
    lunchmenu = await sort.sort_lunchmenu(lunchinfo)
    print(lunchmenu)

loop = asyncio.get_event_loop()
loop.run_until_complete(main())

#실행 결과
비빔밥(고)5.13.
계란북어국(고)1.5.6.13.
해시브라운/케찹(고)1.2.12.
배추김치(고)9.
볶음고추장(고)5.6.10.13.
삼색과일
```

## 인자값

|변수명|타입|변수 설명|설명|
|---|-----|------|---------|
|KEY|STRING(필수)|인증키|기본값 : sample key|
|Type|STRING(필수)|호출 문서(xml, json)|기본값 : xml|
|pIndex|INTEGER(필수)|페이지 위치|기본값 : 1(sample key는 1 고정)|
|pSize|INTEGER(필수)|페이지 당 신청 숫자|기본값 : 100(sample key는 5 고정)|