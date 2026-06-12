---
title: "http request to my ubuntu machine..."
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by shushu on 2009-06-04
Hi,

I'm running ubuntu and jboss on it, accessing jboss from [http://localhost:8080](http://localhost:8080) works gr8, but from another machine on the same network (i have ping to it) doesn't.

any idea?

shushu

---

### Post by whoop on 2009-06-04
What is the exact url you are typing in on the other machine?

---

### Post by shushu on 2009-06-05
localhost = [my server name/ip address] so it would be: [http://[my](http://[my) server name]:8080

---

### Post by whoop on 2009-06-05
> **shushu said:**
> localhost = [my server name/ip address] so it would be: [http://[my](http://[my) server name]:8080

Try the lan ip address of you server machine -- > [http://ipaddressofserver:8080](http://ipaddressofserver:8080).

example: [http://192.168.0.12:8080](http://192.168.0.12:8080)

---

### Post by shushu on 2009-06-06
did that and no go :(

---

### Post by whoop on 2009-06-06
> **shushu said:**
> did that and no go :(

can you ping the server from the other machine?

---

### Post by jonobr on 2009-06-06
I would also recommend on the webserver machine,
open a terminal,
type 

sudo tcpdump -vvv -i any port 8080

Then try your connection.

If anything pops up, it means the packets are getting there.

If you see nothing going back its a server issue,
if you see nothing reaching the server (or showing an output here)
its a network or problem or the other machine,.

One other possibility is that (given your on the same network) your most likely not having network issues and this could be that your host - trying to get to the web server- could be using that port number already for something else.

The tcpdump might show this

---

### Post by shushu on 2009-06-07
1. i have ping to that machine
2. i entered "sudo tcpdump -vvv -i any port 8080" and i see packets received by the server, what is the meaning of it?
3. the web server is up and running no other application has taken the 8080 port

---

### Post by puppywhacker on 2009-06-07
what you should see on the tcpdump is the following

client > server

> tcp SYN
< tcp SYN ACK
> tcp ACK
> http GET / HTTP/1.0
< HTTP/1.0 200 OK
  the stuff you serve

either you have a firewall filtering out port 8080, which means you should only see the TCP SYN packets and not establishing a connection. if you see the HTTP GET then you JBOSS is not accepting connections properly and you should troubleshoot the log files.

post the tcpdump

---

### Post by jonobr on 2009-06-07
Agree with Pupperwhacker, without the dumps its hard to know whats happening,
it sounds as if your packets are being recieved though whoch points to either application or response problems

---

