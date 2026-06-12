---
title: "Replacing graphic card in Ubuntu 7.04"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by avatar21 on 2007-08-27
Dear Ubuntuians, 


I happily setup my Ubuntu Feisty on my Intel Celeron 2.26 machine, (on a Intel D865GBF board, ATI Radeon 5250 VGA, 1GB RAM, 200+GB SATA HDD).

Everything works fine, glad to have the upgraded version.

After using some time, my ATI card start to give me unstable hardware problems, hence I [COLOR="Red"]unplug the ATI card[/COLOR] ([COLOR="Red"]integrated VGA - "Intel Extreme Graphic" takes over[/COLOR]) and test on my dual boot WinXP ... things worked fine.

But the other day when I tried to check on my Ubuntu,** "gdm"** gave me an error message saying unable to find device ([COLOR="Red"]leaving me in the text mode[/COLOR]) and asking me to check on my **"/etc/X11/xorg.conf"** file.

I tried to reconfigure the file and accidentally messed up with my configuration file.

May I know how do I resolved this issue?
- thinking of booting up with live CD and try to copy the working **"/etc/X11/xorg.conf"** file to replace the corrupted ones in my installed Ubuntu


Will it work? I still able to login to recovery mode to do this ...

Need some better advice as well ...



Thanks and Regards,
:popcorn:Avatar Ng:popcorn:

---

### Post by tseliot on 2007-08-27
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
dpkg-reconfigure xserver-xorg
```

select the "i810" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vesa" or "vga" instead of "i810" and try again.

---

### Post by avatar21 on 2007-08-27
Dear tseliot,


LoL, fast reply.
Thanks for your answer, will tried up.

:) thanks again. :guitar:


Thanks and Regards,
:popcorn:Avatar Ng:popcorn:

---

