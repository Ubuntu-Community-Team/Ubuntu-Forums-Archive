---
title: "How to remove and reinstall Nvidia driver in ubuntu 8.4"
date: 2009-02-17
forum: Multimedia Software
---

### Post by asti_bg on 2009-02-17
Hi everyone. 
I`m a beginner in linux systems ...
I have installed Ubuntu 8.4 a few days ago. So everything was working since I decided to update my video driver (I don`t know why ... just decided that if it is from official nvidia site it will work better ... but now I see it did not )
So I have downloaded the driver from nvidia site ... read the manual for noobs how to install it... and everything was OK until I rebooted (I stoped the x server , installed the nvidia driver ... it said that it needs to compile new kernel because on the site there was no kernel for me ... everything was Ok and I rebooted)
After the reboot I ran in Low Graphic mode... The nvidia settings says "You do not appear to be using Nvidia X driver please edit your X configuration file and restart the X server " 
So I tried to install it again ... then tried to recovery the X server in recovery mode ... then tried to install the driver again with Hardware Drivers. 
So it is a big mess, and I want if it is possible to delete all about nvidia drivers and settings and install it again with Hardware Drivers tool - that worked the first time (after installing Ubuntu)

P.P. Excuse me if the question is very stupid, but I`m really new in this stuffs, so please explain it as simple as possible.

---

### Post by duott on 2009-02-17
>I want if it is possible to delete all about nvidia drivers

This line may help:

```
sudo apt-get purge nvidia-*
```

---

