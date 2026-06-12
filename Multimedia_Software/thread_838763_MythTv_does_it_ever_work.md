---
title: "MythTv does it ever work?"
date: 2008-06-23
forum: Multimedia Software
---

### Post by ramadan on 2008-06-23
I've installed it( ubuntu 8.1) but no clue how to configure it, i do read the documentation but it makes it even worse so please my simple questions are:
1. my computer is not connected to network( standalone), i want to run mythtv on it along with other application so what to choose: backend, frontend or both?
2. my dvb card is skystar2 + lirc + TTS35AI, not mentioned in the hardwarelist(mythtv) are they refered to by another name? i.e is technisat mediafocus remote control is another name of mine?
any help is appreciated and please dont refer me to docs
thanks alot

---

### Post by thorgal on 2008-06-24
1- you need a kernel module that will drive your TV card
2- if 1- is set up correctly, you need the MythTV backend that will handle the database updates, take care of your scheduled recordings, etc
3- you need a frontend to communicate with the backend for watching your recordings or liveTV. BE and FE can be on the same machine. FE requires that you have a decent video card. If you are low on CPU on the FE, XvMC is your best bet for video display.

Mind you each of these 3 points are not obvious to set up if things don't work OOB. I built a mythTV server with a miniITX mobo and use remote clients (laptops, PC) as frontends. It works great, super stable and reliable but you definitely need to know your way through linux stuff, especially if you plan on setting up a remote server in your LAN. The nice thing about it is that clients (frontends) can be diskless, everything happening at server level.    

The MythTV wiki would be a good place to browse, together with the forum or user mailing list. Be prepared to sweat a bit and good luck ;)

(I wish I could tell you what I did exactly but it would take me a looong time to take you through it, sorry).

---

### Post by ramadan on 2008-06-24
thanks for reaction, I really did some homework already but for example my skystar2 is not listed on the mythtv hardware list neither is the remote . wonder if you guys use another alias for it!, where to find scan?
it is exhausting :confused:  
but I'll not give up

---

### Post by thorgal on 2008-06-24
in a terminal, type 

lspci

and see what info it spits out about your card chip. Then try to google to check if video4linux2 (v4l2) has a driver for this chip.

---

### Post by ramadan on 2008-06-24
I choosed my PC as primary back end  + front end
I've tried to find drivers to my DVB card but life is not always easy,( for linux life is always not easy :) ),  when tried to start the mythtv >> "no uPnP backend found"
what the heck is that supposed to mean,
every time i try to learn more >> just more troubles

---

