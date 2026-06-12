---
title: "Resolution...again...srry"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by trunks14 on 2007-02-24
Greetings to all, well, firstly i want to say, im finally making the movement from windows to linux, i chose ubuntu cuz ive heard great stuff bout it and cuz the screenshots talk by theirselves, anyway, i first wanted to test it, so i put the CD into the tray, boots etc everything was magical i could do anything i did in windows and not only that...i didint even had to install anything hehe, a word document, ready to be open, firefox, gimp etc.

Well the problem is a well known one, the resolution, of course i searched, i found a few things but since im running a Live CD i dont know if that could affect, i did this:

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
...
At this point i thought i had done it, it recognized my ATI Radeon 9550, my StudioWorks monitor etc, then i started it again
sudo /etc/init.d/gdm start

but nothing seemed to change, i went to preferences>resoluction and nothing, still only 640 by 480.

Sorry, i have made you read a lot of useless information, so the final question is, in order to this to take effect Do i need to actually install ubuntu or something can be done in a Live boot?

---

### Post by skug on 2007-02-24
Firstly I would really recommend installing Ubuntu to the hard drive, but you could try editing the /etc/X11/xorg.conf:

in Section "Device" change the Driver from "ati" to "radeon" and add the line:

Option      "MonitorLayout" "LVDS,AUTO"

in the device section.

It should look something like this:



Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon (Yourmodelhere)"
        Driver      "fglrx"
        Option      "MonitorLayout" "LVDS,AUTO"
EndSection

and then change the resolutions tin Section "Screen" to fit your monitor:

But I strongly recommend installing Ubuntu to the harddisk  for optimal performance and the real Ubuntu feeling :P

---

