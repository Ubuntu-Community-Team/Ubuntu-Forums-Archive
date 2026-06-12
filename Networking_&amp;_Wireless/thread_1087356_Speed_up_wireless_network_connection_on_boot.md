---
title: "Speed up wireless network connection on boot?"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by BassKozz on 2009-03-04
How can I speed up the process of connecting to my routers WiFi connection on bootup?

On my main laptop (Dell e1505 - Ubuntu 8.10) it takes forever to connect to my router's wifi, however on my eeepc (901 - Ubuntu 8.04) after login it's almost instantanous...

So how can I speed up the time it takes to connect to my wifi router?
Is there a way to have it start searching for a connection even prior to login?

---

### Post by bodhi.zazen on 2009-04-04
Moved at the OP request and bumped.

Can you tell us anything of your connection ?

My only suggestion is to disable network manager and directly configure your wireless card in a boot script of /etc/rc.local

---

### Post by BassKozz on 2009-04-05
> **bodhi.zazen said:**
> 
Can you tell us anything of your connection ?

My connection is to a wireless 802.11g router (Buffalo WHR-G54S) running [Tomato Firmware]("http://www.polarcloud.com/tomato") and using WEP (I know, I know, but there are some legacy devices on my home network that don't allow WPA) .

> **bodhi.zazen said:**
> 
My only suggestion is to disable network manager and directly configure your wireless card in a boot script of /etc/rc.local
How would I go about setting that up?

---

### Post by bodhi.zazen on 2009-04-05
use iwconfig

[http://www.techmetica.com/howto/manual-wireless-configuration-with-iwconfig-in-ubuntu/](http://www.techmetica.com/howto/manual-wireless-configuration-with-iwconfig-in-ubuntu/)

---

