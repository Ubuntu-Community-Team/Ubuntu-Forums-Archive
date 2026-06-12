---
title: "Switched to Nvidia from ATI lost GUI"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by tracer2027 on 2007-07-06
I removed an ATI card that wasn't working well with Ubuntu and installed Nvidia Geforce FX5500. Now all I get when the computer boots is an all text screen. The Nvidia card works in WIndows but I don't know how to get Ubuntu to work with it. I switched back to ATI for now. Any thoughts?

---

### Post by scxtt on 2007-07-06
what driver were you using (fglrx / ati / radeon) and did you change it before you shutdown the box to change the card?

you can change "Driver" in /etc/X11/xorg.conf to "nv" and you should get a GUI again ... 3d accel is another matter ...

sudo nano /etc/X11/xorg.conf
{find the driver section and change it to nv}
ctrl+o {to save}
ctrl+x {to exit}

edit: yeah, come to think of it - what's below may be easier for some :p {i'm old school ;)}

---

### Post by Nergar on 2007-07-06
try with ```
dpkg-reconfigure xorg
```

---

### Post by kvonb on 2007-07-06
If you are using Ubuntu 7.04 (Feisty) then do as any of the others suggested, then when back at the desktop, go to your System->Admin menu and select "Restricted drivers manager".

That will install the 3d accel for you :).

---

### Post by tracer2027 on 2007-07-07
I tried what scxtt suggested but no GUI. Worse yet, the ATI card wouldn't work either until i changed "nv" back to "flrgx". I don't know how or where to do what Nergar suggested. I'm a newbie to Linux so more help is better than assuming I know what you are talking about. Thanks.

---

### Post by scxtt on 2007-07-07
nv = drivers for nvidia card {use them when you're using an nvidia card}
fglrx = drivers for ATI card {use them when you're using an ATI card}

you can't expect to change hardware - esp. that drastic of a change - and have it work (even in windows) *out of the box* ... nv/fglrx aren't interchangeable at all ...

---

### Post by tracer2027 on 2007-07-07
Thanks for your reply scxtt. I made the change you suggested to xorg.conf but after rebooting it still had no GUI with the Nvidia card. I changed "nv" back to "flrgx" to get the ATI card working again. That change did get the ATI card working again, so at least I know I am changing the right parameter. I don't now why the change to "nv" doesn't work though. Is there anything else that should be changed? Where do I find information on this subject besides the forums? FYI, that "drastic change" booted up fine in WIndows XP on this dual boot computer. Plug-n-play isn't a bad thing, and it has come a long way from the early plug-n-pray days.

---

### Post by scxtt on 2007-07-07
i'm talking about changing cards, but not changing drivers - and the same DOES apply to windows - the Nvidia drivers aren't *magically* available in windows just how they aren't in linux - windows just uses a "generic" driver til you install them (a lot of Linux distros can detect your video card and will provide you w/ the nv driver) ... using the nvidia card, you should be able to use "vesa" (instead of nv or fglrx) ... maybe you don't have the nv driver on your box?

you could also install the "nvidia" driver from the CLI - but vesa should work ...

---

### Post by RomeReactor on 2007-07-07
Hi. Like **scxtt** said, you could try installing the **NV** driver before switching cards:
```
sudo apt-get install xserver-xorg-video-nv
```
then, shutdown, install the nVidia card on your PC, start your PC, and upon getting to the terminal:
```
sudo nano /etc/X11/xorg.conf
```
scroll down to **Section "Device"**, and on the **Driver** line, cahnge it to "nv", so it looks like this:
> Driver          "nv"
press CTRL+O to save, CTRL+X to close the text editor, and
```
start x
```
or reboot
```
sudo reboot
```
if that doesn't take you to your desktop after trying **start x** or rebooting, you can try reconfiguring your display:
```
sudo dpkg-reconfigure xserver-xorg
```
Try to answer the questions as best you can; that will probably give you your graphical desktop.

---

### Post by tseliot on 2007-07-07
Plug in your Nvidia card then boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```

Then you'll need to remove the ATI driver (fglrx):
```
sudo apt-get --purge remove xorg-driver-fglrx
```
```
sudo aptitude reinstall libgl1-mesa-glx libglu1-mesa  libgl1-mesa-dri
```

and finally:
```
sudo apt-get install nvidia-glx-new
```
```
sudo nvidia-xconfig
```

---

