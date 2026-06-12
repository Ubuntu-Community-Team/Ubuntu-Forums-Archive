---
title: "I think I need port forwarding?"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by nbo10 on 2009-12-18
Hi all,
I don't think this is really a ubuntu specific question, but this place is the best for getting answers.

I have a router connecting my dsl line to my home network. My network has 2-3 computers with wireless connections. I want to connect to my laptop, ssh, from the outside world. If I know my modems IP address, how do I get the ssh command to get forwarded to my laptop and not my wife's or my other desktop?

---

### Post by ApEkV2 on 2009-12-18
1. assign the computer with ssh to have a static ip, 
2. enter your router from a web browser (must have a router, most modems don't do forwarding) and find the port forwarding section,
3. enter the ip and port number you want to forward (ip of the ssh comp)

---

### Post by sanderj on 2009-12-18
... or use IPv6 by typing "sudo apt-get install miredo"...

---

### Post by synapsys on 2009-12-18
[http://portforward.com/](http://portforward.com/)

---

