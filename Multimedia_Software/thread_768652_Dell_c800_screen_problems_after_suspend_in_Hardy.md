---
title: "Dell c800 screen problems after suspend in Hardy"
date: 2008-04-26
forum: Multimedia Software
---

### Post by dstubb on 2008-04-26
Just upgraded my Dell c800 ati rage 128 to hardy - no problems except when I wake it from "suspend" the video is garbled.  Hitting F7 does nothing.  I am forced to reboot.

I never saw this in previous iterations of ubuntu.

---

### Post by archim on 2008-04-27
Ubuntu 8.04 on Inspiron 1501. The same problem. After suspend I can see a lot of fast moving color shapes, something such as squares and lines...

Also, I can see the normal screen about 1/5 second while regulating brightness. Brightness is regulated by own scripts such as this

[FONT="Courier New"]```

archim@archim-laptop:~$ cat /etc/acpi/video_brightnessdown.sh 
#!/bin/bash
current=`cat /proc/acpi/video/VGA/LCD/brightness | grep current | cut -f 2 -d :`
[ $current -eq 0 ] && current=100; next=$current
[ $current -eq 25  ] && next=12; [ $current -eq 37  ] && next=25
[ $current -eq 50  ] && next=37; [ $current -eq 62  ] && next=50
[ $current -eq 75  ] && next=62; [ $current -eq 87  ] && next=75
[ $current -eq 100 ] && next=87
[ ! $current -eq $next ] && echo -n $next > /proc/acpi/video/VGA/LCD/brightness

```[/FONT]

The only one way not to lost data is to hibernate and return back.

I tried to change settings in /etc/default/acpi-support, such as disabling POST_VIDEO. No effect at all... :(

In console (Alt_Ctrl+Fx) text is zoomed and randomly jumps... :confused:

---

