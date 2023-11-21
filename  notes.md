HTTP examples
This reading explores the contents of HTTP requests and responses in more depth.

Request Line

Every HTTP request begins with the request line.

This consists of the HTTP method, the requested resource and the HTTP protocol version.

GET /home.html HTTP/1.1

In this example, GET is the HTTP method, /home.html is the resource requested and HTTP 1.1 is the protocol used.

HTTP Methods

HTTP methods indicate the action that the client wishes to perform on the web server resource.

Common HTTP methods are:
HTTP Method
Description
GET
The client requests a resource on the web server.
POST
The client submits data to a resource on the web server.
PUT
The client replaces a resource on the web server.
DELETE
The client deletes a resource on the web server.
PATCH
The client partially updates a resource on the web server.


HTTP Request Headers

After the request line, the HTTP headers are followed by a line break.

There are various possibilities when including an HTTP header in the HTTP request. A header is a case-insensitive name followed by a: and then followed by a value.

Common headers are:

Host: example.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: */*
Accept-Language: en
Content-type: text/json

The Host header specifies the host of the server and indicates where the resource is requested from.
The User-Agent header informs the web server of the application that is making the request. It often includes the operating system (Windows, Mac, Linux), version and application vendor.
The Accept header informs the web server what type of content the client will accept as the response.
The Accept-Language header indicates the language and optionally the locale that the client prefers.
The Content-type header indicates the type of content being transmitted in the request body.


HTTP Request Body

HTTP requests can optionally include a request body. A request body is often included when using the HTTP POST and PUT methods to transmit data.

```
    POST /users HTTP/1.1
    Host: example.com
    
    {
     "key1":"value1",
     "key2":"value2",
     "array1":["value3","value4"]
    }

```

```

    PUT /users/1 HTTP/1.1
    Host: example.com
    Content-type: text/json
    
    {"key1":"value1"}
```


HTTP Responses

When the web server is finished processing the HTTP request, it will send back an HTTP response.

The first line of the response is the status line. This line shows the client if the request was successful or if an error occurred.

HTTP/1.1 200 OK 

The line begins with the HTTP protocol version, followed by the status code and a reason phrase. The reason phrase is a textual representation of the status code.

### HTTP Status Codes

The first digit of an HTTP status code indicates the category of the response: Information, Successful, Redirection, Client Error or Server Error.

The common status codes you'll encounter for each category are:

### 1XX Informational

Status Code
Reason Phrase
Description
100
Continue
The server received the request headers and should continue to send the request body.
101
Switching Protocols
The client has requested the server to switch protocols and the server has agreed to do so.

### 2XX Successful

Status Code
Reason Phrase
Description
200
OK
Standard response returned by the server to indicate it successfully processed the request.
201
Created
The server successfully processed the request and a resource was created.
202
Accepted
The server accepted the request for processing but the processing has not yet been completed.
204
No Content
The server successfully processed the request but is not returning any content.

### 3XX Redirection

Status Code
Reason Phrase
Description
301
Moved Permanently
This request and all future requests should be sent to the returned location.
302
Found
This request should be sent to the returned location.

### 4XX Client Error

Status Code
Reason Phrase
Description
400
Bad Request
The server cannot process the request due to a client error, e.g., invalid request or transmitted data is too large.
401
Unauthorized
The client making the request is unauthorized and should authenticate.
403
Forbidden
The request was valid but the server is refusing to process it. This is usually returned due to the client having insufficient permissions for the website, e.g., requesting an administrator action but the user is not an administrator.
404
Not Found
The server did not find the requested resource.
405
Method Not Allowed
The web server does not support the HTTP method used.

### 5XX Server Error

Status Code
Reason Phrase
Description
500
Internal Server Error
A generic error status code given when an unexpected error or condition occurred while processing the request.
502
Bad Gateway
The web server received an invalid response from the Application Server.
503
Service Unavailable
The web server cannot process the request.
HTTP Response Headers

Following the status line, there are optional HTTP response headers followed by a line break.

Similar to the request headers, there are many possible HTTP headers that can be included in the HTTP response.

Common response headers are:

Date: Fri, 11 Feb 2022 15:00:00 GMT+2
Server: Apache/2.2.14 (Linux)
Content-Length: 84
Content-Type: text/html

The Date header specifies the date and time the HTTP response was generated.
The Server header describes the web server software used to generate the response.
The Content-Length header describes the length of the response.
The Content-Type header describes the media type of the resource returned (e.g. HTML document, image, video).


### HTTP Response Body

Following the HTTP response headers is the HTTP response body. This is the main content of the HTTP response.

This can contain images, video, HTML documents and other media types.

```
    HTTP/1.1 200 OK
    Date: Fri, 11 Feb 2022 15:00:00 GMT+2
    Server: Apache/2.2.14 (Linux)
    Content-Length: 84
    Content-Type: text/html
    
    <html>
      <head><title>Test</title></head>
      <body>Test HTML page.</body>
    </html>

```



# Other Internet Protocols
Hypertext Transfer Protocols (HTTP) are used on top of Transmission Control Protocol (TCP) to transfer webpages and other content from websites.
This reading explores other protocols commonly used on the Internet.

#### Dynamic Host Configuration Protocol (DHCP)

You've learned that computers need IP addresses to communicate with each other. When your computer connects to a network, the Dynamic Host Configuration Protocol or DHCP as it is commonly known, is used to assign your computer an IP address.
Your computer communicates over User Datagram Protocol (UDP) using the protocol with a type of server called a DHCP server. The server keeps track of computers on the network and their IP addresses. It will assign your computer an IP address and respond over the protocol to let it know which IP address to use. Once your computer has an IP address, it can communicate with other computers on the network.

#### Domain Name System Protocol (DNS)

Your computer needs a way to know with which IP address to communicate when you visit a website in your web browser, for example, meta.com. The Domain Name System Protocol, commonly known as DNS, provides this function. Your computer then checks with the DNS server associated with the domain name and then returns the correct IP address.

#### Internet Message Access Protocol (IMAP)

Do you check your emails on your mobile or tablet device? Or maybe you use an email application on your computer?
Your device needs a way to download emails and manage your mailbox on the server storing your emails. This is the purpose of the Internet Message Access Protocol or IMAP.

#### Simple Mail Transfer Protocol (SMTP)

Now that your emails are on your device, you need a way to send emails. The Simple Mail Transfer Protocol, or SMTP, is used. It allows email clients to submit emails for sending via an SMTP server. You can also use it to receive emails from an email client, but IMAP is more commonly used.

#### Post Office Protocol (POP)

The Post Office Protocol (POP) is an older protocol used to download emails to an email client. The main difference in using POP instead of IMAP is that POP will delete the emails on the server once they have been downloaded to your local device. Although it is no longer commonly used in email clients, developers often use it to implement email automation as it is a more straightforward protocol than IMAP.

#### File Transfer Protocol (FTP)

When running your websites and web applications on the Internet, you'll need a way to transfer the files from your local computer to the server they'll run on. The standard protocol used for this is the File Transfer Protocol or FTP. FTP allows you to list, send, receive and delete files on a server. Your server must run an FTP Server and you will need an FTP Client on your local machine. You'll learn more about these in a later course.

#### Secure Shell Protocol (SSH)

When you start working with servers, you'll also need a way to log in and interact with the computer remotely. The most common method of doing this is using the Secure Shell Protocol, commonly referred to as SSH. Using an SSH client allows you to connect to an SSH server running on a server to perform commands on the remote computer.
All data sent over SSH is encrypted. This means that third parties cannot understand the data transmitted. Only the sending and receiving computers can understand the data.

#### SSH File Transfer Protocol (SFTP)

The data is transmitted insecurely when using the File Transfer Protocol. This means that third parties may understand the data that you are sending. This is not right if you transmit company files such as software and databases. To solve this, the SSH File Transfer Protocol, alternatively called the Secure File Transfer Protocol, can be used to transfer files over the SSH protocol. This ensures that the data is transmitted securely. Most FTP clients also support the SFTP protocol.

### CSS
![Screen Shot 2023-11-04 at 4.33.34 PM.png](Image%2FScreen%20Shot%202023-11-04%20at%204.33.34%20PM.png)


### Different types of selectors
When styling a web page, there are many types of selectors available that allow developers to be as broad or as specific as they need to be when selecting HTML elements to apply CSS rules to.

Here you will learn about some of the common CSS selectors that you will use as a developer.

### Element Selectors

The element selector allows developers to select HTML elements based on their element type.

For example, if you use ```p``` as the selector, the rule will apply to all p elements on the webpage.

### HTML

```HTML
    <p class="introduction"></p>
```


CSS
```CSS
p.introduction { 
  margin: 2px;
}
```
### Descendant Selectors

Descendant selectors are useful if you need to select HTML elements that are contained within another selector.

Let's explore an example.

You have the following HTML structure and CSS rule.

```html
<div id="blog">
  <h1>Latest News</h1>
  <div>
    <h1>Today's Weather</h1>
    <p>The weather will be sunny</p>
  </div>
  <p>Subscribe for more news</p>
</div>
<div>
  <h1>Archives</h1>
</div>
```
```CSS
#blog h1 {
  color: blue;
}
```
The CSS rule will select all h1 elements that are contained within the element with the ID blog. The CSS rule will not apply to the h1 element containing the text Archives.

The structure of a descendant selector is a CSS selector, followed by a single space character, followed by another CSS selector.

Multiple descendants can also be selected. For example, to select all h1 elements that are descendants of div elements which are descendants of the blog element, the selector is specified as follows.

```CSS
#blog div h1 {
  color: blue;
}
```


### Child Selectors

Child selectors are more specific than descendant selectors. They only select elements that are immediate descendants (children) of a selector (the parent).

For example, you have the following HTML structure:

HTML
```html
<div id="blog">
  <h1>Latest News</h1>
  <div>
    <h1>Today's Weather</h1>
    <p>The weather will be sunny</p>
  </div>
  <p>Subscribe for more news</p>
</div>
```
If you wanted to style the h1 element containing the text Latest News, you can use the following child selector:

CSS
```CSS
#blog > h1 {
  color: blue;
}
```


This will select the element with the ID ```blog``` (the parent), then it will select all ```h1``` elements that are contained directly in that element _(the children)_. The structure of the child selector is a CSS selector followed by the child combinator symbol > followed by another CSS selector.

Note that this will not go beyond a single depth level. Therefore, the CSS rule will not be applied to the h1 element containing the text Today's Weather.

### :hover Pseudo-Class

A special keyword called a _pseudo-class_ allows developers to select elements based on their state. Don't worry too much about what that means right now. For now, let's look at how the hover pseudo-class allows you to style an element when the mouse cursor hovers over the element.

The simplest example of this is changing the color of a hyperlink when it is hovered over. To do this, you ```add the :hover pseudo-class``` to the end of the selector. In the following example, adding ```:hover```  to the ```a``` element will change the color of the hyperlink to orange when it is hovered over.

CSS
```CSS
a:hover {
  color: orange;
}
```

This pseudo-class is very useful for creating visual effects based on user interaction.

### COLOR

Colors are used in many CSS properties, for example:

```CSS
p { 
  color: blue; 
}

```
From CSS Version 3, there are five main ways to reference a color.

By RGB value,
By RGBA value,
By HSL value,
By hex value and
By predefined color names.

#### RGB Value
RGB is a color model that adds the colors red (R), green (G) and blue (B) together to create colors. This is based on how the human eye sees colors.

Each value is defined as a number between 0 and 255, representing the intensity of that color.

For example, the color red would have the RGB value of 255,0,0 since the intensity of the red color would be 100% while blue and green would be 0%.

The color black then would be 0,0,0 and the color white 255,255,255.

When using RGB values in CSS, they can be defined using the rgb keyword:

```html
p { 
  color: rgb(255, 0, 0); 
}
```
#### RGBA Value

RGBA is an extension of RGB that add an alpha (A) channel. The alpha channel represents the opacity, or transparency, of the color.

Similar to RGB, this is specified in CSS using the rgba keyword:
```css
p { 
  color: rgba(255, 0, 0, 0.8); 
}
```

#### HSL value

HSL is a newer color model defined as Hue (H), Saturation (S) and Lightness (L). The aim of the model is to simplify mental visualization of the color that the value represents.

Think of a rainbow that has been turned into a full circle. This represents the Hue. The Hue value is the degree value on this circle, from 0 degrees to 360 degrees. 0 is red, 120 is green and 240 is blue.
![6W-NFfelTF-vjRX3pXxfHw_71bfe705b84941a1b8f51eea05a848e1_text_color_hue.png](Image%2F6W-NFfelTF-vjRX3pXxfHw_71bfe705b84941a1b8f51eea05a848e1_text_color_hue.png)

Saturation is the distance from the center of the circle to its edge. The saturation value is represented by a percentage from 0% to 100% where 0% is the center of the circle and 100% is its edge. For example, 0% will mean that the color is more grey and 100% represents the full color.

Lightness is the third element of this color model. Think of it as turning the circle into a 3D cylinder where the bottom of the cylinder is more black and toward the top is more white. Therefore, lightness is the distance from the bottom of the cylinder to the top. Again, lightness is represented by a percentage from 0% to 100% where 0% is the bottom of the cylinder and 100% is its top. In other words, 0% will mean that the color is more black and 100% is white.
![EoftTRz8S7uH7U0c_Fu7KQ_ba9919ab0ef54d29bb897ce29dcd03e1_text_color_hue2.png](Image%2FEoftTRz8S7uH7U0c_Fu7KQ_ba9919ab0ef54d29bb897ce29dcd03e1_text_color_hue2.png)

In CSS, you use the hsl keyword to define a color with HSL.
```css
p { 
  color: hsl(0, 100%, 50%);
}
```

**Hex value**

Colors can be specified using a hexadecimal value. If you're unfamiliar with hexadecimal, think of it as a different number set.

Decimal is what you use every day. Digits range from 0 to 9 before tens and hundreds are used.

Hexadecimal is similar, except it has 16 digits. This is counted as ```0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F.```

In fact, you can convert between decimal and hexadecimal. Decimal 10 is equal to hexadecimal A. Hexadecimal F is equal to decimal 15.

Hexadecimal can also go to tens and hundreds. For example, decimal 16 is equal to hexadecimal ```10```, with ```10``` being the next number after ```F```.

It can be a little confusing at first but don't worry, there are plenty of converters available if you get stuck.

Colors specified using hexadecimal are prefixed with a # symbol followed by the RGB value in hexadecimal format.

For example, the color red which is RGB 255,0,0 would be written as hexadecimal #FF0000.

Again don't worry if you get stuck, there are plenty of converters available for this too!

**```Predefined color names```**

Modern web browsers support 140 predefined color names. These color names are for convenience purposes and can be mapped to equivalent hex/RGB/HSL values.

Some common color names available are listed below.


1. black
2. silver
3. gray
4. white
5. maroon
6. red
7. purple
8. fuchsia
9. green
10. lime
11. olive
12. yellow
13. navy
14. blue
15. teal
16. aqua

**Text**

With CSS there are many ways to change how text is displayed. In this section, you'll learn the most common text manipulation CSS properties.

```css
p { 
  color: red;
}

```
**Text Font and Size**
There are many different fonts to display text on your computer. In simple terms, a font is a collection of text characters written in a specific style and size.

If you've used a word processor before, you're probably familiar with the fonts Times New Roman and Calibri.

To set the font used by text in CSS you use the **font-family** property.

```css

p { 
  font-family: "Courier New", monospace;
}

```

Since computers vary in what fonts they have installed, it is recommended to include several fonts when using the `font-family` property. These are specified in a fallback order, meaning that if the first font is not available, it will check for the second font. If the second font is not available, then it will check for the third font and so on. If none of the fonts are available, it will use the browser's default font.

To set the size of the font, the ```font-size``` property is used.
```css
p { 
  font-family: "Courier New", monospace;
  font-size: 12px;
}
```
#### Text Transformation

Text transformation is useful if you want to ensure the correct capitalization of the text content. In the example below, the CSS rule will change all text in paragraph elements to uppercase using the `text-transform `property:
```css
p { 
  text-transform: uppercase;
}
```
The most commonly used values for the text-transform property are:  `uppercase,  lowercase,  capitalize  and none.` The default value used is none, which means the text displays as it was written in the HTML document.

#### Text Decoration

The `text-decoration` property is useful to apply additional decoration to text such as underlining and line-through (strikethrough).
```css
p { 
  text-decoration: underline;
}
```
If this is confusing, don't worry. These properties can be individually set using the ```text-decoration-line```, `text-decoration-color`, `text-decoration-style` and `text-decoration-thickness` properties. Let's use the same example again and define it using the individual properties:

```css
p { 
  text-decoration-line: underline;
  text-decoration-color: red;
  text-decoration-style: solid;
  text-decoration-thickness: 5px;
}
```

The most common text-decoration-line values used are: 
- underline, 
- overline, 
- line-through and 
- none. 

None is the default value to use no text decoration.

There are many styles available for the text-decoration-style  property;  
- solid,  
- double,  
- dotted,  
- dashed  and  
- wavy. 

The text-decoration-style property requires the decoration line to be defined. If the decoration style is not specified, solid will be used.

# Box Model 
### For on appealing layout

# Document Flow

- inline elements
  - Inline elements only occupy the width and height of their content and they don't appear on a new line, hence the name "inline".
- block level elements
  - It's important to remember that block elements begin on a new line and take up the full width of the page
  - 
- 
The web browsers normal way of calculating the position of html elements on the screen is called document flow. By default, nearly all html elements are organized into one of two categories namely in block and in line elements.

A block level element will occupy the full horizontal width of its parent element and the vertical height of its content. Each block level element will have a new line before and after. Therefore, multiple block level elements will stack on top of each other like a stack of boxes.

In line elements only occupy the width and height of their content. They don't appear on a new line, hence the name in line. Therefore, multiple in line elements can form a row of elements. When coding in html, you need to be able to recognize and use block elements. Some examples of block level elements include the tags, div form and heading. You also need to be familiar with common in line elements. These include the tags anchor, image, input label, bold, italics, emphasis and span.


## Alignment

Text alignment can be set to left, right, center and justify
```css
p {
    text-align: center;
}
```

## HTML element alignment
Aligning an HTML element is done by changing the properties of its box model and how it impacts the document flow.
```html
<div class="parent">
  <img src="photo.png" class="child">
</div>
```

```css
.parent {
  border: 4px solid red;
}

.child {
  width: 50%;
  padding: 20px;
  border: 4px solid green;
  margin: auto;
}
```


## HTML Element Left / Right Alignment

The two most common ways to left and right align elements are to use the float property and the position property.

The position property has several value options that impact how the element displays in the document flow. You'll explore how to use the position property later on. For now, let's focus on the float property.

The float property sets an element's position relative to the text content within a parent element. Text will wrap around the element.

In the following example, the image will be aligned to the right of the div element. The text content will wrap around the image:

```html
<div class="parent">
  <img src="photo.png" class="child"> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur eu odio eget leo auctor porta sit amet sit amet justo. Donec fermentum quam in diam volutpat, at lacinia diam placerat. Aenean quis feugiat sem. Suspendisse a dui massa. Phasellus scelerisque, mi vestibulum iaculis tristique, orci tellus gravida nisi, in pellentesque elit massa ut lorem. Sed elementum ornare nunc vel cursus. Duis sed enim in nulla efficitur convallis sed eget dolor. Curabitur scelerisque eros erat, in vulputate dolor consequat vel. Praesent ac sapien condimentum, ultricies libero at, auctor orci. Curabitur ut augue ac massa convallis faucibus sed in magna. Phasellus scelerisque auctor est a auctor. Nam laoreet sem sapien, porta imperdiet urna laoreet eu. Morbi dolor turpis, congue id bibendum eget, viverra et risus. Quisque vitae erat id tortor ullamcorper maximus.
</div>
```
```css
.child {
  float: right;
}
```
