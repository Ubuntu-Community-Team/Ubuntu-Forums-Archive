---
title: "Hosting a website on a different port"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by eyellowbus on 2009-06-03
Hello,

Currently my ISP blocks port 80, so I have to map my domain name  (example.com) to port 8100 of my computer. When the visitor types example.com, the domain register will generate a frame, and the url  of the frame content is: [http://]("http:///")<my home IP>:8100. This is a problem for the visitors  who bookmark my website, because they will book mark my IP address  instead of my domain name.

Is it possible to do the following?
1. When the visitor types example.com[]("http://www.icesquare.com") (without specifying the port number), it will go to my home computer without using a frame. Can I do this by making my home machine as a DNS server?


2. If the visitor types http://<my home IP>:8100/, can Apache automatically convert it to example.com?


FYI, here is my Apache config:

[FONT=Courier New, Courier, monospace]Listen 8100
...

NameVirtualHost *:8100
<VirtualHost *:8100>
   ServerName www.[/FONT]example.com[FONT=Courier New, Courier, monospace]
   ServerAlias [www.example.com](www.example.com)[/FONT][FONT=Courier New, Courier, monospace]
   ....

[/FONT]
Thanks!

---

