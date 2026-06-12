---
title: "Wireless using staging usb rt2870??"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by EMateer on 2011-04-22
I've compiled and installed my rt2870sta.ko and the firmware to the correct locations but my ubuntu 10.10 is loading the one under
/lib/modules/2.6.38-25-generic/kernel/drivers/staging/rt2870/rt2870sta.ko. How do I get it to use the correct driver? I've attached a screenshot of the module info. Thanks

---

### Post by chili555 on 2011-04-22
Why do you believe the one you compiled is correct and the built-in is not? Please post:```
lspci -nn
lsusb
lsmod | grep rt2
dmesg | grep -i rt2
```Thanks.

---

### Post by EMateer on 2011-04-22
I just shut that computer down after banging my head for days. I'll get that other info probably tomorrow. No matter what I try I can't get my usb wireless speed past 54 mbps. I have a 150 adapter that works elsewhere (windows) and I've tried two other 150 adapters that work elsewhere (windows again). I put on a whole new kernel, nothing is working. Very frustrating. Thanks for your response. I'll write back with info tomorrow.

---

### Post by EMateer on 2011-04-23
Attached is the output screen shots. I did do the obvious and renamed the staging .ko file and copied over my compiled file but that didn't even give me any wlan0 at all. Thanks for your time.

---

### Post by chili555 on 2011-04-23
The compiled version would give you an interface of ra0, not wlan0. Do you have that? Can you connect?

A lot of people have struggled getting N speeds with rt2870sta; some have and some have not. I wish I knew the magic trick.

---

### Post by EMateer on 2011-04-23
I'm getting wlan0 and it works great up to 54 mbps. Since I've got an N router and adapter, I wanted 150 but if I'm not going to get it with rt2870sta then so be it. At least I've learned a lot. Do you know of an adapter and driver combo where I can get 150? I'm not committed to my adapter, don't mind spending a reasonable amount of $ so if I was pretty sure I could get it with a different one, I'd be willing to try it. Thanks again.

---

### Post by chili555 on 2011-04-23
> **EMateer said:**
> I'm getting wlan0 and it works great up to 54 mbps. Since I've got an N router and adapter, I wanted 150 but if I'm not going to get it with rt2870sta then so be it. At least I've learned a lot. Do you know of an adapter and driver combo where I can get 150? I'm not committed to my adapter, don't mind spending a reasonable amount of $ so if I was pretty sure I could get it with a different one, I'd be willing to try it. Thanks again.I do not, sorry.

---

### Post by EMateer on 2011-04-24
Would you know why it's loading from staging and how to change that? I don't mind playing around with those settings (actually, time permitting, it's fun to learn) but I don't know where they are. Any help is mostly appreciated and thank you for your time.

---

### Post by chili555 on 2011-04-24
What was the process you used to compile the downloaded driver? sudo su, make, make install, exit? If so, the 'make install' part should substitute the compiled version for staging.

I thought you had that handled:> I did do the obvious and renamed the staging .ko file and copied over my compiled filePlease post:```
sudo updatedb
locate rt2870sta
```The first step will take a few moments; please be patient.

---

### Post by EMateer on 2011-04-24
I'll have to try those other items you mentioned later. I did do the install though and it copied to the .../kernel/drivers/net/wireless folder (may not be exact naming since I'm typing from memory). Also, I did copy over the .ko that is in the staging folder but then I totally lost the wlan0. I thought maybe I was missing something because that first screen shot, in my first post, showed that the firmware of rt3070.bin, and others, were loaded too.

---

### Post by EMateer on 2011-05-12
Well, I only put this aside temporarily but decided to abandon the effort on Ubuntu. Since then, I've installed Fedora, not been able to connect at all, re-installed Ubuntu, back to 54, then just put tested out the live DVD of Gentoo. All of the other live DVDs didn't connect at all wirelessly since I needed to make the blacklist change (hence the need to actually install Fedora, which didn't even work then). Gentoo not only found my wireless network, it's connecting at N speeds. The only reason I'm not at 150 fully is reception but I'm getting over 80. I'm sure Gentoo has other headaches but that computer is primarily to be used for streaming video from the internet so I might have to go with Gentoo. Thought you might like to know.

---

