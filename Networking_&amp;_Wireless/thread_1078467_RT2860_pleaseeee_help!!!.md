---
title: "RT2860 pleaseeee help!!!"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by Myronray on 2009-02-23
[SIZE="5"][SIZE="6"]hi to all ubuntu experts

i tried to install RT2860 driver for my MSI wind u100x but i git some headache for this, i follow this instruction [http://k.dieplz.net/evolution/2008/11/22/wlan-in-ubuntu-8-10-on-new-msi-wind-u100/](http://k.dieplz.net/evolution/2008/11/22/wlan-in-ubuntu-8-10-on-new-msi-wind-u100/) but no luck, im installing in hardy heron.

first code i execute in terminal >> sudo aptitude install debhelper module-assistant got no error

second >> sudo m-a a-i rt2860 and got an error it says  Build of the package rt2860-source failed

 dh_testdir                                                                 &#8593; 
               &#9474; dh_testroot                                                                &#9646; 
               &#9474; dh_clean                                                                   &#9618; 
               &#9474; /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules     &#9618; 
               &#9474; make[1]: Entering directory `/usr/src/modules/rt2860'                      &#9618; 
               &#9474; dh_testdir                                                                 &#9618; 
               &#9474; dh_testroot                                                                &#9618; 
               &#9474; dh_clean                                                                   &#9618; 
               &#9474; dh_clean: Sorry, but 6 is the highest compatibility level supported by     &#9618; 
               &#9474; this debhelper.                                                            &#9618; 
               &#9474; make[1]: *** [kdist_clean] Error 1                                         &#9618; 
               &#9474; make[1]: Leaving directory `/usr/src/modules/rt2860'                       &#9618; 
               &#9474; make: *** [kdist_build] Error 2                                            &#9618; 
               &#9474; ^Y                                                                         &#9618; 
               &#9474;                                                

i done this before in intreped ibex it works perfect but in hardy heron doesnt work, is there anyone can resolve this problem? 


thanks and much appreciated

Myron

[/SIZE][/SIZE]

---

### Post by komputes on 2009-02-25
This is being tracked as 210725. 
bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210725/comments/172](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210725/comments/172)

Can you confirm this works for you? You can try booting from the Jaunty LiveCD Daily build: [http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/current/jaunty-desktop-i386.iso)

---

