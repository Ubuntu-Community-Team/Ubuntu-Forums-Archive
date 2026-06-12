---
title: "Missing mouse pointer after installing NVidia driver"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by ProudGeekDad on 2007-06-13
Hello all.  I've just installed Ubuntu on my brand new Compaq computer.  I've just updated the computer to use the NVidia driver, and after restarting xwindows, my mouse pointer is missing.  I can still move the mouse around (I see hover effects and can grab scroll bars), but I just can't see the pointer!  I've found an option under mouse settings to "highlight the pointer" when I hit the Ctrl button, which helps make things more useable, but still a pain!

According to my updated /etc/X11/xorg.conf file, this computer has a nVidia Corporation C51 [GeForce 6150 LE] graphics card.  I have a backed up copy of xorg.conf, and the mouse settings are identical.

I'm sorry if this has already been posted, but its difficult to search the forums without a mouse pointer!

(In case it helps anyone else out, my original problem with this card was that I could not get it larger than 800x600, which isn't even big enough to run the Ubuntu Install program correctly.  I remedied this enabling "desktop effects" from the "System | Preferences" menu, which downloaded the NVidia driver and rebuilt xorg.conf.)

Thanks in advance for your help!

---

### Post by Pstevens on 2007-07-04
Well, I have this one too.  Let me add some info and see if we can figure this out.

For me the problem is intermittent - the Mouse pointer is *sometimes* invisible.  Logging out (not, restarting - logging out) triggers the disappearance of the pointer.  I haven't found a way to make it reappear, unfortunately (but thanks for the tip about the 'highlight mouse position' setting).

I also have an nVidia graphics card: nVidia Corporation C51G [GeForce 6100], 
according to xorg.conf

My machine is Lenovo, not Compaq; my mouse is Logitech.
I have made sure Ubuntu is up-to-date.

---

### Post by david_2001 on 2007-07-04
A little Googling around suggests that there is a bug in some versions of the nvidia driver that can cause this problem and the suggested solution is to add
```
Option "HWCursor" "off"
```
to the "Device" section of xorg.conf.

---

### Post by Pstevens on 2007-07-06
Thanks, david_2001.  This newbie appreciates your help.
Further rummaging turned up this guide
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)
which also recommends adding a line
Option "SWcursor" "True"
after the HWCursor line.

---

### Post by ProudGeekDad on 2007-07-26
Thank you both, this works great!!!  :)

I've been in the process of moving so I haven't had much time to get on the computer and figure this out.  I definitely appreciate your help on this!

---

