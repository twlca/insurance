# Database 定義：volunteers
## 資料表定義
table name: volunteers.members
<hr />
```
id            int(32) primary key auto_increment,      // 資料庫主索引
member_id     varchar(11),                             // 志工證號
name          varchar(14),                             // 姓名
sex           varchar(4),                              // 性別
birthday      date,                                    // 生日
pid           char(10),                                // 身分證字號
address       varchar(100),                            // 住址
phone         varchar(11),                             // 家中電話
mobile        varchar(11),                             // 行動電話
join_date     date,                                    // 加入志願隊日期
specialty     tinyint(2)                               // 專長代碼 (見專長代碼對照表)
education     tinyint(2)                               // 學歷代碼 (朏學歷代碼對照表)
occupation    tinyint(2)                               // 職業代碼 (見職業代碼對照表)
activity      tinyint(9),                              // 活躍狀態
qualification varchar(10),                             // 志工資格
status_quo    varchar(12),                             // 目前狀態 (活躍、離隊、休眠)
options       text());                                 // 各類額外訊息 (見 options data definition reference)
```
### 專長代碼
```
specialty = {
  '01': '家電修理',
  '02': '機械',
  '03': '汽車修護',
  '04': '工藝',
  '05': '刻印',
  '06': '印刷',
  '07': '語文',
  '08': '文書處理',
  '09': '編輯',
  '10': '打字',
  '11': '美工',
  '12': '縫紉/編織',
  '13': '烹飪/烘焙',
  '14': '家事服務',
  '15': '美容/美髮',
  '16': '護理',
  '17': '手工藝',
  '18': '電腦',
  '19': '攝影',
  '20': '團康',
  '21': '管理',
  '22': '會計',
  '23': '作物栽培',
  '24': '農牧(藝)',
  '25': '音樂',
  '26': '體育',
  '27': '心理諮商',
  '28': '駕駛',
  '29': '特殊教育',
  '30': '搬運',
  '31': '房屋修繕',
  '32': '其他'
}
```
### 學歷代碼對照表
```
education = {                                          // 專長代碼表 
  '01': '博士',
  '02': '碩士',
  '03': '大學',
  '04': '專科',
  '05': '高中',
  '06': '國中',
  '07': '職校',
  '08': '小學',
  '09': '其他'
}
```
### 職業代碼
```
occupation = {
  '01': '工商', 
  '02': '公教', 
  '03': '退休',
  '04': '家管', 
  '05': '學生',
  '06': '服務業',
  '07': '其他'                                          // 以 UI 取得職業名稱
}
```
### options data definition reference
#### 各類受訓記錄
```
credentials = {                                        // 各類證書
  basic: {                                             // 基礎訓練
    start_date: str date,                              //  訓練開始日
    end_date: str date,                                //  訓練結束日
    sender: str,                                       //  送訓單位
    hour: str,                                         //  受訓時數
    cred_no: str,                                      //  證書號碼
    img_URI: str _image URI_ }                         //  證書影像網址
  special: {                                           // 特殊訓練
    start_date: str date,                              //  訓練開始日
    end_date: str date,                                //  訓練結束日
    sender: str,                                       //  送訓單位
    hour: str,                                         //  受訓時數
    cred_no: str,                                      //  證書號碼
    img_URI: str _image URI_ }                         //  證書影像網址
  growth: {                                            // 成長訓練
    start_date: str date,                              //  訓練開始日
    end_date: str date,                                //  訓練結束日
    sender: str,                                       //  送訓單位
    hour: str,                                         //  受訓時數
    cred_no: str,                                      //  證書號碼
    img_URI: str _image URI_ }                         //  證書影像網址
  leadership: {                                        // 領導訓練
    start_date: str date,                              //  訓練開始日
    end_date: str date,                                //  訓練結束日
    sender: str,                                       //  送訓單位
    hour: str,                                         //  受訓時數
    cred_no: str,                                      //  證書號碼
    img_URI: str _image URI_ }                         //  證書影像網址
  others: {                                            // (以 UI 取得真正訓練名稱)
    start_date: str date,                              //  訓練開始日
    end_date: str date,                                //  訓練結束日
    sender: str,                                       //  送訓單位
    hour: str,                                         //  受訓時數
    cred_no: str,                                      //  證書號碼
    img_URI: str _image URI_ }                         //  證書影像網址
  brochure: {                                          // 紀錄冊資料
    issuer: str,                                       //  核發紀錄冊單位
    issue_date: str date,                              //  核發紀錄冊日期
    brochure_no: str,                                  //  紀錄冊號碼
    img_URI: str _image URI_ }                         //  證書影像網址
}
```
#### 緊急聯絡訊息
```
urgent_contact = {                                     // 緊急聯絡訊息
  name: str,                                           // 姓名
  phone: str,                                          // 電話 
  mobile: str                                          // 手機
}
```
#### 介紹人
```
introducer = {                                         // 介紹人
  name: str                                            // 姓名
}
```
#### 族群
```
ethnicity = {                                          // 族群
  name: str                                            // 一般, 各族族名，見族名對照表
}
```
#### 宗教
```
religion = {                                           // 宗教
  name: str                                            // 天主教, 基督教, 佛教, 喇嘛教(藏傳佛教)...
}
```
#### 隊中身分
role = {                                               // 隊中身分
  title: str                                           // 隊長、副隊長、組長、小組長、隊員(一般不額外加註)
}

## 服務記錄資料表
### 服務項目代碼表
table name: volunteers.service_record

```
service_items = {
  '01': '身心障礙者福利服務',
  '02': '老人福利服務',
  '03': '婦女福利服務',
  '04': '少年福利服務',
  '05': '兒童福利服務',
  '06': '諮商輔導服務',
  '07': '醫院社會服務',
  '08': '家庭福利服務',
  '09': '社區福利服務',
  '10': '綜合福利服務',
  '99': '其他服務(文化、環保)
}
```

   

