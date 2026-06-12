---
title: "Ubuntu 10.04 wireless connection is racist"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by snarko on 2010-05-06
I installed ubuntu 10.04 (gnome) on dell vostro 1510 with a Broadcom wireless card. 

First the network manager couldn't connect to any wireless network whatsoever (wired connection was fine). 

what I did:
sudo modprobe -r b43 b44 ssb
sudo modprobe b43
sudo modprobe b44

and that fixed it, allowing me to connect to my home network. What a joy. 

But apparently it wouldn't connect to any **other** wireless network out there, no matter how much I whisper to the laptop that this is a brutal discrimination. bummer. 
Btw, it **does identify other networks**, indicating if they are secured or not but when trying to connect nothing happens and I get the "!" (no connection symbol) on the networking icon. 

It will not even try the next available network. 

I tried to completely remove and then install the drivers (with the synaptic package manager)  but it didn't work. 

Any suggestions?

---

### Post by snarko on 2010-05-07
It now works but only god knows why.

I tried (again) to completely remove the broadcom driver and reinstall and suddenly it works just fine - connecting automatically and allows me to choose a network. 

I'm not sure why it worked this time and not when I did remove+install 2 days ago. I guess 2 is a charm.

---

