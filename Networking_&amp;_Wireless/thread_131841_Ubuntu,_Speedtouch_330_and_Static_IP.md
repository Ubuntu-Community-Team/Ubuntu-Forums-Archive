---
title: "Ubuntu, Speedtouch 330 and Static IP"
date: 2006-02-17
forum: Networking &amp; Wireless
---

### Post by simion on 2006-02-17
I've got a DSL test line at work and I setup an old dell pc with ubuntu and by following the guidelines [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) everything worked perfectly.

Having just had 8meg dsl installed at home I'd like to mirror the setup at home. The only difference is that at home I have a static IP. So I'm wondering if the only change I'd have to make is to modify would be to specify the static IP in the /etc/ppp/peers files as below:

Dynamic file:

noipdefault
defaultroute
user 'username@isp'
noauth
updetach
usepeerdns
plugin pppoatm.so
0.38

Static File:

<my static ip address>
defaultroute
user 'username@isp'
noauth
updetach
usepeerdns
plugin pppoatm.so
0.38

Logically thats the only place I can think to put the IP that sort of makes sense. I'm at work at the moment so I can't try it out until I get home. I was just wondering if the hive mind had any experience of this?

cheers
simion

---

### Post by Nyati on 2006-02-17
Simion

You might want to look at the attachment that I compiled. It works every time. I have this setup at home.

---

