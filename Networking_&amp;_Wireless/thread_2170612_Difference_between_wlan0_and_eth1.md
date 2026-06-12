---
title: "Difference between wlan0 and eth1?"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by ERtzDbX on 2013-08-26
Hello all, I am running into trouble when following tutorials on compiling and setting up wpa_supplicant for use. I am trying to get its p2p (Wifi Direct) functionality working, but I am currently at the starting wpa_supplicant step. I am following the tutorial here: [http://wireless.kernel.org/en/developers/p2p/howto](http://wireless.kernel.org/en/developers/p2p/howto)
And am running the command:
./wpa_supplicant -Dnl80211 -c /path/to/p2p.conf -i wlan0 -dt


My question is, there is no "wlan0" interface on my OS (12.04) so is it okay to use eth1 which is what my wireless is using?
Should I change my wireless to use wlan0?


When I try the above command with eth1 it just goes about "removing" various networks that I have connected to in the past and never completes.


Any help at all woul really be appreciated. Thanks.

---

### Post by Truxpin on 2013-08-27
Could you please show the output from the following commands: 

sudo ifconfig 
sudo iwconfig 

I would expect you to find a wlan0 associated to the HW WiFi device...

---

### Post by wildmanne39 on 2013-08-27
eth1 is created when you use the wl driver so that is normal, when running commands you just put eth1 where wlan0 is.

---

### Post by chili555 on 2013-08-27
> **Wild Man said:**
> eth1 is created when you use the wl driver so that is normal, when running commands you just put eth1 where wlan0 is.As well as ipw2100, ipw2200 and a few others. Perfectly normal.

---

### Post by wildmanne39 on 2013-08-27
Thanks chili555, I did not know >  ipw2100, ipw2200 and a few othersalso were called eth1.:)

---

### Post by ERtzDbX on 2013-08-27
> **chili555 said:**
> As well as ipw2100, ipw2200 and a few others. Perfectly normal.

Ah, thanks a lot.  That puts my mind at ease.

Do you have any idea why starting wpa_supplicant would be seemingly endlessly looping to remove connections?  Or should I make another thread specifically for that question?

---

### Post by chili555 on 2013-08-27
> **ERtzDbX said:**
> Ah, thanks a lot.  That puts my mind at ease.

Do you have any idea why starting wpa_supplicant would be seemingly endlessly looping to remove connections?  Or should I make another thread specifically for that question?I suggest you do and include the relevant .conf files.

Is this a desktop with Network Manager running? I haven't tried it myself, but I'd assume the Ad Hoc arrangement might do what you are trying to do. Did you try that?

---

### Post by ERtzDbX on 2013-08-27
It is a laptop not running Network Manager.

My goal is to develop a Wifi Direct application for others' use, so I am trying to avoid extra required installs if at all possible.  My first step is simply getting WFD running and make some connections though to make sure I have the right drivers etc., so that is what I am going for right now.

---

### Post by chili555 on 2013-08-27
> **ERtzDbX said:**
> It is a laptop not running Network Manager.

My goal is to develop a Wifi Direct application for others' use, so I am trying to avoid extra required installs if at all possible.  My first step is simply getting WFD running and make some connections though to make sure I have the right drivers etc., so that is what I am going for right now.I see. I think wpa_supplicant is a new, different question.

---

