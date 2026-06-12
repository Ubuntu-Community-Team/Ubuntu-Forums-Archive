---
title: "WNC-600 Wireless Problem"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by MaeTroX on 2009-04-19
Hi, new to ubuntu/linux installed it yesterday and noticed that my wireless conection don't work so I started to look at the list with supported cards and mine was not there. So I followed the link on what to get for information and then post it here. I could not find out the model/brand but everything else should be OK, I hope.

---

### Post by chili555 on 2009-04-19
It looks like it's working perfectly well to me. Your *dmesg* shows a number of 'No Probe Response...' and your scanning result shows a signal strength of 28/100. How far away is that router or access point? 

I have trouble connecting and staying connected at anything below 40/100.

---

### Post by MaeTroX on 2009-04-19
It's not far away, if I boot up with windows I have 100% signal. Is there something I have missed, I mean I cant take the exe drivers and install on linux right?

When I try to connect to our SSID it think for a long while then I get the message network have been disconnected or something like that.

---

### Post by chili555 on 2009-04-19
> I mean I cant take the exe drivers and install on linux right?
Well, you can, but let's keep that little tool in our vest pocket until we really need it. I noticed, as well, that dmesg reports it cannot change channels and that your router is on channel 4. Do we get any complaints if we do:```
sudo iwconfig wlan0 channel 4
```Then, we'd love to see:```
sudo iwconfig
```Thanks.

---

### Post by MaeTroX on 2009-04-19
I will try sudo iwconfig wlan0 channel 4 this tomorrow, right now it's pretty late here.

---

### Post by chili555 on 2009-04-19
Will you please also try:```
sudo ifconfig wlan0 down 
sudo rmmod -f ath9k
sudo modprobe ath9k btcoex_enable=1
sudo ifconfig wlan0 up
```Does this make any difference in your ability to connect?

This is a temporary fix; if it works, we will need to take a few extra steps to make it permanent. Alone, it will not survive a reboot.

---

### Post by MaeTroX on 2009-04-20
Ok, it did not seem to have helped at all, but I saved it into a txt file for you to view

---

### Post by chili555 on 2009-04-20
> FATAL: Error inserting ath9k (/lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)And what did *dmesg* say about it? Please do:```
dmesg | grep ath9k
```Thanks!

---

### Post by MaeTroX on 2009-04-20
Ok, here it is

---

### Post by chili555 on 2009-04-21
This is quite mysterious. This thing does everything perfectly...except connect! My next suggestion is to install linux-backports-modules-intrepid. There is evidently an improved ath9k in there. Please do:```
sudo apt-get install linux-backports-modules-intrepid
```It will want to also install some dependencies, which you should accept. Then let us know if you are able to connect.

---

### Post by MaeTroX on 2009-04-21
OK, this is weird I started the computer and it connected without me doing this commando

sudo apt-get install linux-backports-modules-intrepid

So should I still do that commando or wait intill next time I start the computer and it don't connect?

Edit 1: It's true that it don't got great signal it got about 40% as highest.

---

### Post by chili555 on 2009-04-21
I would wait. Is your wired ethernet connected, as well as your wireless? Network Manager doesn't like that.

---

### Post by MaeTroX on 2009-04-21
No, I have disabled wired ethernet in the bios, since I dont use wired at all

---

