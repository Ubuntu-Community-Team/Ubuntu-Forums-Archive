---
title: "wireless??? BCM4318"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by khuttger on 2008-12-28
Ok, Ok. I've seen several threads here that ask for help with older versions of Kubuntu and their wireless problem.

I have Kubuntu Intrepid Ibex and my wireless doesn't work. I have tried the b43-fwcutter tool driver and that has stopped working for no reason at all. I then tried to do ndiswrapper, but that may have made it worse.

I'm not sure what to do at this point, so any help would be appreciated. 

Here's some info : 

```
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

Also, I'm connecting via Ethernet right now. I have the program "Windows Wireless Drivers" and there is a installed driver there but that doesn't do anything. 

```
kyle@kyle-mobile:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: ssb)

```

Anything helps. 

Thanks alot!:)

---

### Post by kevdog on 2008-12-28
My suspicion is that there may be a problem with the order the drivers are being loaded.  Always for some reason ssb wants to load first prior to b43 or ndiswrapper, screwing up the entire process.

I don't care which driver you want to use -- ndiswrapper or b43. But since you have ndiswrapper installed right now, lets work with that.  Lets try the following:

sudo ifconfig wlan0 down
sudo rmmod ndiswrapper b43 b44 ssb bcm43xx
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up

Can you now see any wireless networks when you do:
iwlist wlan0 scan

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

### Post by sampbar on 2009-01-24
Hello, 

My guide hasn't been written for kubuntu but it should still work. So if you want to pop across to: [http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html]("http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html") and give it a go feel free!

If you need any help just reply to this thread or email me: samuelbarrett {@} sampbar.com

Samuel

---

