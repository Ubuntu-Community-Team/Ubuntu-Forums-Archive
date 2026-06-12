---
title: "Samba incredibly slow"
date: 2014-12-04
forum: Multimedia Software
---

### Post by jonttu2 on 2014-12-04
Hello!
My problem is Samba being way too slow. I am sharing files from Windows 7 computer, and I can acces the files very well from another Windows computer. It works pretty fast like that. Byt when I acces the files with my Lubuntu laptop, the transfer speed is very slow. I tried moving a 500mb file to my laptop, and it would have taken 1,5 hours. I have tried googling what I should change in the smb.conf file, but with no success. The laptop has got a good signal to the modem it self.
    Here's my smb.conf file [http://pastebin.com/GGwa1yZw](http://pastebin.com/GGwa1yZw)
As you can see, I do not know what I should change in the configuration file.
 My OS is Lubuntu 14.10.01 LTS

---

### Post by carlwsnyder on 2014-12-04
You don't state, and it does not show on your pastebin file, are you connecting through wired or wireless connection?  If you are connecting through wired connection, what is the speed of your wired connection, 1Mbps/10Mbps/100Mbps/1000Mbps(also known as 1Gbps)?  If you are connecting wirelessly, do you have an 802.11n connection on both the router and the laptop, or only 802.11b?  Are you connecting with your Windows computer through the same type of connection?

My suspicions are not with your Samba setup, but with your connection.

---

### Post by jonttu2 on 2014-12-05
I have tested sharing the files from desktop computer to another Linux desktop computer, but it didn't help. Anyways, my laptop is connected wirelessly to P-660HN-T1A modem, which has LAN rate of 100M and WLAN 150M. The modem does support 802.11n, but I can't figure out does the laptop support it. My laptop model is Aces Aspire 5738ZG. Internet through the wifi is still a lot of faster then the file transfering through LAN

---

### Post by jonttu2 on 2014-12-07
Sorry for double post, but I still need help! I don't believe the reason could be in the connection, since the shared stuff works well with everything except my Linux computers. Here's a pic about my configuration: [http://files.1337upload.net/something-980c95.png](http://files.1337upload.net/something-980c95.png)
It must be in the settings, since desktop computer with wired computer can't get a video file quickly enough to stream video.

---

