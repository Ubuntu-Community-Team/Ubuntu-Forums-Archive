---
title: "9600 Issues"
date: 2008-05-22
forum: Multimedia Software
---

### Post by Deiz on 2008-05-22
I've tried several methods so far - Envy, and the drivers directly from Nvidia using guides such as [this]("http://www.adamspotton.com/node/1").

Using the method in the linked article, I get dumped to low graphics mode after restarting GDM.

The other issue is that my fan speed's locked at 100%, but I imagine it will become adaptive once the driver's running.

Starting to wish I'd replaced my dead 8800 GTS 320 with a card of similar vintage.

---

### Post by Xiong Chiamiov on 2008-05-22
Are you following step number 7 in his guide?  If you are, you might try not, and vice versa.  Instead of restarting gdm directly, what if you do
```

startx

```

---

### Post by Deiz on 2008-05-27
Tried that, no dice.

[This]("http://ubuntuforums.org/showthread.php?t=800925") guide ended up getting my drivers working. Then I absent-mindedly rebooted after the kernel update and I'm down for the count again.

Tried the exact same steps again (Retraced my steps based on terminal input, even.) to no avail.

I've deleted /etc/init.d/nvidia-glx, /etc/init.d/nvidia-kernel and /lib/linux-restricted-modules/.nvidia_new_installed, added DISABLED_MODULES="nv,nvidia-new" to /etc/default/linux-restricted-modules-common, exactly as the various guides tell me to do.

My exact steps when installing the driver:
/etc/init.d/gdm stop
dpkg-reconfigure xserver-xorg (To get a clean xorg.conf to work with.)
sh /home/swh/Desktop/NVIDIA-Linux-x86_64-173.08-pkg2.run 
nano /etc/X11/xorg.conf (Adding Option "AddARGBVisuals" "True" and Option "AddARGBGLXVisuals" "True".)
/etc/init.d/gdm start

This causes the terminal to go blank, restore the text for 2-3 seconds three times, and then dump me into low graphics mode.

Update: Huh. I guess repeating the whole process was undoing my progress, somehow. For kicks, I killed GDM and ran nvidia-xconfig, then started GDM back up. Nvidia drivers working just fine!

---

### Post by briandu on 2008-05-28
I had same problem as you describe on previous occasion. 9600GT

So follow this exactly [http://ubuntuforums.org/showthread.php?p=5064980#post5064980](http://ubuntuforums.org/showthread.php?p=5064980#post5064980) msg #430 and prob should resolve.

Cheers.

---

