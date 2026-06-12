---
title: "Problem in changing my ip address"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by bulls_eye on 2009-08-09
HI,
I have installed Ubuntu inside windows.
I wish to change the ip address for my network but can't figure out how to do it.
I have tried editing /etc/network/interfaces
but it gives some sort of error and i am unable to save the changes that I make...
Please help me through this one...

---

### Post by Revolutionary101 on 2009-08-09
To change the ip address for your network you have to change it on your router. Your computer is not able to change it.

---

### Post by bulls_eye on 2009-08-09
so what should i do??

---

### Post by Revolutionary101 on 2009-08-09
What is the brand of router that you are using?

---

### Post by bulls_eye on 2009-08-09
netgear

---

### Post by Revolutionary101 on 2009-08-09
Access your router by typing this into your browser url 192.168.0.1 Then look for LAN settings. Click on it then it should give you an option of changing your IP and enter in the new IP you want.

---

### Post by Iowan on 2009-08-10
I presume you're using DHCP addresses - as opposed to static... but it's worth asking. Were you using **sudo** or **gksudo** (for graphical editor) to edit */etc/network/interfaces*
 (i.e. **sudo nano /etc/network/interfaces**
 or **gksudo gedit /etc/network/interfaces**)?

---

### Post by bulls_eye on 2009-08-11
The problem is solved...
Actually I just went to the file location and made the changes directly without using the authority of the root user...
But then I remembered how I did it to my sources list and then applied it and it worked...
Thanks a lot...

---

### Post by bulls_eye on 2009-08-11
I used sudo gedit /etc/network/interfaces

---

### Post by Iowan on 2009-08-11
[gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") is preferred with **gedit**... but whatever works!!!

---

### Post by bulls_eye on 2009-08-12
ok 
thanks...

---

