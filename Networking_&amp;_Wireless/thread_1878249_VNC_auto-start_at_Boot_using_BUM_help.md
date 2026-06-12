---
title: "VNC auto-start at Boot using BUM help"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by BHEJU on 2011-11-09
Hi 
I want to configure VNC to auto start on boot on my headless 11.04 desktop.
The Options I found are:
1- write up couple of scripts for init.d and mess with some settings directly from files. 
I do not have time to take the risk of messing with files and scripts and also I can not find proper step-by-step help for this.
2- Boot Up Manager (BUM): GUI interface to mess around with services and apps
This is what I need help with. Does anyone know how to configure BUM to run VNC at start up? this would be big help.

3-webmin: this sounds like overkill for what I want.

Please help me with the easiest way to configure my boot up apps to add VNC so that I can log in to the machine remotely right after reboot.

Thanks,
Smit

---

### Post by josephmills on 2011-11-09
Hi there. there is also a program called sysv-rc-conf this is kinda like bum. how it works first download it and install open terminal 
```
sudo apt-get -y install sysv-rc-conf 
```
after installed open it up from the terminal 
```
sudo sysv-rc-conf 
```
you will get a screen that looks like this 
[img]http://img228.imageshack.us/img228/368/screenshotat20111109131.png[/img]

you can then scroll down to the one of your liking and press space bar to activate that "one" on boot. In a nut shell the ones with the [x] means that it is turned on the ones with the [] means that "it" is turned off. I hope that this helps.
I know that this is kinda a "old" way about going about things but it is what I know I hope that it helps:)

---

### Post by BHEJU on 2011-11-09
Thank
This is very similar to BUM. However, I am confused by the numbers from 1-2-3-4-0-5-6. I would appreciate crash course on it and also what should the VNC line look like. 

Thanks,
Smit

---

### Post by BHEJU on 2011-11-10
I tried BUM and this one as well. But I don't even see VNC in the list?
How do I add it??

---

### Post by BHEJU on 2011-11-14
BUMP..
Please help.

---

### Post by Steve54 on 2011-11-15
This is the guide I followed with step-by-step instructions. It gives you two or three choices.
 
[http://www.havetheknowhow.com/Configure-the-server/Run-VNC-on-boot.html](http://www.havetheknowhow.com/Configure-the-server/Run-VNC-on-boot.html)

---

