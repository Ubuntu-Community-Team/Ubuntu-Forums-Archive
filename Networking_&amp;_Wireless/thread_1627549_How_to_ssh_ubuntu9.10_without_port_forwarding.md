---
title: "How to ssh ubuntu9.10 without port forwarding"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by vivien_yan on 2010-11-21
Hi, I have a ubuntu 9.10 on my desktop in my office and I have another ubuntu on my home desktop. Both machines are behind a router. I guess many people have already asked the same question: how to remote control the office desktop from my home desktop? 

Many posts discussed about solving this by setting up ssh and port forwarding. But my situation is that I cannot control the router in my office so I cannot set up any port forwarding for my office desktop. So I guess my question becomes how to remote control my office desktop without setting up any port forwarding on the office router. Can anyone give me some help on this? Thank you!

---

### Post by Naitsirhc Hsem on 2010-11-21
I don't believe that is possible, sorry

---

### Post by vivien_yan on 2010-11-21
I used to be using win7+hamachi and I could remote controlled my office desktop. 

Then I switched to ubuntu 9.10 and set up VNCserver as if my desktop has a public IP. Magically, it worked. I can use VNCviewer to remote contol my office desktop. I think I just followed the instructions on installing VNCserver. 

But then one day, VNC stopped working and I don't even know the reason. Since I set up VNCserver as if I have a public IP, I'm thinking whether it will work if I use something like vncserver+hamachi . But I don't know whether it is possible and how to set it up.

> **Naitsirhc Hsem said:**
> I don't believe that is possible, sorry

---

### Post by DanYoSon on 2010-11-21
This should work [http://www.teamviewer.com/]("http://www.teamviewer.com/")

this way both computers connect to the same remote server and then you can get through the firewalls/routers because there is a active  connection to work with, you can do this with ssh and reverse tunneling but this is probaly a lot easyer.

i have not used this myself but i do know people that have. 

hope this helps

Daniel

---

