---
title: "GeForce GT 340 Garbling"
date: 2012-03-03
forum: Multimedia Software
---

### Post by jackhe22 on 2012-03-03
Hello,

This is my second post about this problem on the forums, the first being completely unanswered after 3 weeks. Recently upon trying Ubuntu 11.10 on my Acer Predator G5900, with a GT 340 PCI-E card, Ubuntu simply boots into a garbled display. This shows blocks of solid colour across the screen as well as sections of the previously loaded session which as been addressed from VRAM. Possible solutions anyone?

Jack

---

### Post by BicyclerBoy on 2012-03-05
Is the display garbled at boot or greeter/login or X desktop screens ?
Are you dual booting with earlier 10.04 ? and the PC works okay ?
Were you using the video driver from jockey tool "additional drivers"?

nVidia 275.43 or later is probably required.
Are you sure the GPU is not a GT440, not that it makes much difference..

---

### Post by jackhe22 on 2012-03-06
Okay so basically, the screen would garble at login, but instead now it just black screens. Monitor 1 reports it is outputting 1280x720, which is correct, although Monitor 2 reports 640x480. After waiting 10 minutes it is still black, so I don't even know how to go about getting the nVidia driver. A quick note, this is through Wubi. Unfortunately I don't consider Ubuntu a serious operating system since GNOME was shelved.

---

### Post by BicyclerBoy on 2012-03-06
Unity is just a GUI desktop manager..in windows you have no choice & no choice in desktop effects manager.

You can install/use a number of desktop/effects managers..
gnome-fallback can be installed & then picked at login ..basically same as old gnome 2.

When you are stuck at black screen you can console login..
<ctrl>+<alt>+<F1>
Then view or redirect into text file some debug info
dmesg > kernellog.txt
cat /var/log/Xorg.0.log > dumpXorglog.txt

Access these files later from windows..

---

### Post by jackhe22 on 2012-03-07
Not quite sure what you want me to do there, but I did Ctrl+Alt+F1 when it garbles/black screens and I saw something quite far up that something like "GPU lockup resorting to" something mode. I really should have written it down >.<

---

### Post by BicyclerBoy on 2012-03-07
That sounds quite terminal..

Can you try a live CD DVD USB stick boot to see if the machine works okay?
Wubi may be the problem.

---

### Post by jackhe22 on 2012-03-10
I have today tried a USB stick with the system to boot, with an identical issue. Maybe this is down to the fact I am on the 64-bit version of Ubuntu? 
Thanks,
Jack

---

### Post by BicyclerBoy on 2012-03-10
I have been using 64bit ubuntu since 8.04 with no issue.

A possible cause is the default nouveau driver for nVidia h/w.

You need to access the Xorg or kernel log files to debug..

If you can console login (from live CD/DVD/USB).. then try
sudo apt-get install nvidia-current
sudo service gdm start

If you can not use console then it is possible to stop the nouveau driver from grub by adding:
rdblacklist=nouveau

---

### Post by jackhe22 on 2012-03-11
Lol surprised I didn't try the sudo-apt-get earlier, but I don't think it will work thanks to me being on wireless connection. Will try the grub hack later, thanks

Jack

---

### Post by jackhe22 on 2012-03-17
Did try both, still garbling. The blacklist option in Grub seems ignored, despite making sure it had taken it in. During the boot sequence noveau can still be seen booting. Sudo-apt-get is useless with terminal login, due to the fact that I previously mentioned, I am on wi-fi, not LAN.

---

### Post by BicyclerBoy on 2012-03-17
Find a $5 cable & plug straight into the router/modem/WAP..

---

### Post by jackhe22 on 2012-03-19
This isn't possible, the router is downstairs, and there are no phone lines up here. I guess a large LAN extension is a feasible option but I wont be paying for one. Meh

---

### Post by BicyclerBoy on 2012-03-20
CAT6e is only 30cents/metre
punch-down tool is $20

---

### Post by jackhe22 on 2012-05-18
A LAN cable to the router is not possible.

---

