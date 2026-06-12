---
title: "FCOE - getting started"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by tejask on 2013-06-28
i am trying to configure FCOE on my LTS 12.04 system running on a dell M910 blade that has the Broadcom 57810 converged adapter

when i run the sudo fcoeadm -c eth4, i get the error message Failed to open /sys/module/fcoe/parameters/create

the create folder does not exist

what am i missing ? this is the first step is doing the FCOE config

---

### Post by chili555 on 2013-06-28
I know nothing, zero, zip about fcoe. Zero! I do know about 1% about how modules loading, etc. works. As you have had no answer in several hours, I am going to take a guess. In order for there to be a /sys/modules/fcoe/anything to manipulate, the module fcoe has to first be loaded:```
sudo modprobe fcoe
```Then, I wonder if the command will then go better:```
sudo fcoeadm -c eth4
```You can automate all this in /etc/rc.local if you need to, I'd guess.

Hey, that's my best shot!

---

