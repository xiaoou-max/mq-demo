# mq-demo

RabbitMQ 的 Spring AMQP 演示工程，包含消息生产者与消费者两个模块，覆盖常用的消息模型。

## 模块

| 模块 | 说明 |
|---|---|
| `publisher` | 消息生产者，演示基础队列、工作队列、发布/订阅、Routing、Topic 等模型 |
| `consumer` | 消息消费者，基于 `@RabbitListener` 接收消息；`FanoutConfig` 负责声明交换机、队列与绑定关系 |

## 技术栈

Spring Boot 2.3.9 · Spring AMQP · RabbitMQ · Lombok

## 目录结构

```
publisher/src/test/java/cn/itcast/mq/
├── helloworld/PublisherTest.java      基础队列与工作队列
└── spring/SpringAmqpTest.java         Spring AMQP 的发送方式

consumer/src/main/java/cn/itcast/mq/
├── config/FanoutConfig.java           交换机、队列与绑定的声明
└── listener/SpringRabbitListener.java 消息监听与消费
```

## 运行

1. 启动 RabbitMQ，默认连接地址 `localhost:5672`，管理台 `localhost:15672`
2. 按实际情况修改两个模块 `src/main/resources/application.yml` 中的连接信息
3. 先启动 `consumer`，再运行 `publisher` 中的测试类发送消息
4. 在 RabbitMQ 管理台的 Queues / Exchanges 页面观察消息流转
