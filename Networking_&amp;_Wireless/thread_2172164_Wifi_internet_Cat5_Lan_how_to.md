---
title: "Wifi internet Cat5 Lan how to?"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by geekyhawkes on 2013-09-03
Hey guys and girls;

I am trying to get my laptop networking setup to allow me to connect to the internet via wifi but my LAN/NAS/Printer etc via the Cat5 cable. 

For lots of not very interesting reasons, my internet router is wifi only and as such doesnt support Cat5, my NAS and printer and Squeezebox are all setup wired via an old Router with DHCP running.  

Is there an easy way I can set this up to work?  Currently when I want the internet I unplug the Cat5 cable from my laptop, then plug it back in when I want to get onto my LAN.  It works, but i cant help thinking there has to be a better way!

Thanks;

Andy

---

### Post by zero2xiii on 2013-09-04
Hay,

Since its been a day and still no reply I'll have a go:
[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

if after following instructions there you are not getting anything working better. Supply the outputs from the article and we can try and help you set up your routing properly. I have never done this before, but it does not seem hard at all.

Cheers

---

### Post by scbingham on 2013-09-04
Why not just connect your internet connection to your old router and then connect that to your wireless router with a cat5 cable?

Edit: Obviously you will have to disable dhcp on your wireless router as that is all handled by your old one.

---

### Post by geekyhawkes on 2013-09-05
> **scbingham said:**
> Why not just connect your internet connection to your old router and then connect that to your wireless router with a cat5 cable?

Edit: Obviously you will have to disable dhcp on your wireless router as that is all handled by your old one.

I wish it were this imsple, as i stated in my first post the internet connection device i am using doesnt have cat5 and the old router doesnt support bridging, so sadly the simple option isnt available.

---

### Post by scbingham on 2013-09-05
How does your wifi router connect to the internet? It's usually cat5 from a modem.
Your old router would not need to act as a bridge, just act as a router ie cat5 in from internet modem & cat5 out to other devices and the wifi router. You said it already handles the dhcp, so leave it doing that.
Should be straight forward or is there something you haven't mentioned? What make/model are your routers?

Edit: lol you're not dumb, just finding your way :-) Everyone started somewhere.

---

### Post by geekyhawkes on 2013-09-08
So the problem I have is that the internet router has NO cat 5 ports at all.  So I think my options are all relating to port forwarding or my network setup.

---

### Post by Merrattic on 2013-09-12
This [http://www.cyberciti.biz/networking/howto-connect-two-wireless-router-wirelessly-bridge-with-open-source-software/](http://www.cyberciti.biz/networking/howto-connect-two-wireless-router-wirelessly-bridge-with-open-source-software/) is what you want to do, but if your old router will not work as a repeater or bridge, and you can't install an open source solution like openWRT you are a bit stuck.

---

