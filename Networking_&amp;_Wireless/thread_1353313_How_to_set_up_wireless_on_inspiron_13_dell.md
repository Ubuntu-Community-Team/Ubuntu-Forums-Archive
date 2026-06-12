---
title: "How to set up wireless on inspiron 13 dell"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by Giovano on 2009-12-12
Hello everyone, 

I have read a lot of stuff about the installation of wireless, like use intell driver.
but could anyone give me a straight forward method to do it for a newbie like me ?

I alreaday checked in system/administration/hardware drivers and there is nothing...

so I am totally lost, 
I need your help!!!!!

Thank you so much!


an ubuntu newbie....

---

### Post by The Toxic Mite on 2009-12-12
Hey!

Can you go to Applications > Accessories > Terminal, and enter the following commands?

```

sudo lshw -c network
lspci
iwconfig

```

Post the outputs of them when you are done.

:D

---

### Post by Giovano on 2009-12-12
Thank you so much for the fast answer. 
actually I just made it work

a bit randomly, after some updates, the driver appeared again, and then by modprobe lw it makes it active...


thanks again for your interest,

Giovanno

I have still a problem to make the microphone working... but will poster at another place the question...

---

### Post by The Toxic Mite on 2009-12-13
Nice to hear you got it working! :D

---

