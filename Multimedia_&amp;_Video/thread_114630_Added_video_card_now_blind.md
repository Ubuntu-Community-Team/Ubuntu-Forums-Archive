---
title: "Added video card now blind"
date: 2006-01-09
forum: Multimedia &amp; Video
---

### Post by doug400 on 2006-01-09
I added a video card to my PC (nVidia TNT2 M64 32Meg) was running off of motherboard video port.  Now I get errors and no desktop.  I'm assuming I need to disable the motherboard video.  CompaQ told me how to do this in Windows Device Manager but they don't support Linux.

I'm on Ubuntu 5.10 just did a fresh reinstall.  I get the basic startup text but when the GUI should display I only have a cursor.

I do not have dual boot ONLY Ubuntu.

---

### Post by doug400 on 2006-01-10
The error looks something like this.
[4294842.nnnnnn  hub 1-1:1.0:  Connect - debounce failed, port 3 disabled

I tryied x-server config for video setup but got no where.

If this isn't fixed in a few days I'll just reformat and load Windows to get my PC running again.

---

### Post by mmcmonster on 2006-01-10
I'm fairly new myself, so I'm not sure 100% if this is right, but it should work:

1. Log onto the terminal with your first username.  If you don't have a login screen when you boot, after the boot process is complete (the hard drive is not active), hit ctrl-alt-F1.

2. Enter the following commands.  (I'm not sure if the first two are necessary.  Maybe you can just try the third one and see if that works?)  The first 2 will download the nvidia drivers.  The third will reconfigure X to use the video card.

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure xserver-xorg

3. reboot the computer. (type "sudo reboot" at the command prompt)

---

### Post by doug400 on 2006-01-10
Great, sounds like this should help.  But when I tried it I had a very difficult time entering the xserver config screen data.  I keep getting error messages every couple of seconds that distort the screens.

Any way to supress them?

---

### Post by mo_x on 2006-01-10
Can you disable the onboard video in the bios?

---

### Post by doug400 on 2006-01-10
When I asked CompaQ about the BIOS setting they didn't respond.  They told me to come up in safemode and use Device Manager (Windows).   

What I might do is pull the video card and go back to the motherboard port.  Then try doing the xserver config for the nVidia (now that I have the driver).  This should allow me to type without all the errors scrambeling the screens.

---

### Post by mmcmonster on 2006-01-10
Try that and let us know what happens, please. ;-)

I have my doubts, though, since (I would think) the video card has to be active for the X windows configuration to go properly. :-(

---

### Post by doug400 on 2006-02-06
Well I got back to this.  Pulled the video card and went back to the motherboard video port.  Still got my errors, so I figured I would just reset and do a full install of Ubuntu 5.10 again.  Well the first pass went OK but just after the point where it reboots the GUI did not get shown.  Instead I get a screen full of this error (it repeats about every second and the background becomes unusable.
error:  [nnnnnnn.nnnnnnn] Hub 1-1:1.0: connect-debounce failed, port 3 disabled.

It seems now the only thing I can try is to load Windows.

---

