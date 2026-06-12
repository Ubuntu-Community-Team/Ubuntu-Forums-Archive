---
title: "Dual Screen"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by Feren6 on 2006-07-04
I installed the nvidia drivers and I got the resolution to what i want (same with refresh rate ) by following a previous guide. What should I do to enable my other monitor? Its in 'standby' mode atm and is not being used in linux, but works fine with windows. What should I do?

Specs:

GeForce 6600 GT 128 MB AGP 8x

---

### Post by lurchi on 2006-07-04
Read the Nvidia-Readme delivered with the drivers. The options Twinview and MetaModes should help you.

---

### Post by RawMustard on 2006-07-04
Search the forums, because this has been discussed many, many times.
If you still have problems, post back here!

---

### Post by sfink01 on 2006-07-06
Feren6,

Follow this HowTo [http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-breezy.html)

and

Read and respond to this thread 

[http://www.ubuntuforums.org/showthread.php?t=85769](http://www.ubuntuforums.org/showthread.php?t=85769)

for help.

Best,

Steve

---

### Post by orb9220 on 2006-07-06
This was my post and reply and it worked like a champ

for FX-5200 dual monitors.

[http://www.ubuntuforums.org/showthread.php?p=1199911#post1199911](http://www.ubuntuforums.org/showthread.php?p=1199911#post1199911)

Used the xorg.conf starting at device nividia Highlight all the way down and copy
Then open xorg.conf highligt select at beginning of nvidia entry all to the end.

Then right click paste what was copied from forum xorg.conf into yours.
Save and reboot.

Remember to back up your current xorg.conf file before editing it. If it messes up and you can't load Ubuntu normally use the GRUB menu to boot into recovery mode, then copy the backup file back over the current xorg.conf.

Now I have dual monitor which for now it cant do seperate monitors.
Twinview will create one monitor out of the 2 for a 2560x1024 display.

Hope this helps

---

