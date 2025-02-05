# 国内如何轻松接入 Claude3 API？一站式聚合平台解决方案

众所周知，由于地理限制，Claude3 并未对国内用户开放，而国内镜像网站的使用成本又高得离谱！因此，团队萌生了一个想法：为什么不创建一个一站式的平台，让用户能够通过单一的接口与多个 AI 模型交互呢？这样，用户可以轻松比较不同模型的表现，并选择最适合的一个。于是，**ChatGPT & Claude3 聚合 API 平台**应运而生。

话不多说，先上截图。从图中可以看到，无论是 ChatGPT 还是 Claude3，该平台都完美支持。

![API 平台截图](https://bbtdd.com/img/95001542320.webp)

通过一个接口即可对接国际主流 AI 模型，兼容性已经处理得妥妥当当，用户无需担心技术细节，直接无脑对接即可。API 文档地址：[api.atalk-ai.com/api](https://api.atalk-ai.com/api#/operations/post-gpt-completions-messages)

![API 接口截图](https://bbtdd.com/img/770539481.webp)

👉 [WildCard | 一分钟注册，轻松订阅海外线上服务](https://bbtdd.com/WildCard)

## 对接方式

### Python

python
import http.client

conn = http.client.HTTPSConnection("api.atalk-ai.com")

payload = "{\n \"messages\": [\n {\n \"role\": \"system\",\n \"content\": \"You are a helpful assistant.\"\n },\n {\n \"role\": \"assistant\",\n \"content\": \"can i help you ?\"\n },\n {\n \"role\": \"user\",\n \"content\": \"Hello!\"\n }\n ],\n \"model\": \"gpt-3.5-turbo\",\n \"max_tokens\": 1000,\n \"stream\": true,\n \"temperature\": 0.2\n}"

headers = {
  'Authorization': "",
  'Content-Type': "application/json"
}

conn.request("POST", "/gpt/completions", payload, headers)

res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))


### Java

java
AsyncHttpClient client = new DefaultAsyncHttpClient();

client.prepare("POST", "https://api.atalk-ai.com/gpt/completions")
  .setHeader("Authorization", "")
  .setHeader("Content-Type", "application/json")
  .setBody("{\n \"messages\": [\n {\n \"role\": \"system\",\n \"content\": \"You are a helpful assistant.\"\n },\n {\n \"role\": \"assistant\",\n \"content\": \"can i help you ?\"\n },\n {\n \"role\": \"user\",\n \"content\": \"Hello!\"\n }\n ],\n \"model\": \"gpt-3.5-turbo\",\n \"max_tokens\": 1000,\n \"stream\": true,\n \"temperature\": 0.2\n}")
  .execute()
  .toCompletableFuture()
  .thenAccept(System.out::println)
  .join();

client.close();


### PHP

php
<?php
$client = new \GuzzleHttp\Client();

$response = $client->request('POST', 'https://api.atalk-ai.com/gpt/completions', [
  'body' => '{
    "messages": [
      {
        "role": "system",
        "content": "You are a helpful assistant."
      },
      {
        "role": "assistant",
        "content": "can i help you ?"
      },
      {
        "role": "user",
        "content": "Hello!"
      }
    ],
    "model": "gpt-3.5-turbo",
    "max_tokens": 1000,
    "stream": true,
    "temperature": 0.2
  }',
  'headers' => [
    'Authorization' => '',
    'Content-Type' => 'application/json',
  ],
]);

echo $response->getBody();


海鲸 AI-API 聚合平台是我们对 AI 技术无限探索的一次尝试。它不仅简化了与多个 AI 模型的交互过程，也为用户提供了一个高效、便捷的解决方案。随着 AI 技术的不断进步，海鲸 AI 将成为您实现创意和解决问题的得力助手。