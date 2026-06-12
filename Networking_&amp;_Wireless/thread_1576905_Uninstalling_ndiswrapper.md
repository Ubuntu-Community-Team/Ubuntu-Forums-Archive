---
title: "Uninstalling ndiswrapper"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by Ernie S. on 2010-09-18
So after a quick look around the forums, I haven't seen anything on removing ndiswrapper. What I have done is removed ndiswrapper via synaptic. Now in order to start my wireless card I have to issue:

rmmod ndiswrapper
modprobe ath9k
ifconfig wlan0 up

Basically this is a pain. Does anyone know how to get rid of ndiswrapper completely and set things up to use ath9k automatically? 

Thanks in advance,

Ernie

---

### Post by Ernie S. on 2010-09-26
^bump

---

