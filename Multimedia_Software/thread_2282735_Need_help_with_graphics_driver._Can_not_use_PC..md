---
title: "Need help with graphics driver. Can not use PC."
date: 2015-06-16
forum: Multimedia Software
---

### Post by dtree46 on 2015-06-16
Installed fglrt (spelling ?) driver via synaptic, sign in will no longer accept password. Screen is not what it was. Can not use PC.
Using laptop now.
Any help appreciated.

dlw

---

### Post by papibe on 2015-06-16
Hi dtree46.

Option 1:
[LIST]
[*]Boot into recovery mode and then fail safe ([here]("https://www.youtube.com/watch?v=HYiTJtYmmzg&feature=youtu.be&t=35s")'s how).
[*]Open synaptic and uninstall/purge fglrx.
[*]Reboot.
[*]
[/LIST]
Option 2:
[LIST]
[*]Boot into recovery mode.
[*]Drop to root prompt (as described in this [video]("https://www.youtube.com/watch?v=c7TTD_UUUjQ") to reset your password).
[*]Then run this to remove the package:```
apt-get purge fglrx
```
[*]And this to reboot:```
reboot
```
[/LIST]
Hope it helps. Let us know how it goes.
Regards

---

### Post by ajgreeny on 2015-06-16
So that we are able to help you more, tell us what hardware you have, particularly the graphics card.

If you are not sure use terminal command **sudo lshw -c display**

---

### Post by dtree46 on 2015-06-16
Thanks for replying.
When booting up, I never see grub.
I do not see the Ubuntu logo with the white dots below it.
It goes directly to a log in screen waiting for my password.
It will not accept my password.
It just loops back to the same log in screen.

AMD Radeon Xpress: that's all I remember. I can not log in to do anything.

---

### Post by papibe on 2015-06-16
> **dtree46 said:**
> When booting up, I never see grub.
Check the videos again. In order for the menu tu appear, you may need to either:
[LIST]
[*]keep the shift key pressed while booting, or
[*]keep pressing it and releasing it (click, click, click)
[/LIST]
Let us know if that works.
Regards.

---

### Post by dtree46 on 2015-06-16
Neither clicking the shift key or holding it down while booting works.

---

### Post by dtree46 on 2015-06-16
OK, clicking finally worked.
However, after walking through the video... it does the same thing.
Will keep trying.
I'll be back to keep your informed.

---

### Post by dtree46 on 2015-06-16
In safe mode, after failsafex, then 'yes', I get an error, stand by while the display restarts.
Nothing happens. I press 'ok' then its back to the Recovery Menu.
If I press 'ok'. it reboots.
As it reboots, I get an error: 'the system is running in low graphics mode'
I press 'ok'.
'Would you like to run in low graphics mode for just one session." click 'ok'.
The screen turns black.... and, that's it. Nothing happens.

The PC is on.

---

### Post by papibe on 2015-06-16
Bummer :(

Did you try option 2?

Regards.

---

### Post by QIII on 2015-06-16
Option 2 is your only choice.  It has been about 7 years since AMD/ATI withdrew Linux support for that series of graphics adapters.  If you remove the fglrx driver you will revert to the open source Radeon driver, which is the only one that will work.

---

### Post by dtree46 on 2015-06-16
In safe mode, after failsafex, then 'yes', I get an error, stand by while the display restarts.
Nothing happens. I press 'ok' then its back to the Recovery Menu.
If I press 'ok'. it reboots.
As it reboots, I get an error: 'the system is running in low graphics mode'
I press 'ok'.
'Would you like to run in low graphics mode for just one session." click 'ok'.
The screen turns black.... and, that's it. Nothing happens.

The PC is on.

---

### Post by dtree46 on 2015-06-16
OK... kept trying. It finally boots up.
Doesn't ask for password, but, that is alright.
Now, there is the problem that I originally tried to solve.
The photo on the home screen is too wide. Height is ok.
Faces are distorted, too wide.
What graphics driver to I need?
Ubuntu 14.04LTS.

---

### Post by QIII on 2015-06-16
Just to be clear:  have you removed the fglrx driver?

---

### Post by dtree46 on 2015-06-16
All is well, except photos are distorted, too wide.

Yes, fglrx driver is purged.

---

### Post by QIII on 2015-06-16
OK.  Let's be sure you don't have an xorg.conf conflicting with the monitor's EDID.

See if you have a file "/etc/X11/xorg.conf".  Remember that Linux is case-sensitive.

If you do, let's rename it first rather than using the more dangerous rm (remove) command right now.

```
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
```

Reboot.

---

### Post by dtree46 on 2015-06-17
There is not /etc/X11/xorg.conf. There is an xorg.conf.failsafe.
Also, photo is no longer distorted and speed is back.

However, boot up problem still exist.
Turn PC on.
Boots up to the maroon page but no grub menu then goes black and hangs.
Turn PC off.
Boots up normal on second try.

---

### Post by oldrocker99 on 2015-06-17
> **QIII said:**
> Option 2 is your only choice.  It has been about 7 years since AMD/ATI withdrew Linux support for that series of graphics adapters.  If you remove the fglrx driver you will revert to the open source Radeon driver, which is the only one that will work.

He is quite right; six years ago I got a Toshiba laptop with an ATI chip which was declared "legacy" a month after I purchased it. I used the "radeon" driver, which started out the only option and has steadily gotten better (with, to give credit where credit is due, with significant help from ATI); and, after some hard and laborious coding, works very, very well indeed. There are serious gamers who swear by it, and never use fglrx.

---

### Post by Yellow Pasque on 2015-06-17
Post the text of the /var/log/Xorg.0.log file. Use code /code tags because it's a lot of text.

---

### Post by dtree46 on 2015-06-17
You are correct... it is huge.
Do not know how to use code tags.

---

### Post by papibe on 2015-06-18
Paste the file here instead: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Then post a link to the pasted/uploaded file.

Regards.

---

### Post by dtree46 on 2015-06-18
> **papibe said:**
> Paste the file here instead: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Then post a link to the pasted/uploaded file.

Regards.

Pasted as: 
[h=1]Paste from dlw at Thu, 18 Jun 2015 13:16:06 +0000[/h]

---

### Post by papibe on 2015-06-18
> **dtree46 said:**
> Pasted as: [h=1]Paste from dlw at Thu, 18 Jun 2015 13:16:06 +0000[/h]
You need to copy the url of the file just pasted, and then paste it back here.

Regards.

---

### Post by dtree46 on 2015-06-18
[http://paste.ubuntu.com/11735772/](http://paste.ubuntu.com/11735772/)

---

### Post by Yellow Pasque on 2015-06-18
Your log looks fine in terms of resolution (assuming your monitor is 1680x1050) and the driver used.
> The photo on the home screen is too wide. Height is ok. Faces are distorted, too wide.
Maybe it's just that the wallpaper image doesn't match your monitor's aspect ratio (16:10). If you use a wallpaper that was designed for another aspect ratio (like a common 16:9 ratio that 1920x1080 monitors use), then it's not going to look right if the desktop is set to stretch the image. You can either use a different wallpaper or change the desktop to center (not stretch) the image.

---

### Post by dtree46 on 2015-06-18
I posted this earlier.

There is no /etc/X11/xorg.conf. There is an xorg.conf.failsafe.
Also, photo is no longer distorted and speed is back.

However, boot up problem still exist.
Turn PC on.
Boots up to the maroon page but no grub menu then goes black and hangs.
Turn PC off.
Boots up normal on second try.

---

### Post by papibe on 2015-06-18
Thanks.

It looks like there's still something from fglrx:
```
[    39.134] (II) LoadModule: "fglrx"
[    39.134] (WW) Warning, couldn't open module fglrx
[    39.134] (II) UnloadModule: "fglrx"
[    39.134] (II) Unloading fglrx
[    39.134] (EE) Failed to load module "fglrx" (module does not exist, 0)
```
Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

dpkg -l | grep -i fglrx
```
Regards.

---

### Post by dtree46 on 2015-06-18
dlw@HP:~$ lspci -nnk | grep -iA2 vga
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS482/RS485 [Radeon Xpress 1100/1150] [1002:5974]
    Subsystem: Hewlett-Packard Company DC5750 Microtower [103c:280a]
    Kernel driver in use: radeon
dlw@HP:~$

dlw@HP:~$ dpkg -l | grep -i fglrx
rc  fglrx-core                                            2:15.200-0ubuntu0.3                                 i386         Minimal video driver for the AMD graphics accelerators
dlw@HP:~$

---

### Post by Yellow Pasque on 2015-06-18
papibe, the snippet of log you posted does not indicate anything is left behind. I think it's standard for Ubuntu's Xserver to look for the proprietary driver first. The Xorg log looks fine to me.

@dtree: After a failed boot, reboot and see if you can give pastebin the /var/log/Xorg.0.log.**old** file. That should be the log for the previous (failed) boot.

---

