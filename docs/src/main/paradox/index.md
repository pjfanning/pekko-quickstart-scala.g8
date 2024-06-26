# Apache Pekko Actors Quickstart with Scala
 
Pekko is a toolkit and runtime for building highly concurrent, distributed, and fault-tolerant event-driven applications on the JVM. Pekko can be used with both Java and Scala.
This guide introduces Pekko Actors by describing the Scala version of the Hello World example. If you prefer to use Pekko with Java, switch to the [Pekko Quickstart with Java guide](https://github.com/apache/incubator-pekko-quickstart-java.g8).

Actors are the unit of execution in Pekko. The Actor model is an abstraction that makes it easier to write correct concurrent, parallel and distributed systems. 
The Hello World example illustrates Pekko basics. Within 30 minutes, you should be able to download and run the example and use this guide to understand how the example is constructed. 
This will get your feet wet, and hopefully inspire you to dive deeper into the wonderful sea of Pekko!

After trying this example the comprehensive [Getting Started Guide](https://pekko.apache.org/docs/pekko/current/scala/guide/introduction.html) is a good next step to continue learning more about Pekko.

## Running the example

To run Hello World:

1. In a console, change directories to the top level of the unzipped project.
 
    For example, if you used the default project name, akka-quickstart-scala, and extracted the project to your root directory,
    from the root directory, enter: `cd pekko-quickstart-scala`

1. Enter `./sbt` on OSX/Linux or `sbt.bat` on Windows to start sbt.
 
    sbt downloads project dependencies. The `>` prompt indicates sbt has started in interactive mode.

1. At the sbt prompt, enter `reStart`.
 
    sbt builds the project and runs Hello World

The output should look _something_ like this (scroll all the way to the right to see the Actor output):

```
[2019-10-09 09:55:23,390] [INFO ] [com.example.Greeter$] [PekkoQuickstart-pekko.actor.default-dispatcher-5]
[pekko://PekkoQuickstart/user/greeter] - Hello Charles!
[2019-10-09 09:55:23,392] [INFO ] [com.example.GreeterBot$] [PekkoQuickstart-pekko.actor.default-dispatcher-3]
[pekko://PekkoQuickstart/user/Charles] - Greeting 1 for Charles
[2019-10-09 09:55:23,392] [INFO ] [com.example.Greeter$] [PekkoQuickstart-pekko.actor.default-dispatcher-5]
[pekko://PekkoQuickstart/user/greeter] - Hello Charles!
[2019-10-09 09:55:23,392] [INFO ] [com.example.GreeterBot$] [PekkoQuickstart-pekko.actor.default-dispatcher-3]
[pekko://PekkoQuickstart/user/Charles] - Greeting 2 for Charles
[2019-10-09 09:55:23,392] [INFO ] [com.example.Greeter$] [PekkoQuickstart-pekko.actor.default-dispatcher-5]
[pekko://PekkoQuickstart/user/greeter] - Hello Charles!
[2019-10-09 09:55:23,392] [INFO ] [com.example.GreeterBot$] [PekkoQuickstart-pekko.actor.default-dispatcher-3]
[pekko://PekkoQuickstart/user/Charles] - Greeting 3 for Charles
```
   
Congratulations, you just ran your first Pekko app. Now take a look at what happened under the covers. 

## What Hello World does

The example consists of three actors:

* Greeter: Receives commands to `Greet` someone and responds with a `Greeted` reply to confirm the greeting has taken place.
* GreeterBot: Receives the reply from the Greeter and sends a number of additional greeting messages and collects the replies until a given max number of messages has been reached.
* GreeterMain: The guardian actor that bootstraps everything.

## Benefits of using the Actor Model

The following characteristics of Pekko allow you to solve difficult concurrency and scalability challenges in an intuitive way: 

* Event-driven model &#8212; Actors perform work in response to messages. Communication between Actors is asynchronous, allowing Actors to send messages and continue their own work without blocking to wait for a reply.
* Strong isolation principles &#8212; Unlike regular objects in Scala, an Actor does not have a public API in terms of methods that you can invoke. Instead, its public API is defined through messages that the actor handles. This prevents any sharing of state between Actors; the only way to observe another actor's state is by sending it a message asking for it.
* Location transparency &#8212; The system constructs Actors from a factory and returns references to the instances. Because location doesn't matter, Actor instances can start, stop, move, and restart to scale up and down as well as recover from unexpected failures. 
* Lightweight &#8212; Each instance consumes only a few hundred bytes, which realistically allows millions of concurrent Actors to exist in a single application.
 
Let's look at some best practices for working with Actors and messages in the context of the Hello World example.

@@@index

* [Define the Actors and messages](define-actors.md)
* [Create the Actors](create-actors.md)
* [Communicate with Actors](communicate-with-actors.md)
* [The Main Class](main-class.md)
* [Full Example](full-example.md)
* [Testing Actors](testing-actors.md)
* [Running the Application](running-the-application.md)
* [IntelliJ](intellij-idea.md)

@@@
