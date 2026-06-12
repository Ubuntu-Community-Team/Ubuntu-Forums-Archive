---
title: "WPA wireless stopped working after recent update"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by grettiron on 2010-09-04
Hi all,
I have an EEE 1000 that successfully connected to WPA networks until yesterday. I tried re-installing the RT2860 drivers that had been previously modified and did not have success.
 
Additionally, I just installed 10.04 on a Gateway laptop that's a few years old. It immediately connected to the WPA network and I ran the updater. Lo and behold, after updating it no longer connects to the network.
 
What is going on!?! Very frustrating as it USED to work and now no longer works :(

---

### Post by mileniasm on 2010-09-04
I have the same problem! I have an EEE PC 1001HA. I've been going through the forums for hours now and I can't find a solution. I think I'll have to re-install... AGAIN. This Lynx version is really not working for me - wireless is always a problem, mic not working properly, etc. etc. I fix one thing, another breaks after an update. I wonder if that will continue to be a problem with Maverick... 

I don't want to go back to Windows and I hate to become an Apple slave like most of my friends... but if I can't find a **reliable** alternative soon, I'm going to have to give in to the Mac craze...

---

### Post by bosamber on 2010-09-05
Same issue here. Wireless stopped working after an update on september 4 2010.

The wireless networks are available, both via notification area and using 'iwlist scan', but I can't connect to my WPA2 network. The available networks appear to have very weak signals, but my other laptop (Windows) shows them to be strong enough. 

Plugged the cable back in, so I can use internet, but I'd rather use wireless.

Anyone an idea how to solve this? I'd appreciate help.

---

### Post by grettiron on 2010-09-06
It's working now. Had to not only re-install, but rename the old rt2860.ko file in /lib/modules/.../staging/rt2860 and follow through with the depmod/modprobe commands. Why didn't I just do this at first? ](*,)

---

### Post by skatart on 2010-09-17
> **grettiron said:**
> It's working now. Had to not only re-install, but rename the old rt2860.ko file in /lib/modules/.../staging/rt2860 and follow through with the depmod/modprobe commands. Why didn't I just do this at first? ](*,)

can you please explain with a little bit more information 
what did you do?

thnx ;)

---

