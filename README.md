# Adiscope에서 Reward Callback 수신하기

* 응답받을 Server는 [Adiscope Server Callback API]() 의 규격에 맞추어 생성합니다.
* 응답받을 Server의 URL은 Adiscope Admin Page에 **Callback을 등록합니다**. 외부 사용자는 Adiscope 담당자를 통해서 등록 해 주세요. (Admin에 등록되는 Server Callback의 형태는 *Adiscope Server Callback API* 문서의 Example를 참조해 주세요.)
<br><br>

## Adiscope Server Callback API
|||
|--|--|
|Methods|GET|
|Content-Type|?|
|Accept|?|
|URL Format|https://host.com/path?{URL_PARAMETERS}|

* URL_PARAMETERS는 이하 [Adiscope Server Paramters](https://) 를 참조합니다.
* Example
    * Placeholder의 값은 고정되어있습니다. 이하 응답값에 대한 Key(userID, unit 등...)은 자유로운 포맷으로 사용 할 수 있습니다.
    * https://my-server.com/anypath/transctionID=[TRANSCTION_ID]&signature=[SIGNATURE]&unitID=[UNIT_ID]&userID=[USER_ID]&adid=[ADID]&unit=[REWARD_UNIT]&amount=[AMOUNT]

<br><br>

## Adiscope Server Parameters
|Name|Placeholder|Description|
|--|--|--|
|transctionId|TRANSCTION_ID|고유한 ID값. 중복호출 여부에 사용 할 수 있다.|
|signature|SIGNATURE|Callback 유효성 검증에 사용되는 MD5 HASH 값|
|unitId|UNIT_ID|참여한 광고 UnitID|
|userId|USER_ID|Client에서 setUserID로 설정한 UserID|
|adid|ADID|광고 추적 ID(iOS: IDFA)|
|currency|REWARD_UNIT|보상 화폐 단위|
|amount|REWARD_AMOUNT|보상 지급 수량|

* signature의 검증은 Adiscope Admin Page에서 발급받은 **secretKey**와 Callback의 parameters을 통해 값을 검증하게 됩니다. 외부 사용자는 secretKey를 발급받기 위해서는 Adiscope 담당자를 통해서 발급받아 사용합니다.