---
title: "Wireless connections not detected - ubuntu 10.10"
date: 2012-07-03
forum: Networking &amp; Wireless
---

### Post by sheeru on 2012-07-03
In my ubuntu 10.10, suddenly wireless connections are not getting detected. My wireless network card is Brcm4313. Usually 'wl' wireless driver in kernel helps in establishing my wireless network connection.

So, i tried to restart my wl.ko module using the below command:
> sudo rmmod wl
sudo modprobe wl 

It resulted in error:
> sheeru@sheerapthinath:~$ sudo modprobe wl
FATAL: Error inserting wl (/lib/modules/2.6.35-27-generic-pae/updates/dkms/wl.ko): Invalid argument

please help me in establishing my wireless connections

---

