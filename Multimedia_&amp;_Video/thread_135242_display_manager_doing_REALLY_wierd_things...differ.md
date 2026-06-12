---
title: "display manager doing REALLY wierd things...different distros &amp; different partitions!"
date: 2006-02-23
forum: Multimedia &amp; Video
---

### Post by stewb on 2006-02-23
Ok, I know there's a million threads about problems about display managers not loading, but I've yet to find a solution from any of them. I try not to post questions about common issues, but I'm afraid I'll have an aneurysm soon if I don't figure this out!

Hardware: dell inspiron 600m laptop ....raedon lcd display with ati driver

Problem: 

After installing Ubuntu, the system seems to boot properly until it attempts to load the display manager. When it tries to load the display manager all I get is a blank black screen without a cursor or prompt. I've tried booting with init 3 and then loading it, but it just does the same thing....black screen. I've tried loading kdm, gdm & xdm! None have worked.

But here's the ***really*** wierd thing:

Before I installed Ubuntu, I had dual boot with Fedora (kernels 2.6.11 & 2.6.15) and Debian (kernels 2.6.8 and 2.6.15). I'd never had problems booting any of them until a few days ago... I installed a 3rd kernel in fedora (was trying to build one that was really efficient). That kernel booted the display manager and everything fine, but caused kde to do something funky. So i tried rebooting Fedora with the 2.6.15 kernel and got the black screen deal when it went to load gdm. I rebooted with the 2.6.11 kernel and it did the same thing. Sounds like an X11 config problem right? I didn't feel like dealing with it then so I booted Debian......I'd boot debian with the 2.6.15 kernel, it loaded fine, but when trying to boot with the 2.6.8 kernel it did the black screen deal like it did with fedora!! Yesterday I decided to just format my Fedora partition and reinstall it.....i did and it installed completely fine, but while booting it gave me the blank black screen when it tried loading the display manager again!!! *(the reason i wanted fedora back on was that i was that i couldn't get my internet to work with debian, but could in fedora)* ....OK, so then I decided to install ubuntu over my debian partition (assuming it'd be easier to get my internet working with that than with debian). It installed fine, rebooted, did the final config thing it gives you, but then when it went to load the display manager It gave me the black screen again!! I haven't changed any hardware. I have no idea what could cause this kind of thing....in three different distros on 3 different partitions?!

I did find this in my Ubuntu Xorg.0.log :

```
/usr/share/X11/fonts/cryllic  doesn't exist
deleted from font path
/usr/share/X11/fonts/CID  doesn't exist
deleted from font path

fonts.dir not found (or invalid) in /var/lib/defoma/x-ttcidfont-conf
deleted from font path

run mkfontdir on:
/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID

/dev/apm_bios ..no such device
```

I'm not sure how the mkfontdir script works or if it'll solve my problem....:-k 

Any help please!!! Thanks in advance!!!

---

### Post by stewb on 2006-02-24
anyone??

---

### Post by tseliot on 2006-02-25
Turn on your computer and keep pressing ESC until you get to the GRUB menu.
You will see a list of kernels: select Recovery mode
It will boot without the Graphical interface.
type this:
sudo nano /etc/X11/xorg.conf

scroll down the text with your keyboard and get to the "Section Device".

Set the driver to "vesa" instead of "ati" (which you will find beside the word "Driver"

CTRL+O to save (yes, overwrite it)
CTRL+X to exit

then type:
reboot

Boot as usual and you shouldn't have the black screen again.

---

