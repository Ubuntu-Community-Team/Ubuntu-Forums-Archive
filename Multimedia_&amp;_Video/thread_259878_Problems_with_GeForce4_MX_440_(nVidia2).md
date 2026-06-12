---
title: "Problems with GeForce4 MX 440 (nVidia2)"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by LetsLinux on 2006-09-18
Hi,

I'm a noob at Linux and I've recently installed it because I got tired of my Win XP craching down. I simply needed an alternative solution in case my XP didn't work. Now it doesn't work again and I decided to spend a little time getting around Linux. :-)

I have problems with my screen resolution - and I don't know it it's Ubunto that doesn't supprt my VGA driver - or that it does, but I don't know how to set it up. Obviously (to me) it's the latter and I therefore ask for some help here.

The output from **lspci -n | grep 0300** is: 
[CENTER]0000:02:00.0 0300: 10de:0171 (rev a3)[/CENTER]

And the output from **lspci | grep VGA** is:
[center]0000:02:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440 ] (rev a3)[/center]

The problem is that the bootscreen is fuzzy looking and has horizotal stripes across the screen. Also when running Ubuntu with resulution 1280x1024 @ 75Mhz is fuzzy as well and has the horizontal stripes across the screen as well. However with a lover resolution 1024x768 @ 75Mhz the screen is just fuzzy. 

Is there something I can do to make it crisp and clear (like in Win XP) and if so - please enlighten me! :p 

Thanks in advance - and Ubunto is really userfriendly!

Best Regards
Jonas

---

### Post by croak77 on 2006-09-18
Are you using the nv or nvidia driver?

---

### Post by LetsLinux on 2006-09-18
Hi,

And thanks for the quick reply.

Well I'm not quite sure which driver I'm using. I simply just installed Ubuntu and I'm using the driver Ubuntu set up for me.

Is there a way I can check it?

Jonas

---

### Post by croak77 on 2006-09-18
Then you are most likely using the free 'nv' driver. The 'nvidia' driver is the one made by Nvidia. It's not included by default on the cd. The 'nv' driver is good for some people but your problem might be solved with the 'nvidia' driver. To install, follow these directions.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by LetsLinux on 2006-09-18
Whoa... Nice!

Thanks a whole bunch I'll sure try it out. I'll let you know if it works or doesn't...

Again, thank you for the help sofar!

Jonas

---

### Post by LetsLinux on 2006-09-18
> **croak77 said:**
> Then you are most likely using the free 'nv' driver. The 'nvidia' driver is the one made by Nvidia. It's not included by default on the cd. The 'nv' driver is good for some people but your problem might be solved with the 'nvidia' driver. To install, follow these directions.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

It worked, thank you very much. It's clear and crisp now. However I had to go through the troubleshooting documentation - but it was easy peasy! :)

You don't my any change know why I can't mount one of my harddrives? The error I get is:
[INDENT][FONT="Courier New"]error: device /dev/hda1 is not removable
error: could not execute pmount[/FONT][/INDENT]

Jonas

---

### Post by LetsLinux on 2006-09-19
Ohh. Nevermind - got the hang of it by checking out many a website. Can't remember the exact location though - but it worked. I think it was something with the NTFS-3g thing! :-)

---

