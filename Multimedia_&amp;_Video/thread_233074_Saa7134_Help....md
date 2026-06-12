---
title: "Saa7134 Help..."
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by LeonHeart on 2006-08-09
Hi guys.
I have recently installed Ubuntu Dapper Drake (6.06 LTS)
and there is one thing I'd like to ask you about my tv tuner:
In order to get my tuner wokr I always do this:

1) sudo rmmod saa7134_alsa
2) sudo rmmod saa7134
3) sudo modprobe saa7134 card=16

How can I configure the kernel so as to autoload the correct module
on startup so I don't have to do all this myself everytime I want to 
watch tv?

---

### Post by gborzi on 2006-08-09
From what you say it seems the kernel module is not able to correctly autodetect your card, but that the correct module is loaded. To force card=16 open /etc/modprobe.d/options > sudo gedit /etc/modprobe.d/options and add the following line in it: > options saa7134 card=16
To check if it works, unload the module and reload it without the card=16 option on the command line. Then check with your TV application.

---

### Post by LeonHeart on 2006-08-09
Thanks man, it works...........

---

