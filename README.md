# **Google API token generator**
用於生成 google api oauth2 的 access_token，目前此 token 的期限似乎是永久的，不確定是為甚麼
# **申請 oAuth2 憑證**
[參考此篇](https://learn.markteaching.com/google-drive-api-%E6%95%99%E5%AD%B8-oauth-2-0-%E6%86%91%E8%AD%89/)  
1. 前往 GCP 後台
2. 前往 `API 和服務` -> `OAuth 同意畫面`
3. 在第一步驟填入應用程式名稱案 email，其他都可以跳過，完成後按儲存
4. 前往憑證頁，按下`建立憑證` -> `OAuth 用戶端 ID`
5. 應用程式類型選擇電腦版應用程式，接著就可以下載憑證
# **Environment**
先安裝
```
npm isntall
```
建立 `config` 資料夾，並把憑證放在裡面並改成你要的名字
```
mkdir config
nano *.json // put your credentials
```
# **usage**
首先選擇要產生 token 的憑證環境
```
export NODE_ENV="wed12345976" // your credential json name
```
填入你想要要求的 scope 到 scope.json
可要求的 scope 可以到下面找  
https://developers.google.com/identity/protocols/oauth2/scopes  
```
/** scope.json**/
[
    "https://www.googleapis.com/auth/drive",
    ...
]
```
完了以後執行
```
npm start
```
執行後會在終端輸出一串網址，按下 `ctrl+左鍵` 打開網址，選擇你要的帳戶進行授權。  
**<strong>**要先把該帳戶加到專案中的測試使用者(`API 和服務` -> `OAuth 同意畫面` -> `測試使用者`)才能進行授權，否則會告訴你403**</strong>**  
授權後會得到一串 code ，把 code 複製下來貼到終端按 enter 就會生成 token.json 了。