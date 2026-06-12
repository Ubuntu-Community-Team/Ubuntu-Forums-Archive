---
title: "New Nvidia card Module problem!!"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by linuxmick on 2006-10-10
Hi forum,

I am thoroughly enjoying Ubuntu, while I am new to Linux I am picking it all up as I go along, but would like to learn a little more about changing out video cards between Linux systems. 

I was using an Nvidia TNT Riva 64 on my Dapper 6.06 system. I had installed the legacy drivers (7174) as described in the Ubuntu Documentation Nvidia/Drivers section and it was working.

Recently I got a new card. An Nvidia Geforce FX 5200 AGP.
I was following the instructions for loading the drivers nvidia-glx, and then when I attempt to activate them it changes my xorg.conf file and then the X server won't come up. When I attempt to Startx: I get an error message stating: 
 "API mismatch. Nvidia kernal module has version 1.0-7174 but this X module has version 1.0-8762."

After that I did a sudo dpkg-reconfigure -phigh xserver-xorg, and startx brings my X server back up. It appears to be reconfiguring to an older backed up Xorg.conf file. So how do I go about getting the older Nvidia kernal module 7174 out, and getting the new 8762 module loaded and running in the current Xorg.conf?

Thank you in advance for any and all comments or assistance.
Mick

---

### Post by tseliot on 2006-10-10
do you use a wireless card to connect to the internet?

if not, try envy (it will solve the whole mess for you):
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by linuxmick on 2006-10-10
Hi tseliot,

Yes I do use a wireless card. Why?
Mick

---

### Post by linuxmick on 2006-10-10
Ah, I see why now. I just jumped over to the 'envy' script page.

Well I have a Ralink wireless card using the RT2500 driver.
Will use of the 'envy' script affect that? I mean it was recognised at install, I didn't have to go get any extra funky modules for it. 
What do you think?
Hey thanks for mentioning the 'envy' script. I appreciate it.
Mick

---

### Post by linuxmick on 2006-10-11
Problem solved!!

Okay, I got your 'envy' script and used the uninstall option first, then the install option. It took care of it all. The card is activated and the xserver is up and running. 
As far as I can tell, it didn't break anything else on the system. Wireless access is still good. 
I just got done going through some of the 3D games I couldn't play until now.
Thank you very much tseliot! :D
Mick

---

