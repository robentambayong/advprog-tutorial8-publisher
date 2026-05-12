### Understanding Publisher and Message Broker

**a. How much data will your publisher program send to the message broker in one run?**
In one run, the publisher will send exactly 5 events (messages) sequentially to the message broker, one for each user created (Amir, Budi, Cica, Dira, and Emir).

**b. The URL is the same as the subscriber program, what does it mean?**
It means both the publisher and the subscriber are connecting to the exact same AMQP message broker instance running locally on port 5672 using the same credentials. This shared connection point allows the publisher to push messages to a queue that the subscriber is concurrently listening to.

### RabbitMQ Dashboard
![RabbitMQ Dashboard](rabbitmq.png)

### Running the Publisher and Subscriber

**Terminal Outputs:**
![Subscriber Terminal](subscriber_terminal.png)
![Publisher Terminal](publisher_terminal.png)

**What is happening:**
When the publisher program is executed, it establishes a connection to the RabbitMQ broker and fires off five distinct `UserCreatedEventMessage` events to the `user_created` queue. Because the subscriber program is already running and actively listening to that exact same queue, the message broker instantly routes and pushes those newly arrived events to the subscriber. The subscriber then processes each message and logs the data to the console in real-time, demonstrating a seamless event-driven architecture.