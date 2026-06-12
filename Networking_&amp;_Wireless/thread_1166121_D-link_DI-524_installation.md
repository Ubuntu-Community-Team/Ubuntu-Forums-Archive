---
title: "D-link DI-524 installation"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by xBlackDahliax on 2009-05-21
Hi! I'm quite a noob when it comes to ubuntu. I have recently installed it on my PC and tried to install the di-524 drivers and I couldn't. I'd be grateful if anybody instructed me either how to run the autorun.exe in the cd for the router or install the whole thing in a different way.

---

### Post by chili555 on 2009-05-21
In all the three routers that I use or have used, it is possible to set up the router without the CD. Please try the following steps:

1. There are five ports on the back of the router. One is marked ***WAN*** and that is where you should connect the ethernet cable from your cable modem, DSL modem or other device that delivers the internet to your location.

2. Connect your computer to any of the four remaining ***LAN *** ports. 

3. Open a terminal on your computer and do:```
sudo ifconfig eth0 192.168.0.2 up
```

4. Open a Firefox browser and type in the address bar:```
http://192.168.0.1
```The browser should open the administration pages of the router. The username is admin and leave the password blank. You can then set up the router. At a minimum, I suggest changing the username and password, changing the router name or ESSID (currently 'default') and setting up wireless encryption. You should then be able to go to the 'Status' tab and renew the address, that is, get an IP address from the modem.

Post back if you get stuck.

---

### Post by xBlackDahliax on 2009-05-22
When I connect the PC to the router and then the router to the internet, I can't connect to the 192.168.0.1 :/

---

### Post by Bucky Ball on 2009-05-22
I have two D-Link routers and all I ever did was just plug em in, no CD required so forget that bit. I have a DI-704P which has a print server, cable plugged into that, then two machines hardwire ethernet cable into two ports and the DI-524 directly into another port and into a LAN port on it acting as an access point for my laptop (hope that makes sense). The D-Link routers I have 'just work'. the 704P is at 192.168.0.1 whilst the 524 is at 192.168.0.2

Take the WAN out and make sure you just have the one machine connected to a LAN port. First things first, when you plug in the machine to the router with the ethernet cable, does a light come on the front panel indicating which port you have plugged into? The router can see the machine okay?

---

### Post by xBlackDahliax on 2009-05-22
Yes it does. I'm not sure if tit's a problem but two days ago when i was still having windows xp, the router or something else started rebelling against me, because I couldn't connect any of the laptops in the house (one with vista and another with ubuntu) and it indicated that the password was not correct, although nobody had changed it. I thought it's just a problem with windows, maybe a virus or so, so I cleared the disk and changed the operating system, but now I'm beggining to think that maybe it's the router's fault. It may be so, because i tried to connect using the laptop with vista either by cd or the 192.168.0.1 page and I couldn't do it. Using cd it showed that the cable is not connected.

---

### Post by chili555 on 2009-05-22
Every symptom you've described points to a defective router. I suggest replacement.

---

### Post by Kareeser on 2009-05-22
Before you try replacing it, hard reset the modem by pressing the switch on the back and holding it for 10+ seconds.

That should reset everything and allow you to set the router up again.

It sounds like someone hacked into your administration interface (not hard if you have an unsecured network and did not change the admin password) and mucked about.

---

### Post by Bucky Ball on 2009-05-22
> **Kareeser said:**
> Before you try replacing it, hard reset the modem by pressing the switch on the back and holding it for 10+ seconds.

That should reset everything and allow you to set the router up again.



Sounds like good advice. You'll need a pen or straight paper clip, hole next to the power socket. I sometimes unplug the thing for a couple of minutes also.

Don't worry about plugging your internet cable into the WAN port at this point.

---

### Post by xBlackDahliax on 2009-05-22
It worked! Thanks a lot.

---

### Post by Bucky Ball on 2009-05-22
Excellent news!

---

### Post by xBlackDahliax on 2009-05-23
It worked but just for some time... After a few hours my vista laptop stopped seeing the net, then said that the password is wrong, same with the ubuntu laptop... I'll try to service it, maybe it'll help.

---

### Post by Bucky Ball on 2009-05-23
I am presuming you have the router set up correctly as an AP (Access Point)? It is named with WEP security, etc?

Sorry if this is old news, but drop into System->Admin->Network, Unlock and check your wireless properties. That is set for Auto DHCP (gets IP from router) and you have the matching details in there to what is on the router (name of access point and WEP key)? 

Are you positive you were using your own network and not a rogue one which is in your area and now either signal too weak or they changed the password? Positive you are connecting to your own network?

---

### Post by xBlackDahliax on 2009-05-24
It's definitely mine (name and password). I managed to recover it once more. It may that everything got wrong because of the channel change. I changed it because I have problems connecting to the wan by my vista laptop. When ubuntu one is on the vista becomes disconnected and I'm not able to connect it once more. Maybe you know the solution to it, without changing channels?

---

### Post by xBlackDahliax on 2009-05-24
I must have used a wrong channel (2 and 10, as far as I remember), because now i set it to channel 11 and everything works fine. I hope that it won't change.

---

### Post by Bucky Ball on 2009-05-25
> **xBlackDahliax said:**
> When ubuntu one is on the vista becomes disconnected and I'm not able to connect it once more. Maybe you know the solution to it, without changing channels?

Hmm. I'll think about that. Generally, it is channel 6.

---

