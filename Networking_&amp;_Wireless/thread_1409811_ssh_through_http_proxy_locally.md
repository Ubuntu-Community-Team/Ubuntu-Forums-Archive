---
title: "ssh through http proxy locally"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by sduvick on 2010-02-18
i'm behind a very blocked firewall that only allows connections through port 80 and 443. i wish to ssh to my machine at home, but the port is blocked. is there a simple server that i can run to route my ssh connection through http?

---

### Post by Crafty Kisses on 2010-02-18
You might want to look into [**Corkscrew.**]("http://www.agroman.net/corkscrew/") Try and download the tar and compile it from source, make sure you have build-essential installed when your compiling it from source. Once Corkscrew is compiled, you then need to open your SSH configuration file and then you need to add the following lines:
```
Host *
  ProxyCommand corkscrew (HTTP proxy address here) 8080 %h %p
```
Obviously where HTTP address here, you need replace that with the correct information. Then try and SSH into the box and see if it works.

---

### Post by sduvick on 2010-02-21
thanks for the reply, i had looked into corkscrew previously, and it works.
but the problem with that is finding an outside proxy to use. i was wondering if i could use the concept behind corkscrew and instead of sending it outside, if i could host a local proxy and route corkscrew through that? and if so do you have any suggestions?

---

