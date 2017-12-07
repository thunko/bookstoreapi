# LAB 03: Programming Cloud Services - REST API

Author:

- Jonathan BERRIOS, [ojaebi-7@student.ltu.se](mailto:ojaebi-7@student.ltu.se)

This document can be viewed in HTML rendered form [here].

[here]: http://htmlpreview.github.com?https://github.com/thunko/bookstoreapi/blob/master/README.html

## Table of contents

- [2 Question](#2-quiestion)
- [3 Exercises](#3-exercises)
  - [Service Description](#service-description)
  - [Create a RESTful API](#create-restful-api)
  	- [API Routes](#api-routes)
  	- [API Tests](#api-tests)
* [References](#references)

## 2 Question

> What are microservices? Describe in detail the pros and cons of microservices architecture by giving examples.

Pros

Technology Heterogeneity

It is possible to build a system with different techonlogies used. In this way, the developer can use the prefered tool, such in the project for this Lab, instead of selecting a standarized approach, one technology for the whole implementation.

Resilience

The services stand for their own. If in the system, one of them fail, the rest can continue working. It is not the case for a monolithic service.
With microservices, the total failure of a system will be handled accordingly with the granular functionalities of it.

Scaling

As per the granular nature of microservices, it allows scaling only to the services needed. This is prefered instead of having the need to scale the whole system when only a small part requires the scaling.

Ease of Deployment

It allows to make changes entailing considerably less risk in terms of issues arising. In the same tame, as it is granular per service, should a problem occur, it can be easier to trace and rollback if needed. Thus, it allows easier deployment in comparison to a monolithic application, in which a whole application release needs to be deployed for a small change.

Composability

It encourages the re-use of functionalities in various ways and purposes.

Optimizing for Replaceability

It is more practical with individual services being small in size, the cost to replace it with a better implementation, or to delete them altogether, it is easier to manage in comparison with a bigger one scale service.

Cons

As it very adaptative to handle many techologies, it also drags the associated complexities of distributed systems. For an actual deployment, it can take longer to be actually familiar with the many technologies handled.

## 3 Exercises

### Service Description

> In this exercise, you will learn how to develop a simple RESTful API for the application of your choice.

> 2. Use microservices as an architectural paradigm to design a simple service (one component only). Describe and document that service. 

In this exercise, a REST APIs is implemented for a Bookstore catalog. The database called Bookstore has 2 collections (or tables), book and genre.
book handles the following data:
	-title
	-genre
	-description
	-author
	-publisher
	-pages
	-image_url
	-buy_url
	-create_date
genre handles the following data:
	-name
	-create_date

The API implemented is RESTful CRUD (Create, Retrieve, Update, Delete) and Node.js, Express and MongoDB were used to deploy. Mongoose was used to interface with the MongoDB database.

As this lab is intended to show the API functionality, a MongoDB instance was created in the localhost an accessed via CMD.

For the web framework, Express for node.js is used as there is many information to use among the community.
Express is built on top of node.js http module, and support functionalities for routing, middleware, view system and so on.

For the DB handling, Mongoose was used based on the same criteria of information available. It is an ODM (Object Document Mapping) tool for Node.js and MongoDB. It translates the objects in the code into documents in the DB and vice-versa.

For ease of use **RESTeasy** app in Google Chrome is used.


### Create a RESTful API

> Your RESTful API should implement atleast two verbs, for example GET and POST. For GET, you should implement atleast one path.

#### API routes

The API routes implemented are the following:

For users:
```console
http://localhost:3000/
```

This will retrieve a welcome message followed by the working routes

**GET:**

```console
/api/genres or /api/books
/api/books/<id>
```

first route Will retrieve an array of JSON objects with the fields determined for the book or a genre object.
secind route Will retrieve an specific JSON object with the ID requested with its according fields.

**POST:**

```console
/api/genres or /api/books
```

Before inserting strucutred data, it is necessary to set *Headers* in **RESTeasy** to *Content Type* and value *application/json*

when inserted the complete route into `URL` section in `RESTeasy` which would be `http://localhost:3000/api/books`, you need to insert the requested structured data into the `Body`.
If one of the fields is not filled, it will be filled with null.
After sending, an **OK** will be returned and the data will be *posted*.

**PUT:**

```console
/api/genres/<id> or /api/books/<id>
```

A returned **OK** will be retrieved when an existing id is given as a parameter and a new data set is inserted to replace for the object with that **ID**.

**DELETE:**

```console
/api/genres/<id> or /api/books/<id>
```

After selecting `DELETE` option in `RESTeasy`, and by giving the **ID**, the desired object will be deleted.
An **OK** is returned after a successfull message.

#### API tests

Screenshots inserted for validation.


**GET:**

<p align="center">
  <img alt="get-books.png" src="https://github.com/thunko/bookstoreapi/blob/master/get-books.PNG?raw=true">
</p>


<p align="center">
  <img alt="get-books-id.png" src="https://github.com/thunko/bookstoreapi/blob/master/get-books-id.PNG?raw=true">
</p>

**POST:**

<p align="center">
  <img alt="post-book-structure.png" src="https://github.com/thunko/bookstoreapi/blob/master/post-book-structure.PNG?raw=true">
</p>

<p align="center">
  <img alt="post-book-ok.png" src="https://github.com/thunko/bookstoreapi/blob/master/post-book-ok.PNG?raw=true">
</p>

**PUT:**

<p align="center">
  <img alt="put-book-structure.png" src="https://github.com/thunko/bookstoreapi/blob/master/put-book-structure.PNG?raw=true">
</p>

<p align="center">
  <img alt="put-book-ok.png" src="https://github.com/thunko/bookstoreapi/blob/master/put-book-ok.PNG?raw=true">
</p>

**DELETE:**

<p align="center">
  <img alt="delete-book" src="https://github.com/thunko/bookstoreapi/blob/master/delete-book.PNG?raw=true">
</p>

<p align="center">
  <img alt="delete-book-ok" src="https://github.com/thunko/bookstoreapi/blob/master/delete-book-ok.PNG?raw=true">
</p>

## References

1. Sam Newman in: Building Microservices: Designing Fine-Grained Systems 1st Edition from
   https://stackoverflow.com/questions/34903605/microservices-what-are-pros-and-cons/34904942

[1]: #references

