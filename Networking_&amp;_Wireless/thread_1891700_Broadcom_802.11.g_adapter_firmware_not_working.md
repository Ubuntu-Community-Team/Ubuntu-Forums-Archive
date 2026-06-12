---
title: "Broadcom 802.11.g adapter firmware not working"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by MugOfUbuntu on 2011-12-06
[SIZE=2]Hello!

I had recently installed Ubuntu 11.08 on my PC. When I saw that the wireless device needed the firmware, I went to install the firmware. Ubuntu said I needed to activate the driver so then it would work, so I did. But after I activated it, when I pressed the hardware switch on my PC the light still wouldn't come on. Before I installed the firmware, Ubuntu saw the adapter and told me it needed the firmware for it to work, but now it's like it can't even recognize it anymore. I went to the terminal window, and verified that the adapter was being recognized by Ubuntu, but in the network window it said there was no wireless. But when I typed in the command to see what wireless driver I was using, it displayed the info. So I'm kinda confused right now. Does Ubuntu recognize it, or does it not? [/SIZE][SIZE=2]


Thanks [/SIZE]  [SIZE=2]:) 

[/SIZE][SIZE=2]   [/SIZE]

---

### Post by chili555 on 2011-12-06
> Does Ubuntu recognize it, or does it not?Please help us find out. Please run in a terminal and post:```
lspci -nn | grep 0280
dmesg | grep b43
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by MugOfUbuntu on 2011-12-08
[SIZE=2]Yes,[/SIZE][SIZE=2] I tried your idea and Ubuntu didn't recognize the command. I then decided to type it without the pipe symbols. It showed the options provided in the screenshot I took of the terminal. I want to choose one of the items like the Always show domain numbers button. So I typed in -D (for always show domain numbers) in the terminal but it didn't recognize the command. There must be something I have to type before -D.


Thanks a lot :D


P.S. I never knew that Sheldon said that Ubuntu was his favorite Linux-based OS! That's very interesting! [/SIZE]

---

### Post by chili555 on 2011-12-08
I fear you have not typed the pipe symbol correctly. You might try:```
lspci -nn
```Post back only the lines relating to your Broadcom.> I never knew that Sheldon said that Ubuntu was his favorite Linux-based OS!Oh, yeah! You can see and hear it on YouTube. He was probably influenced by the excellent forum support, don't you think?

---

### Post by MugOfUbuntu on 2012-01-20
Okay, the terminal says Ubuntu knows about the wireless hardware, and that the Soft and Hard aren't blocked.

---

### Post by chili555 on 2012-01-20
Can you temporarily get a wired ethernet connection and do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After it is done, detach the ethernet cable, reboot and your wireless should be working.

---

### Post by MugOfUbuntu on 2012-01-20
Thank you so much! The wireless is working now!! Thanks a million!!!:KS:D

---

### Post by emiliomore on 2012-11-03
I have the same problem, but when i run  the install b43..
I recive the folloowing message, that I must insert the Instalation CD, but my computer do not have one, I install ubuntu from the Harddisk, 2nd partition


[IMG]http://ubuntuforums.org/home/emilio/ImÃ¡genes/Captura de pantalla de 2012-11-03 09:57:11.png[/IMG]

---

### Post by Hadaka on 2012-11-03
Hi, this thread is SOLVED and a year old, please start a new thread
to get your b43 driver correctly loaded.

thanks

---

