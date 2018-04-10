# deKlarative
## A Kotlin based declaritive web framework.

I personally like a more decalritive approach when buidling applications. It makes it easier to follow the logic and to reason about what  you are doing. I have haven't seen a lot of declaritive style web frameworks, so I decided to try to build my own. 

This project will use some other great libraries to accomplish the goals that I want. There will be a focus on greating a nice DSL for declaring your app and will include both full pages and APIs. I will try to keep the design out in the open as I work on it and any feedback will be appreciated. I will try to make my overall goals clear.


## Inspirations

Almost all frameworks solve a pain point and create a few themselves. I have always been inspired by the simplicity frameworks like Rails and Django bring to getting a project started. There are a cool features that are just hanging out in those projects that I find really helpful.

Django has this nice helper method callled *get_object_or_404* that takes a model and an id, if it isn't found it returns a 404 view, if it is, returns the details view of the object. This makes it easy to not worry about null checks, etc. This is a nice declaritive approach. I tell it what I want to happen and it does.

Other frameworks, do a really good job of just wiring up the default cases. Spring Boot with the Sprint Data REST does a really ncie job of giving you a default RESTful API with just using an annotation. All you need is define a model. It doesn't make you worry about all the plumbing required if you set the correct annotiations. This is nice, in both of these instances you have the ability to override that default behavior if you want to do more. That is one of the biggest issues with frameworks like Rails, sometimes you don't have the option to not do it the rails way. 

Another goal is to make this library composible. Composition rules and I think to make something decalritive it needs the abilities for users to compose components together to *declare* what they would like to happen. Funny enough, I feel if you are striving to make something declaritive, it has to be composible. Along with that composibility, having an orthogonal architecture is desired. 

If I get composibility correct and base my constructs based on functions rather than objects, I should be able to create a very orthogonal architecture that will allow you to override functionality that you want with your own functions. Since I plan to use Kotlins it maybe as simple as creating your own extension methods.

## Libraries and Frameworks

Currently I plan to use the following projects

* [Kotlinx.HTML](https://github.com/Kotlin/kotlinx.html)
* [Exposed](https://github.com/JetBrains/Exposed)
* [Ktor](https://ktor.io/)
* [Arrow](http://arrow-kt.io/)

## Possible Syntax examples

While I am thinking through this before I start trying to develop some examples, here is what I am thinking.

```
interface ApiEndpoint {
	fun get()
	fun post()
	fun delete()
	fun put()
	// etc.
}

fun main(args: Array<String>) {
    embeddedServer(Netty, 8080) {
        endpoint {
              +"Description of service"
              url("/orders")
              apiData(orders)
            }
        }
    }.start(wait = true)
}
```
