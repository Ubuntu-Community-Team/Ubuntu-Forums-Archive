---
title: "DynDNS set up questions"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2011-01-27
Hi there
I want one host on my network to be a web server and one to be a mail serverbtw. I did ask this question at dynDNS. In the answer i got it told me that i only needed a single hostname since both computers are using the same Internet link. All i need to know is how to set up DNS(using DynDNS free) for a separate mail server and web server that share the same external I.P but have different hostnames(because without different hostnames the border router wouldn't know where to route to right?). If i added MX hostname as: "mymailserver" then, if my web server is called mywebserver.dyndns.org  my MX record would look like this?:
mywebserver.dyndns.org        60        10  mymailserver.dyndns.org
?
Thank you very much for any replies.

---

### Post by methodtwo on 2011-01-28
god that was a daft question. Of course you don't need an MX record if you want the mail addresses to end with your dyndns web server hostname. That just leaves the question of how does a router discover which machines have which ports open?.
I've also heard that most SMTP servers refuse to replay mail if the server it's from has a dynamic I.P. Is this so?. How do you get round this?.

---

