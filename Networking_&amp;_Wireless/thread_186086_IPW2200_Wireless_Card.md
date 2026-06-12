---
title: "IPW2200 Wireless Card"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by TuXethic on 2006-06-01
Hello every one in here! I love this new U6 release :D I've installed it on my laptop in less then 15 minutes :-D

Unfortunately, I have small problem with my wireless card. It detected it fine, I can see it but I cant connect to internet. My old settings that worked on previews release, did not work this time.

```
sudo gedit /etc/modprobe.d/ipw2200
options ipw2200 hwcrypto=0
save
then run: modprobe -r ipw2200
and then: modprobe ipw2200 hwcrypto=0
```

I had my SSID Broadcast disabled, I've enabled it to test the connection nothing again. I use WEP hex key.

I dont know what is gowing on ](*,) Please help!

When I do "dmesg | grep ipw", here is what I get:

```
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
ipw2200: Copyright(c) 2003-2006 Intel Corporation
Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11 a channels
```

Do I need to install ipw2200 drivers my self manually? ](*,)

---

### Post by TuXethic on 2006-06-01
OK, I dont know why but my connection only worked when I did this settings above after I configured my router with settings like so:

SSID Broadcast: Enabled
Authentication: Open System

for some reason it wont work with SSID disabled and Shared key authentication. Does any one have a clue, why!?

---

### Post by TuXethic on 2006-06-01
[QUOTE=TuXethic]OK, I dont know why but my connection only worked when I did this settings above after I configured my router with settings like so:

Authentication: Open System

for some reason it wont work with Shared key authentication. Does any one have a clue, why!?[/QUOTE]d

---

### Post by ibanez88 on 2006-06-14
Strange but this seems to be a problem with only the LTS release CD.  I have a Flight CD (forget which one) where ipw2200 works better, even with Shared key.  I've kept up with the apt-get upgrades so it was effectively the same as the release version and it worked fine.  However because I'm anal I installed fresh from the release CD, thinking there might be a few fine points that would be better experienced this way.

Bad move apparently, because the wireless is borked.  Possible solutions:

1) revert to editing /etc/network/interfaces by hand, checking to see if including "restricted" in the key line solves the WEP shared key problem

2) re-install using the Flight CD and sudo apt-get upgrade from there.  I wouldn't endorse this wholly at the moment because I haven't had much time to play around with the new install - other solutions may exist.

It should be noted that even on the Flight version I had to create a script that issued sudo dhclient on connect via kwifi.

---

### Post by rickg on 2006-06-14
Ah, the IPW2200 battles. Been doing that dance awhile now myself...

Currently I have the SSID being broadcast and no security, so this may or may not work for you.. but try adding these lines to /etc/modules: 

   ieee80211
   ipw2200

It *seems* that the wireless is more reliable since I tried this (after trying just about everything else). 

Next thing up is to fall back to the stable IPW2200 driver (1.10, vs 1.11 in Dapper). I could always go back to XP but... nah...

---

### Post by ibanez88 on 2006-06-14
Also I should add that if I set my shared-key WEP parameters using either Kwifi or command line I get: 

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Invalid argument.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; Invalid argument.

---

