---
title: "DLink DWA130 revb sees networks but can't connect.. Please help?"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by iMattcotv on 2010-05-25
Ok so.. I am that thing you call a n00b, only difference is I learn fast.

My problem is i don't understand exactly what to do in order to get my DLink DWA130 USB adapter connecting.

It can scan and see networks, but it cannot connect to them (open or known passwords lol)
Here are my PC Specs:
AMD Athlon64 II X 4
4GB Ram
Dual booting W7 and Ubuntu 10.04 (the regular 699mb .iso)

I followed the instructions on another forum stating to download and save on the desktop:
- ndisgtk_0.8.3-1_i386.deb
- ndiswrapper-common_1.50-1ubuntu1_all.deb
- ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb

and then enter:
cd ~/Desktop
sudo .... *.deb (I can't remember that part)

It worked, I then opened ndisgtk through terminal but I have a question here..
The driver files that I downloaded off their site for my adapter contains all XP, XP2K, Vista32, Vista64 each having their own .cat .inf and .sys file, which one do I install?

I tried entering 1susb, 1susb -v and 1spci -v but I get this:
No command '1susb' from package 'usbutils' (main)
1susb: command not found

I also get this after entering iwconfig:
lo no wireless extensions

eth0 no wireless connections

wlan0 IEEE 802.11bn 
and a bunch of info for wlan0

nothing else after that.

So what I'm trying to know and figure out is how to get Internet access working and how to install the drivers and stuff, thanks 

p.s, I am willing to learn, I'm not your average n00b. Oh, and I'm using my iPod touch to type all this so if there are any typos, it's spell correct.

---

### Post by bkratz on 2010-05-25
See your responses in the other posting in the absolute beginners talk thread.  I use the DWA-130 version A myself. Feel free to PM me.

---

