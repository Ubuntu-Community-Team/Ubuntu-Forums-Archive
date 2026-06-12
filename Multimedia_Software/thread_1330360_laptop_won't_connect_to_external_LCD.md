---
title: "laptop won't connect to external LCD"
date: 2009-11-18
forum: Multimedia Software
---

### Post by Gatorade on 2009-11-18
I've got a Dell D620 laptop, running Ubuntu 9.04 

I wanted to test a different LCD screen because I'm having issues with the one in the laptop(looks kinda dark) , but I can't get it to pick up the other monitor.

I'm running a dual boot system with windows 7 being the other OS. When I load win 7 , it picks up the other monitor no problem.

So, how do I get Ubuntu to see this other monitor?

---

### Post by Gatorade on 2009-11-18
ok, this is the advice I was given to get it to work.
can anyone confirm this before I actually do it?

I just wanted to make sure because the guy had a D630 instead of 620

 

sudo gedit /etc/X11/xorg.conf
Find the entry: Section “Device”
Identifier “Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller”
Driver “i810&#8243;
BusID “PCI:0:2:0&#8243;
EndSection

Insert the code:

Option “MonitorLayout” “CRT,LFP”
Option “Clone” “true”
Option “DevicePresence” “true
before the EndSection

Save file and exit.

Press “Ctrl + Alt + Backspace” to restart Xorg.conf

Done! The VGA will output to a external source (monitor, projector, etc)

---

### Post by bluelamp999 on 2009-11-18
Have you played around with Display Preferences (System>Preferences>Display)? 

I've a Latitude D810 and I easily set up dual monitors with the above...

---

### Post by Gatorade on 2009-11-18
hi, 

thanks for the suggestion , but I tried that and it didn't work.

---

### Post by NoBugs! on 2009-11-21
I also noticed that the Display Preferences in 9.04 won't detect a projector. However, using xrandr or a program that directly uses xrandr does work.

---

