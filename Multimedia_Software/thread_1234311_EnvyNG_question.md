---
title: "EnvyNG question"
date: 2009-08-07
forum: Multimedia Software
---

### Post by Hydrid on 2009-08-07
Do i have to uninstall fglrx driver so i can install EnvyNG or i can install it above ati restricted fglrx driver???

I have a ati HD 3850 agp card - 4gb ram - 24" full HD screen and i am having frame rate problems while playing media files with totem or vlc ( i have installed every available codec for linux ubuntu 9.04 but again the problem exists).While i open e.g an avi the movement its has lags - cuttings and the sound some times comes first and after the image.

Does have anyone a solution? I really dont want to use windows just because i cant see my favourite videos

---

### Post by markbuntu on 2009-08-07
Vlc uses the xine engine which you need to set to Xv to avoid tearing etc. Totem uses either gstreamer or xine depending on which version you installed. If you have the gstreamer version then you can change the Video setting to X Window System (No Xv) in System/Preferences/ Multimedia System Selector.  Other settings may also work.

You should always remove old drivers before installing new ones. Do not forget to remove the kernel modules also. Envy has never worked for me. It always misinstalled the driver. 

if you want the latest driver you should get the one from the ati site. There is a link at the driver download page for installation instructions.

---

### Post by Mia1990 on 2009-08-08
some people say envyng works good some say it's bad myself i have never used it.You should use the driver in hardware drivers or if you know the one for your card download it from there website.

---

