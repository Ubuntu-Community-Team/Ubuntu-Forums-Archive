---
title: "Wireless card detection"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by FR350Z on 2009-01-22
Hi guys, I'm a new Ubuntu user..

I just installed 8.10 a few days ago, a clean install on a seperate partition. I love everything about it, except for the fact that my wireless card doesn't seem to be activating/working.

My laptop is a Compaq Presario V2000, and I think I have the Broadcom BCM4318, not sure, someone correct me. 

I installed the Network tool, but it doesn't work. My wireless button light stays unlit, even if I press/hold it. 

I tried using the ndiswrapper, wouldn't work.

Any help? 

Thanks.

---

### Post by acimmarusti on 2009-01-23
Hey there,

I'm also using the same broadcom 4318. I'm using it under ubuntu 8.10 without trouble.

Go here, download the deb package under b43-firmware

[http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/)

(I know you are going to say this package is for hardy ubuntu 8.04, but trust me...I've tried the package for intrepid and it doesn't work!)

Once you do that, double click on the package to "execute" it. It will probably ask you for your administrator password. When you are done, restart your computer. Your wireless light should turn on after you log back in ubuntu and you should be able to detect wireless connections close to you.

I hope this works for ya. It has worked for me. If not you are going to have to use ndiswrapper again...

---

### Post by FR350Z on 2009-01-23
Thank you VERY MUCH!

This worked perfectly, I'm posting this from Ubuntu! :D

Once again, thanks for your help!

---

### Post by acimmarusti on 2009-01-23
Glad I could help.

I've had my share of trouble with this. It seems the newer firmware or driver is NOT working correctly.. this should be submitted to a higher instance

---

