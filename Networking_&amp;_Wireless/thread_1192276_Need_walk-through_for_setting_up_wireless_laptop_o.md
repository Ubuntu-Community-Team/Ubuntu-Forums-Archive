---
title: "Need walk-through for setting up wireless laptop on network"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by fivefour on 2009-06-19
I have already determined that the wireless card in my laptop is functioning properly and that driver is present. Worked fine on my network with XP. Can somebody walk me through the process of setting this machine up on my network (replaced XP w/ubuntu). Using Linksys WRT110 router. Wired machine is running Win XP, if that matters.

---

### Post by fivefour on 2009-06-20
Got to be someone who knows how to do this. Going to have to reinstall XP in the meantime, as I need Internet access w/my laptop.

---

### Post by jerrrys on 2009-06-20
until you find a better answer maybe this will help

[http://www.google.com/search?q=Linksys+WRT110+router+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Linksys+WRT110+router+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Iowan on 2009-06-22
I haven't set up wireless at home, yet, but when at the library or other favorite hotspots, (if I remember to enable wireless) it's a simple left-click on NM icon, and pick the target.

---

### Post by Mark2322 on 2009-06-22
Okay, I am new to Ubuntu so I'll just go ahead and say that I dont know exactly what I am doing but I have been able to get windows wireless driver to work on my laptop. However after trying out the laptop remix, I was unable to use my wireless card. So, I went back to 9.04. You first need to install the GUI which is ndisgtk. To do this hook up a wired connection to your laptop, open the terminal and type: sudo apt-get install ndisgtk. It will ask for your password enter and let it do its thing. As far as I have gotten, I know that first you need to blacklist the native driver on your laptop which I assume is your hardwire connection. You have to identify this connection by entering(in the terminal) lspci. There are other commands that follow like -n, but the lspci command will show you the chipset number at the bottom I assume this is correct. Okay according to the free doc on ubuntu forums you accomplish this by first opening a terminal and enter the following commands:
echo -e 'blacklist bcm43xx\nblacklist wl'( I think the 2 xx's you need to fill that in yourself like mine is bcm4311). Next you type( I think and this is where I need some help) 
sudo tee -a /etc/modprobe.d/blacklist. Then download the driver you need to a flash drive or have it already saved on your desktop, open up windows wireless drivers and choose to install a new driver and point it to the location of the .inf file in the executable. You made need to install ndiswrapper-utils-1.9 and all you gotta do is open the terminal and enter sudo apt-get install ndiswrapper-utils-1.9.
This is as far as I have gotten. I dont know if it will work for you but it should put you in the right direction. If it works our for you lemme know if I am wrong because like I said I havent been entirely successful and have been unable to get a clear solution.

---

