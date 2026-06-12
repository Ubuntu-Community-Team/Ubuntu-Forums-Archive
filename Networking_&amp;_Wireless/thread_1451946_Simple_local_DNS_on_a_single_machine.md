---
title: "Simple local DNS on a single machine"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by HyperFlexed on 2010-04-11
Hi, I've been looking into how I can use custom URLs to access my LAMP setup, but have found either no working solution, or overkill solutions (i.e. BIND9)

I can edit my /etc/hosts file with the line

```
127.0.1.1	go.myaction	localhost
```

but this will only work when I visit [http://go/myaction](http://go/myaction)

What I want to know is how can I access [http://go](http://go)

I've tried setting the the second parameter to ".go", "go." to no avail, and I'm wondering if there's some kind of syntax I'm missing out on. I want to be able to use [http://go/whatever](http://go/whatever), but I also want to have a hub page that links to all of go's subdomains if I simply visit [http://go](http://go)

I know they used to have this at a place I worked, so I'd be interested in doing it myself if possible through /etc/hosts. If not, I guess I'll have to look into BIND9

---

### Post by colemar on 2010-04-11
I don't really understand your question, but I can say one thing for sure:
if you write [http://a/b/c/](http://a/b/c/)... in the browser address bar, rest assured that domain name resolution is completely unrelated to any URL piece besides **a** (which is the fully qualified domain name, or host).

If you are differentiating web sites based on **b** then you should not worry about dns resolution as long as **a **is mapped to the web server ip address.

Instead, if you are writing about "virtual hosts" then you should understand that they are accessed by different values for **a**, for example:
[http://bob.com/](http://bob.com/)
[http://joe.com/](http://joe.com/)
[http://ted.com/](http://ted.com/)
The "virtual host" concept is that bob.com, joe.com and ted.com are all mapped to the same ip address; it is the HTTP request message sent by the browser to the web server that contains one of the three names and the webserver behaves accordingly.

---

### Post by HyperFlexed on 2010-04-11
I thought I was pretty clear on expressing what I wanted. Either way, I realized my mistake was in mixing up the fields in /etc/hosts

I realized instead of

127.0.1.1 go.whatever localhost
(where localhost would redirect to go.whatever)

I needed

127.0.1.1 localhost go
(where localhost will eventually become the route to my "go" application)

---

### Post by Iowan on 2010-04-11
127.0.0.1 is usually **localhost**
127.0.1.1 is usually where hostnames go.
(Glad you got it to work!)

---

