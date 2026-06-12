---
title: "Unable to run xorg"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by HolyAvenger on 2008-04-20
Hello,

First of all, thank you for the time any of you provide in helping me. I'm a complete newbie here and I've been doing my best not to actually require to create a new thread, so I hope you understand that, although repetitive in theme, I'm creating this thread as a last option because I've googled over the whole weekend and found no solution.

That being said, I'll try to explain my problem.

I installed ubuntu 8.04 x86.

After many tries, I found an effective way to install my nvidia drivers.

```


sudo apt-get install build-essential

CTRL + ALT + F1 to close the X manager

login with the same username/password you would normally do but in a terminal.

sudo /etc/init.d/gdm stop

cd /home/username/Desktop
sudo sh ./nvidia_drivers_name
sudo /etc/init.d/gdm start


```

After that, everything went pretty smooth. I was even able to enable desktop effects like the stretchy windows and the cube desktop thing.

My problem came up when I tried to change resolutions from 1024x768 (the max it would allow me to) to 1280x1024.

I have a 19" Samsung 950b monitor which DOES support 1280x1024 resolutions (I'm in windows right now and using that resolution, as a matter of fact).

I tried to modify the /etc/X11/xorg.conf file.

In the "Display" part to add "1280x1024" as I found in a google search. And tried restarting gdm.
At first, I thought I was succesfull, considering my login screen was, indeed, at a 1280x1024 resolution. But, after a little while, nothing else was loaded. No icons, nothing.

I tried closing x again with CTRL-ALT-F1 and restarting GDM, and it was then when I got this message:

"[...]API mismatch. The NVIDIA driver component has version 169.12 but NVIDIA kernel module's version does not match[...]" (I'm attaching the whole xorg.0.log at the end of this thread)

Also, before editing the xconf file I ran a
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` just in case something went wrong. Strangely enough, when I tried to "undo" what I did by running 
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` I got not result, the error was still the same.

I found myself stuck at this point for a long, looong while by now so I'm posting here, hoping to find someone more knowledgeable than me (which mustn't require that much, anyways =p) who could help me in sheding some light into this issue.

Also, most of the actions I took up to this point were by following guides I found on google (I tried to keep them the most "Ubuntu centered" as possible, but at times I might have had to use guides not specifically intended for it) and raw trial and error. I don't know if this helps, but I doubt any information I could provide is useless.

If you need me to provide more information, just ask. I don't have that much of an idea of what you might need in this case to try to follow an error.


Thanks again to everyone for their help, time and comprehension.

Log:

[http://holyavenger.no-ip.org/Error%20log.txt/](http://holyavenger.no-ip.org/Error%20log.txt/)
[http://rapidshare.com/files/109133986/Error_log.txt.html](http://rapidshare.com/files/109133986/Error_log.txt.html)
[http://www.megaupload.com/?d=1YSBGS6X](http://www.megaupload.com/?d=1YSBGS6X)
[http://www.mediafire.com/?96lnbtyjdg1](http://www.mediafire.com/?96lnbtyjdg1)

**_I tried to attach it, but it's 21.1kb, 1kb above what it's allowed. Sorry.**_

---

### Post by sdennie on 2008-04-20
If you've manually installed the nvidia drivers into a stock Ubuntu kernel, on reboot, it's likely to clobber your custom built module with the default Ubuntu module (which may be the cause of the mismatch).  You can remove various packages and reinstall the nvidia driver to fix that problem but, it's probably easier to use [envy]("http://albertomilone.com/nvidia_scripts1.html") and let that setup the drivers for you.

---

### Post by HolyAvenger on 2008-04-21
Hey, thanks for the reply.

Ok, I was trying to do what you told me. I even took note of the name, apt-get command to install it, etc, etc. I rebooted my computer (I was at WinVISTA at the time) and when Ubuntu boots ... voila! It fixed all by itself =o

It even offered me the 1280 resolution (although at a 53Mhz refresh rate, which is pretty low). I didn't have any sound though, but it also fixed itself when I rebooted again.

I swear I did try rebooting before I posted this here. =p

---

