---
title: "can't connect to my access point"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by herbert tamayo on 2010-05-08
Hi, recently I installed ubuntu studio karmic koala on my laptop, in the first login, the Hardware drivers applet show me the option of installed the propietary driver for my wireless card - a Broadcom wireless card, the driver is the STA- so everything was fine.

I can do: iwlist eth2 scan; I see all the access point, but when I did:
iwconfig eth2 essid myapoint key s:helloworld
I got this error:
[HTML]
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Invalid argument.

[/HTML]

i have been googling for a while but nothing my question is:
what is that? could you help me?

regards

---

### Post by herbert tamayo on 2010-05-10
Uf!, at last solved, after search a lot, even try to get answers in the IRC official channel and NOTHING, finally i got wifi in my UbuntuStudio using my Broadcom BCM4312 card, so, there are sveral steps to get this work, if you want to know just visit my blog and all answers that you are looking for are in there. here is the url:
[http://htamayo.blogspot.com/2010/05/instalar-el-driver-para-las-wifi.html](http://htamayo.blogspot.com/2010/05/instalar-el-driver-para-las-wifi.html)

all the best

---

