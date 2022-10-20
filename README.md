# UI Basics

## General

The purpose of this repository is to provide and describe some basic UI elements/concepts. These elements concepts are intended to be used in build Web GUIs for other projects.

## Framework

The framework to be used is [Bootstrap](https://getbootstrap.com).

## Object types

UI elements seem to be directly related to the objects that the GUI will be working with. In this context, it is important to first define the object types. Once the object types are defined, then respective UI elements could be easier defined and described.

- basic

This type of objects represent the main objects in the system. Example: in an ERP system such objects are Items, Customers, Vendors, Bank Accounts, Payment Methods, etc. Another example: in an Serverless system such an object is a Function object.

- secondary

This type of objects represent various aspects of the basic objects. Example: in an ERP system such objects could be Sales Prices, Purchase Prices. This objects are related to a basic object and cannot exist outside the context of a particular basic object.

- operational

This type of objects represent various activities that have taken place in the system. Example: in an ERP system such objects are Sales Order, Posted Sales Order, Purchase Order, Posted Purchase Order, etc.

## Elements

### Home Page

This is the entry point of the application. One thing that it definetely should contain is a navigation to different areas of the application.

Getting started. Create a file called index.html. Put the following initial code in it:

```
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>UI Basics</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-Zenh87qX5JnK2Jl0vWa8Ck2rdkQ2Bzep5IDxbcnCeuOxjzrPF/et3URy9Bv1WTRi" crossorigin="anonymous">
  </head>
  <body>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-OERcA2EqjJCMA+/3y+gxIOqMEjwtxJY7qPCqsdltbNJuaOe923+mo//f6V8Qbsw3" crossorigin="anonymous"></script>
  </body>
</html>
```

Important parts of this code:

```
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-Zenh87qX5JnK2Jl0vWa8Ck2rdkQ2Bzep5IDxbcnCeuOxjzrPF/et3URy9Bv1WTRi" crossorigin="anonymous">
```

This references the bootstrap CSS. It downloads it from bootstrap CDN. Think about downloading it and accessing it locally in order to eliminate CDN dependency.

```
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-OERcA2EqjJCMA+/3y+gxIOqMEjwtxJY7qPCqsdltbNJuaOe923+mo//f6V8Qbsw3" crossorigin="anonymous"></script>
```

This is put at the end of the body section. It references the bootstrap JavaScript via CDN. It could be donwloaded locally to eliminate CDN dependency. It is used to make some bootstrap elements work.

### Navigation

First element in the Web GUI of any application is a navigation. Here is a sample navigation tag and its explanation following:

```
    <nav class="navbar navbar-expand-lg bg-light">
        <div class="container-fluid">
          <div class="collapse navbar-collapse" id="navbarNavDropdown">
            <ul class="navbar-nav dropdown">
              <li class="nav-item">
                <a class="nav-link active" aria-current="page" href="#">Home</a>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                  General Ledger
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="#">Bank Accounts</a></li>
                  <li><a class="dropdown-item" href="#">Payment Methods</a></li>
                  <li><a class="dropdown-item" href="#">General Ledger</a></li>
                </ul>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                  Inventory
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="itemList.html">Items</a></li>
                </ul>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                  Sales
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="#">Customers</a></li>
                  <li><a class="dropdown-item" href="#">Sales Order</a></li>
                  <li><a class="dropdown-item" href="#">Sales Credit Memo</a></li>
                  <li><a class="dropdown-item" href="#">Posted Sales Order</a></li>
                  <li><a class="dropdown-item" href="#">Posted Sales Credit Memo</a></li>
                </ul>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                  Purchases
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="#">Vendors</a></li>
                  <li><a class="dropdown-item" href="#">Purchase Order</a></li>
                  <li><a class="dropdown-item" href="#">Purchase Credit Memo</a></li>
                  <li><a class="dropdown-item" href="#">Posted Purchase Order</a></li>
                  <li><a class="dropdown-item" href="#">Posted Purchase Credit Memo</a></li>
                </ul>
              </li>
            </ul>
          </div>
        </div>
      </nav>
```

First, we need an enclosing _nav_ tag. My guess is that it is used by the boogstrap JavaScript:

```
<nav class="navbar navbar-expand-lg bg-light">
</nav>
```

Next, nested a _div_ element. This makes sure that the content has some margins between itself and the edges of the browsing area:

```
        <div class="container-fluid">
        </div>
```

Next, a _div_ element which contains the navigation entries:

```
          <div class="collapse navbar-collapse" id="navbarNavDropdown">
          </div>
```

Next, we have a _ul_ element. It holds all the navigation elements directly:

```
            <ul class="navbar-nav dropdown">
            </ul>
```

Next, we have a _li_ item. This represents a top level entry in the navigation. The _active_ class of the _a_ element represents that the navigation entry is the one currently selected:

```
              <li class="nav-item">
                <a class="nav-link active" aria-current="page" href="#">Home</a>
              </li>
```

Another example for navigation elements is a top-level one with its sub elements. This is achieved by adding yet another _ul_ element inside the top-level _li_ element. _li_ elements inside this _ul_ element represent the second-level navigation elements.

```
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                  Sales
                </a>
                <ul class="dropdown-menu">
                  <li><a class="dropdown-item" href="#">Customers</a></li>
                  <li><a class="dropdown-item" href="#">Sales Order</a></li>
                  <li><a class="dropdown-item" href="#">Sales Credit Memo</a></li>
                  <li><a class="dropdown-item" href="#">Posted Sales Order</a></li>
                  <li><a class="dropdown-item" href="#">Posted Sales Credit Memo</a></li>
                </ul>
```

### List

This element will represent a list of a particular object type. It will be a table with its rows representing a since object and columns showing different field of the object. Last column of the table should contain links to different actions over a particular object.

One more thing: the list should contain a link which can be used to create a new instance of the particular object type. To be further described later.

Example _itemList.html_:

- breadcrubm

First, the list element should contain a breadcrub showing what navigation path the user took in order to end up at the current list page:

```
      <nav style="--bs-breadcrumb-divider: '>';" aria-label="breadcrumb">
        <div class="container-fluid">
            <ol class="breadcrumb">
                <li class="breadcrumb-item"><a href="#">Inventory</a></li>
                <li class="breadcrumb-item active" aria-current="page">Items</li>
            </ol>
        </div>
      </nav>
```

First, it contains a _nav_ element:

```
      <nav style="--bs-breadcrumb-divider: '>';" aria-label="breadcrumb">
      </nav>
```

Next, it contains a wrapper _div_ element which makes sure there are margins between the content and the edge of the browing area:

```
        <div class="container-fluid">
        </div>
```

Next, there is an _ol_ element:

```
            <ol class="breadcrumb">
            </ol>
```

Next, multiple _li_ elements represent the entries in the breadcrumb. The active element, which in most cases is the last one, has a _active_ class:

```
                <li class="breadcrumb-item"><a href="#">Inventory</a></li>

                <li class="breadcrumb-item active" aria-current="page">Items</li>
```

- header

After the breadcrumb, the next element in the list UI is a header element:

```
    <div class="container-fluid">
        <h2>Item List <a class="btn btn-primary" href="itemCard.html" role="button">New</a></h2>
    </div>
```

It contains a wrapper _div_ element which provides margins.

```
    <div class="container-fluid">
    </div>
```

Next, inside the wrapper _div_ element there is a _h2_ element which represents the header:

```
<h2>Item List <a class="btn btn-primary" href="itemCard.html" role="button">New</a></h2>
```

Inside there _h2_ element there are two components. One is the text of the header. The other one is a link, which could be used to trigger creating of a new object of the respective type:

```
<a class="btn btn-primary" href="itemCard.html" role="button">New</a>
```

- table

After the breadcrumb, the next element in the list UI element is the table containing the data:

```
        <div class="table-responsive">
          <table class="table table-striped table-sm">
            <thead>
              <tr>
                <th scope="col">Code</th>
                <th scope="col">Name</th>
                <th scope="col">Sales Price</th>
                <th scope="col">Purchase Price</th>
                <th scope="col">Inventory</th>
                <th scope="col">Actions</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>1,001</td>
                <td>random</td>
                <td>data</td>
                <td>placeholder</td>
                <td>text</td>
                <td>edit delete</td>
              </tr>
              <tr>
                <td>1,014</td>
                <td>dashboard</td>
                <td>illustrative</td>
                <td>rich</td>
                <td>data</td>
                <td>edit delete</td>
              </tr>
              <tr>
                <td>1,015</td>
                <td>random</td>
                <td>tabular</td>
                <td>information</td>
                <td>text</td>
                <td>edit delete</td>
              </tr>
            </tbody>
          </table>
        </div>
```

The anatomy of the list is as follows:

First we have a wrapper _div_:

```
        <div class="table-responsive">
        </div>
```

Next, we have a _table_ element:

```
          <table class="table table-striped table-sm">
          </table>
```

In the table first we have a table header:

```
            <thead>
              <tr>
                <th scope="col">Code</th>
                <th scope="col">Name</th>
                <th scope="col">Sales Price</th>
                <th scope="col">Purchase Price</th>
                <th scope="col">Inventory</th>
                <th scope="col">Actions</th>
              </tr>
            </thread>
```

Next in the table we have multiple rows representing the instances of the respective object type:

```
              <tr>
                <td>1,015</td>
                <td>random</td>
                <td>tabular</td>
                <td>information</td>
                <td>text</td>
                <td>edit delete</td>
              </tr>
```

- paging

Last element in the list UI element is a paging component.

```
        <nav aria-label="...">
            <ul class="pagination justify-content-center">

              <li class="page-item disabled">
                <a class="page-link">First</a>
              </li>

              <li class="page-item">
                <a class="page-link" href="#">1</a>
              </li>

              <li class="page-item active" aria-current="page">
                <a class="page-link" href="#">2</a>
              </li>

              <li class="page-item">
                <a class="page-link" href="#">3</a>
              </li>

              <li class="page-item">
                <a class="page-link" href="#">Last</a>
              </li>

            </ul>
          </nav>
```

The anatomy of the paging component is as follows:

First, we have a wrapping _nav_ element:

```
        <nav aria-label="...">
        </nav>
```

Next, we have a _ul_ element:

```
            <ul class="pagination justify-content-center">
            </ul>
```

Next, we have the elements in the paging component represented by different _li_ elements. Additional classes like _disabled_ and _active_ could be used to disable a link and to state the page which is currently active, a.k.a. being displayed:

```
              <li class="page-item disabled">
                <a class="page-link">First</a>
              </li>

              <li class="page-item">
                <a class="page-link" href="#">1</a>
              </li>

              <li class="page-item active" aria-current="page">
                <a class="page-link" href="#">2</a>
              </li>

              <li class="page-item">
                <a class="page-link" href="#">3</a>
              </li>

              <li class="page-item">
                <a class="page-link" href="#">Last</a>
              </li>

```

### Card

This UI element will be used to display the details of a single instance of a particular object. 

It will have 2 main usescases:

- view/edit/update an existing object;
- create a new object;

Example: itemCard.html

Anatomy of the UI element contains the following components:

- navigation

As with the other UI elements, on the top of a card page we will have the standard navigation;

- breadcrumb

The breadcrumb should contain information regarding how and what path the user took in order to land in the current page.

- form

Here is a sample code and then its elements explained one by one:

```
      <div class="container-fluid">
        <h2>Item Card</h2>

        <div class="col-md-12 col-lg-12">
            <form class="needs-validation" novalidate>
              <div class="row g-3">
                <div class="col-sm-6">
                  <label for="firstName" class="form-label">Code</label>
                  <input type="text" class="form-control" id="code" placeholder="" value="" required>
                </div>
    
                <div class="col-sm-6">
                  <label for="lastName" class="form-label">Description</label>
                  <input type="text" class="form-control" id="lastName" placeholder="" value="" required>
                </div>

                <div class="col-sm-6">
                    <label for="firstName" class="form-label">Sales Price</label>
                    <input type="text" class="form-control" id="code" placeholder="" value="" required>
                  </div>
      
                <div class="col-sm-6">
                   <label for="lastName" class="form-label">Purchase Price</label>
                   <input type="text" class="form-control" id="lastName" placeholder="" value="" required>
                </div>

                <div class="col-sm-6">
                    <button type="submit" class="btn btn-primary">Save</button>
                </div>

                <ul class="nav nav-tabs">
                    <li class="nav-item">
                      <a class="nav-link active" aria-current="page" href="#">Item Ledger Entries</a>
                    </li>
                    <li class="nav-item">
                      <a class="nav-link" href="#">Sales Prices</a>
                    </li>
                    <li class="nav-item">
                      <a class="nav-link" href="#">Purchase Prices</a>
                    </li>
                </ul>                

                <div class="table-responsive">
                    <table class="table table-striped table-sm">
                      <thead>
                        <tr>
                          <th scope="col">No</th>
                          <th scope="col">Date</th>
                          <th scope="col">Qty</th>
                          <th scope="col">Price</th>
                          <th scope="col">Amount</th>
                        </tr>
                      </thead>
                      <tbody>
                        <tr>
                          <td>1,001</td>
                          <td>random</td>
                          <td>data</td>
                          <td>placeholder</td>
                          <td>text</td>
                        </tr>
                        <tr>
                          <td>1,002</td>
                          <td>placeholder</td>
                          <td>irrelevant</td>
                          <td>visual</td>
                          <td>layout</td>
                        </tr>
                        <tr>
                          <td>1,003</td>
                          <td>data</td>
                          <td>rich</td>
                          <td>dashboard</td>
                          <td>tabular</td>
                        </tr>
                        <tr>
                          <td>1,003</td>
                          <td>information</td>
                          <td>placeholder</td>
                          <td>illustrative</td>
                          <td>data</td>
                        </tr>
                        <tr>
                          <td>1,004</td>
                          <td>text</td>
                          <td>random</td>
                          <td>layout</td>
                          <td>dashboard</td>
                        </tr>
                        <tr>
                          <td>1,005</td>
                          <td>dashboard</td>
                          <td>irrelevant</td>
                          <td>text</td>
                          <td>placeholder</td>
                        </tr>
                        <tr>
                          <td>1,006</td>
                          <td>dashboard</td>
                          <td>illustrative</td>
                          <td>rich</td>
                          <td>data</td>
                        </tr>
                        <tr>
                          <td>1,007</td>
                          <td>placeholder</td>
                          <td>tabular</td>
                          <td>information</td>
                          <td>irrelevant</td>
                        </tr>
                        <tr>
                          <td>1,008</td>
                          <td>random</td>
                          <td>data</td>
                          <td>placeholder</td>
                          <td>text</td>
                        </tr>
                        <tr>
                          <td>1,009</td>
                          <td>placeholder</td>
                          <td>irrelevant</td>
                          <td>visual</td>
                          <td>layout</td>
                        </tr>
                        <tr>
                          <td>1,010</td>
                          <td>data</td>
                          <td>rich</td>
                          <td>dashboard</td>
                          <td>tabular</td>
                        </tr>
                        <tr>
                          <td>1,011</td>
                          <td>information</td>
                          <td>placeholder</td>
                          <td>illustrative</td>
                          <td>data</td>
                        </tr>
                        <tr>
                          <td>1,012</td>
                          <td>text</td>
                          <td>placeholder</td>
                          <td>layout</td>
                          <td>dashboard</td>
                        </tr>
                        <tr>
                          <td>1,013</td>
                          <td>dashboard</td>
                          <td>irrelevant</td>
                          <td>text</td>
                          <td>visual</td>
                        </tr>
                        <tr>
                          <td>1,014</td>
                          <td>dashboard</td>
                          <td>illustrative</td>
                          <td>rich</td>
                          <td>data</td>
                        </tr>
                        <tr>
                          <td>1,015</td>
                          <td>random</td>
                          <td>tabular</td>
                          <td>information</td>
                          <td>text</td>
                        </tr>
                      </tbody>
                    </table>
                  </div>
          
              </div>
            </form>
          </div>
```

First, we have a wrapper _div_ element:

```
      <div class="container-fluid">
      </div>
```

Next we have a _h2_ element static what this card is for:

```
        <h2>Item Card</h2>
```

Next, we have a _div_ element which acts as a wrapper:

```
        <div class="col-md-12 col-lg-12">
        </div>
```

Next, we have a _form_ element:

```
            <form class="needs-validation" novalidate>
            </form>
```

Next, we have yet another wrapper _div_ element:

```
              <div class="row g-3">
              </div>
```

Next, we have yet another wrapper _div_ element. Now, this div element will contain the actual elements of the wrapping _form_ element:

```
                <div class="col-sm-6">
                </div>
```

Next, the actual we have the actual form element with a respective label. Now, due the class of the wrapping _div_ element, this element practically takes half of the screen. The next element takes the other half and so on they go on the next line:

```
                  <label for="firstName" class="form-label">Code</label>
                  <input type="text" class="form-control" id="code" placeholder="" value="" required>
```

After the form elements are listed in their wrapping _div_ elements, we have a button to submit the form:

```
                <div class="col-sm-6">
                    <button type="submit" class="btn btn-primary">Save</button>
                </div>
```

Now, this completes the basic components of the card. Almost all basic objects have some supplementary objects related to them. In the object types section they are refered to as _secondary_ objects. Now, these type of objects could be displayed here in the card of the main object. The idea is that this is done via a tabbed navigation. Here are more details:

First, we define a _ul_ element which will hold the different tables which will show the different types of secondary objects:

```
                <ul class="nav nav-tabs">
                </ul>
```

Next, the different elements of the navigation are listed as different _li_ elements:

```
                    <li class="nav-item">
                      <a class="nav-link active" aria-current="page" href="#">Item Ledger Entries</a>
                    </li>
                    <li class="nav-item">
                      <a class="nav-link" href="#">Sales Prices</a>
                    </li>
                    <li class="nav-item">
                      <a class="nav-link" href="#">Purchase Prices</a>
                    </li>
```

Next, we have a table, which shows the list of secondary objects:

```
                    <table class="table table-striped table-sm">
                      <thead>
                        <tr>
                          <th scope="col">No</th>
                          <th scope="col">Date</th>
                          <th scope="col">Qty</th>
                          <th scope="col">Price</th>
                          <th scope="col">Amount</th>
                        </tr>
                      </thead>
                      <tbody>
                        <tr>
                          <td>1,001</td>
                          <td>random</td>
                          <td>data</td>
                          <td>placeholder</td>
                          <td>text</td>
                        </tr>
                        <tr>
                          <td>1,002</td>
                          <td>placeholder</td>
                          <td>irrelevant</td>
                          <td>visual</td>
                          <td>layout</td>
                        </tr>
                        <tr>
                          <td>1,003</td>
                          <td>data</td>
                          <td>rich</td>
                          <td>dashboard</td>
                          <td>tabular</td>
                        </tr>
                        <tr>
                          <td>1,003</td>
                          <td>information</td>
                          <td>placeholder</td>
                          <td>illustrative</td>
                          <td>data</td>
                        </tr>
                        <tr>
                          <td>1,004</td>
                          <td>text</td>
                          <td>random</td>
                          <td>layout</td>
                          <td>dashboard</td>
                        </tr>
                        <tr>
                          <td>1,005</td>
                          <td>dashboard</td>
                          <td>irrelevant</td>
                          <td>text</td>
                          <td>placeholder</td>
                        </tr>
                        <tr>
                          <td>1,006</td>
                          <td>dashboard</td>
                          <td>illustrative</td>
                          <td>rich</td>
                          <td>data</td>
                        </tr>
                        <tr>
                          <td>1,007</td>
                          <td>placeholder</td>
                          <td>tabular</td>
                          <td>information</td>
                          <td>irrelevant</td>
                        </tr>
                        <tr>
                          <td>1,008</td>
                          <td>random</td>
                          <td>data</td>
                          <td>placeholder</td>
                          <td>text</td>
                        </tr>
                        <tr>
                          <td>1,009</td>
                          <td>placeholder</td>
                          <td>irrelevant</td>
                          <td>visual</td>
                          <td>layout</td>
                        </tr>
                        <tr>
                          <td>1,010</td>
                          <td>data</td>
                          <td>rich</td>
                          <td>dashboard</td>
                          <td>tabular</td>
                        </tr>
                        <tr>
                          <td>1,011</td>
                          <td>information</td>
                          <td>placeholder</td>
                          <td>illustrative</td>
                          <td>data</td>
                        </tr>
                        <tr>
                          <td>1,012</td>
                          <td>text</td>
                          <td>placeholder</td>
                          <td>layout</td>
                          <td>dashboard</td>
                        </tr>
                        <tr>
                          <td>1,013</td>
                          <td>dashboard</td>
                          <td>irrelevant</td>
                          <td>text</td>
                          <td>visual</td>
                        </tr>
                        <tr>
                          <td>1,014</td>
                          <td>dashboard</td>
                          <td>illustrative</td>
                          <td>rich</td>
                          <td>data</td>
                        </tr>
                        <tr>
                          <td>1,015</td>
                          <td>random</td>
                          <td>tabular</td>
                          <td>information</td>
                          <td>text</td>
                        </tr>
                      </tbody>
                    </table>
```

Next, we have a navigation component to navigate over the secondary objects related to the main object:

```
      <nav aria-label="...">
        <ul class="pagination justify-content-center">

          <li class="page-item disabled">
            <a class="page-link">First</a>
          </li>

          <li class="page-item">
            <a class="page-link">Prev</a>
          </li>

          <li class="page-item">
            <a class="page-link" href="#">1</a>
          </li>

          <li class="page-item active" aria-current="page">
            <a class="page-link" href="#">2</a>
          </li>

          <li class="page-item">
            <a class="page-link" href="#">3</a>
          </li>

          <li class="page-item">
            <a class="page-link">Next</a>
          </li>

          <li class="page-item">
            <a class="page-link" href="#">Last</a>
          </li>

        </ul>
      </nav>
```
