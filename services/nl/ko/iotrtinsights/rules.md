---

copyright:
  years: 2015,2016

---

{:shortdesc: .shortdesc}

# 규칙 작성 및 경보에 대한 응답 {: #rules}

분석 규칙을 사용하여 디바이스에 대한 경보와 알림을 설정하십시오. 예를 들어, 디바이스의 온도 센서가 비정상적으로 높은 온도를 등록하면 디바이스 대시보드에 경보를 추가하고 관리자에게 이메일을 발송하는 규칙을 작성할 수 있습니다.
{: shortdesc}

자산 맵핑과 같은 컨텍스트 매개변수나 데이터 포인트를 정적 값, 기타 데이터 포인트 또는 컨텍스트 매개변수와 비교하는 조건을 포함하는 규칙을 사용할 수 있습니다.

>**참고:** {{site.data.keyword.iotrtinsights_short}}의 무료 플랜 인스턴스를 사용할 경우 모든 규칙은 1시간 후에 자동으로 비활성화됩니다. 규칙을 수동으로 다시 활성화할 수 있습니다. 지속적으로 규칙을 적용하려면 유료 사용제로 업그레이드하십시오.

디바이스에 대한 규칙을 작성하려면 다음을 수행하십시오. 
1. {{site.data.keyword.iotrtinsights_short}} 콘솔에서 **분석 > 규칙**으로 이동하십시오.
2. **새 규칙 추가**를 클릭하고, 규칙에 이름을 지정한 후, 설명을 제공하고, 규칙에 대한 메시지 스키마를 선택한 뒤, **다음**을 클릭하십시오.   
3. **확인**을 클릭하여 새 규칙을 작성하십시오. 
3. **선택사항:** 규칙에 대해 경보 우선순위를 선택하십시오.
우선순위는 경보 패널에 표시되는 경보를 분류하는 데 사용됩니다. 기본 우선순위는 낮음입니다. 
3. 규칙 논리를 설정하려면 규칙에 대한 트리거로 사용할 하나 이상의 IF 조건을 추가하십시오.
OR 조건으로 적용하도록 병렬 행에 조건을 추가하거나 AND 조건으로 적용하도록 순차 열에 조건을 추가할 수 있습니다.
**팁:** 디바이스에서 리턴한 일반 값을 확인하려면 **디바이스 > 디바이스 찾아보기**로 이동하여 표시된 실시간 데이터를 보려는 디바이스를 클릭하십시오.
**중요:** 두 개의 데이터 포인트로 구성된 조건을 트리거하거나 순차적으로 결합된 두 개 이상의 데이터 포인트 조건을 트리거하려면 데이터 트리거가 동일한 메시지에 포함되어야 합니다. 둘 이상의 메시지에서 데이터를 수신하면 조건 또는 순차적 조건이 트리거되지 않습니다.   
> **다음은 예제입니다.**   
매개변수 값이 지정된 값보다 클 경우 단순 규칙이 경보를 트리거할 수 있습니다.  
예제: 조건 = `ax>5`  
좀 더 복잡한 규칙은 특정 자산에 맵핑된 디바이스의 매개변수 값이 특정 값을 초과할 때 경보를 트리거할 수 있습니다.  
예제: 조건 = `ax>5 AND asset.assetnum==5001`   
자세한 단계는 [예제: 메시지 스키마와 컨텍스트 매개변수 조건을 사용하여 복잡한 규칙 작성](#complex "예제: 메시지 스키마와 컨텍스트 매개변수 조건을 사용하여 복잡한 규칙 작성")을 참조하십시오.   
4. 규칙에 대해 조건부 트리거 요구사항을 구성하십시오.
일정 기간 동안 규칙에 대해 트리거되는 경보 수를 제어하기 위해 규칙에 대한 조건부 트리거 요구사항을 구성할 수 있습니다.
**중요:**  조건부 트리거는 규칙의 모든 조건에 대해 작동합니다. 예를 들어, 규칙에 5개의 서로 다른 병렬(OR) 조건 세트가 있을 경우, true인 각 조건은 조건부 트리거 계수에 포함됩니다.
규칙에 대한 조건부 트리거를 설정하려면 다음을 수행하십시오. 
 1. 규칙 편집기에서 **조건에 부합할 때마다 트리거** 링크를 클릭하여 조건 대화 상자를 여십시오. 
 2. 규칙과 함께 사용하려는 조건부 트리거를 선택하고 구성하십시오.
 <ul>
 <li>조건에 부합할 때마다 트리거</li>
 <li>M*시간 단위* 동안 N번 조건에 부합할 때 트리거</li>
 </ul>  
조건부 트리거의 좀 더 자세한 설명은 [조건부 트리거](#conditional "조건부 트리거 개요")를 참조하십시오.
5. 규칙 조건에 부합할 때 발생하는 하나 이상의 조치를 작성하거나 선택하십시오.
조치에 대한 추가 정보는 [조치 작성](actions.html#shared "조치 작성")을 참조하십시오.    
 > 예제: 이메일을 전송하는 조치를 사용할 수 있습니다. 다양한 조치 유형에 대한 정보는 [조치 유형](actions.html "조치 유형")을 참조하십시오.
6. 규칙에 문제가 없을 경우 **저장**을 클릭하십시오. 
7. 규칙 페이지에서 ![구성 아이콘](images/gear.png "구성 아이콘")을 클릭하고 **활성화**를 선택하여 규칙을 활성화하십시오. 

규칙이 활성되었습니다. 규칙의 조건에 부합할 경우 경보가 **대시보드 > 개요** 대시보드에 추가되고 규칙 조치가 실행됩니다.

## 조건부 트리거 {: #conditional}

일정 기간 동안 규칙에 대해 트리거되는 경보 수를 제어하기 위해 규칙에 대한 조건부 트리거 요구사항을 구성할 수 있습니다.

메시지 빈도 및 규칙 조건에 따라, 한 번 트리거 조건이 부합하면 규칙이 여러 번 트리거될 수 있습니다. 예를 들어 조건이 `temp >= 90`이고 온도가 증가하여 91도에서 안정되면 규칙이 각 수신 메시지에 대해 트리거됩니다. 규칙이 실행하도록 설정된 조치 및 디바이스 메시지의 빈도에 따라 이는, 예를 들어, 이메일 수신함을 빠르게 가득 채우거나 첫 번째 메시지 외의 추가 값을 제공하지 않는 메시지로 Twitter 피드를 넘치게 할 수 있습니다. 

**중요:**  조건부 트리거는 규칙의 모든 조건에 대해 작동합니다. 예를 들어, 규칙에 5개의 서로 다른 병렬(OR) 조건 세트가 있을 경우, true인 각 조건은 조건부 트리거 계수에 포함됩니다.

조건  | 설명
------------- | -------------
조건에 부합할 때마다 트리거 | 규칙 조건에 부합할 때마다 규칙이 트리거됩니다.
M*일/시간/분/사용자 정의* 동안 N번 조건에 부합할 때 트리거 | 선택한 시간 간격에서 조건이 N번 부합할 때 규칙이 트리거되고, 구성된 기간이 경과할 때까지는 다시 트리거되지 않습니다. </br>예제: 조건부 트리거 요구사항 =`조건이 30분 동안 4번 부합할 때 1번만 트리거`. 디바이스는 5분마다 하나의 새 메시지를 보냅니다. 정오에 온도가 처음으로 90도를 넘어 조건에 부합하게 됩니다. 조건부 트리거 카운터가 시작되지만 규칙은 아직 트리거되지 않습니다. 15분 후 `temp > 90`을 나타내는 세 개의 추가 메시지가 수신되었고 규칙이 트리거됩니다. 규칙은 온도가 얼마이든 또 다른 15분 동안에는 트리거되지 않습니다.

## 예제: 메시지 스키마와 컨텍스트 매개변수 조건을 사용하여 복잡한 규칙 작성 {: #complex}
자산 번호 5001에 맵핑된 IoT 전화 디바이스에 대해 ax 매개변수가 5 값을 초과할 때 경보 대시보드에 경보를 작성하는 더 복잡한 규칙을 작성하려면 다음 단계를 수행하십시오. 
1. **디바이스 > 자산 맵핑 관리**로 이동하고 최소한 하나의 IoT 전화 디바이스를 자산 번호 5001의 자산에 맵핑하십시오.
자세한 단계는 [자산 맵핑](assets.html "자산 맵핑")을 참조하십시오. 
2. **분석**으로 이동하여 **새 규칙 추가**를 클릭하십시오. 
3. 규칙에 설명식 이름 및 설명을 제공하고 사용자의 IoT 디바이스 유형에 대해 작성한 메시지 스키마를 선택하여 규칙을 적용할 디바이스 유형을 지정하십시오.
4. **확인**을 클릭하여 새 규칙을 작성하십시오. 
<!-- 5. Click ![Add icon.](images/rules_plus.png "Add icon") to add an initial condition. -->
6. 새 조건 타일을 클릭하고 초기 조건을 편집하십시오. 
 1. 비교할 피연산자로 **데이터 포인트**를 선택하십시오. 
 2. **ax** 데이터 포인트를 선택하십시오. 
 3. **>** 연산자를 선택하여 첫 번째 피연산자의 값이 두 번째 피연산자의 값보다 클 경우 조건이 true가 되게 하십시오. 
 3. 비교할 피연산자로 **정적 값**을 선택하십시오. 
 4. ax 데이터 포인트와 비교할 값 `5`를 입력하십시오. 
 5.  **확인**을 클릭하여 조건을 추가하십시오. 
5. AND 조건을 추가하려면 ![추가 아이콘](images/rules_plus.png "추가 아이콘")을 클릭하십시오. 이는 첫 번째 조건의 오른쪽에 있습니다. 
6. 새 조건 타일을 클릭하고 조건을 편집하십시오. 
  1. 비교할 피연산자로 **컨텍스트**를 선택하십시오. 
  2. 컨텍스트 매개변수 메뉴에서 **자산** 컨텍스트 스키마 앞에 있는 삼각형을 클릭하여 자산 컨텍스트 매개변수 목록을 펼치십시오.
  3. **ASSETNUM** 컨텍스트 스키마 매개변수를 선택하십시오. 
  3. **==** 연산자를 선택하여 첫 번째와 두 번째 피연산자의 값이 동일할 경우 조건이 true가 되게 하십시오. 
  3. 비교할 피연산자로 **정적 값**을 선택하십시오. 
  4. **ASSETNUM** 컨텍스트 스키마 매개변수와 비교할 값으로 `5001`을 입력하십시오. 
  5.  **확인**을 클릭하여 조건을 작성하십시오. 
7. 기본값인 `조건에 부합할 때마다 트리거` 조건부 트리거를 사용하십시오. 
7. 하나 이상의 조치를 작성하거나 선택하십시오. 
7. 새 규칙을 저장하십시오.
7. 규칙 페이지에서 ![구성 아이콘](images/gear.png "구성 아이콘")을 클릭하고 **활성화**를 선택하여 규칙을 활성화하십시오. 

## 예제: 자산 기반 규칙 작성 {: #asset_rules}

디바이스를 성공적으로 맵핑한 후 자산 세부사항을 사용하는 규칙을 작성할 수 있습니다. 자산에 디바이스를 맵핑하고 데이터 포인트와 자산 정보 모두를 통합하는 규칙을 작성하는 것은 강력한 도구입니다. 

아래 예제에서는 회사 휴대전화를 추적하기 위해 자산을 사용하고 있습니다. 두 개의 자산이 작성되어 휴대전화에 맵핑되었습니다. 자산 5001은 PURCHASEPRICE < 100의 전화에 맵핑되었고 자산 5002는 PURCHASEPRICE >=100의 전화에 맵핑되었습니다. 각 예제에 대한 디바이스 데이터 트리거 조건은  `d.ax>5`이며 이는 이 간단한 예제에서 전화의 갑작스런 가속에 해당합니다(예를 들어, 떨어진 경우). 

자산 5001에 맵핑된 전화가 떨어졌을 때 사용자에게 알리는 두 가지 단순 규칙을 설정할 수 있습니다. 또한 5001에 맵핑되지 않은 전화가 떨어졌을 때 이를 추적하는 규칙을 설정하는 것도 역시 쉽습니다. 이는 5002의 전화 또는 자산에 전혀 맵핑되지 않는 전화가 될 수 있습니다. 

예 | 규칙
------------- | -------------
디바이스가 자산 5001의 일부인 경우에만 규칙 트리거 | IF `d.ax>5` AND  `asset.assetnum==5001` THEN ...
디바이스가 자산 5001의 일부가 아닌 경우에만 규칙 트리거 | IF `d.ax>5` AND  `asset.assetnum!=5001` THEN ...

특정 PURCHASEPRICE의 전화에 대해 트리거하는 규칙을 설정할 수도 있습니다.   

예 | 규칙
------------- | -------------
전화 가격이 100 미만인 경우에만 규칙 트리거 | IF `d.ax>5` AND  `asset.purchaseprice<100` THEN ...
전화 가격이 100 초과인 경우에만 규칙 트리거 | IF `d.ax>5` AND  `asset.purchaseprice>=100` THEN ...

마지막으로 더 복잡한 동작을 위해 이러한 규칙을 결합할 수 있습니다. 

예 | 규칙
------------- | -------------
전화가 자산 5001의 일부(가격이 100 미만)이고 가격이 75보다 높은 경우에만 규칙 트리거 | IF `d.ax>5` AND `asset.assetnum==5001` AND  `asset.purchaseprice>75` THEN ...
전화가 자산 5002의 일부(가격이 100 초과)이고 가격이 200보다 아래인 경우에만 규칙 트리거 | IF `d.ax>5`  AND `asset.assetnum==5002` AND  `asset.purchaseprice<200` THEN ...