---
title: "Cannot ping router- 12.10"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by dbus08 on 2013-02-12
Hello I am having difficulty using my home network.
I can connect to it but cannot ping the router nor out.  Its obviously not a dns issue as I cannot ping the router nor any sites via ip's.
When using windows 7 I can connect to the router and Internet with no issue
WIth ubuntu I can connect and use my phones hotspot and I can also connect to my schools Internet. 
Both of which work perfectly fine. 

I think it may be an issue with wireless N  but my driver (ath9k) wont let me disable wireless N.
eg.

sudo ifconfig wlan0 down
sudo rmmod -f ath9k 
sudo modprobe ath9k 11n_disable=1 * error at this step 
sudo ifconfig wlan0 up * at this step i receive an error saying it could not find/load module

When I am connected to my school network iwconfig reports back a bit rate of 54 Mb/s
which is G.
When I am connected to my home network iwconfig reports back a bit rate of 1xx Mb/s
(i don't recall the bit rate exactly but i remember it being 100+)
I would post sections of code documenting each command and what I receive back but like a frustrated fool I forgot to save them. 

I should note that I am a ubuntu/linux noob 
Any help/solutions would be much appreciated.

---

### Post by ahallubuntu on 2013-02-12
~

---

### Post by dbus08 on 2013-02-12
Ty that seemed to work but Internet speed is ridiculous slow and I have a lot of packet loss. 
Time to look at forum some more.

---

