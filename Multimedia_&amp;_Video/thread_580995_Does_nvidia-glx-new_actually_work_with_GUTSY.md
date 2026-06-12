---
title: "Does nvidia-glx-new actually work with GUTSY"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Shlomir on 2007-10-19
It seems not. Every time I try to install it I get errors..Any workaround or guides in how to install properly?

---

### Post by FredB on 2007-10-19
It works. My computer is using it. Just use the restricted manager and that's all.

---

### Post by Xgkkp on 2007-10-19
After installing it I can no longer boot X (it just gives a blank screen), and I had to manually edit xorg.conf to go back to nv.

Any idea how to even begin debugging this?

---

### Post by Killy.the.seeker on 2007-10-19
The nvidia drivers never worked well in my new gutsy installation; first i installed them the old way, stopping gdm and "sh NVIDIA*"... then I tried the stock cd drivers and still no go. I guess some bad karma from the nvidia binary remained coz as I uninstalled it warned me of being in runlevel 1 and switching to runlevel 3 would be better, but I couldn't cause I got a blank screen.

So first let me state the exact error:
- When starting ubuntu normaly gdm doesn't start (tries 3 times) and you get a configuration dialog. No matter what you do and how much you wait, you get a blank screen and ctrl+alt+F[1-6] doesn't work; have to ctrl+alt+supr or hit the reset button.
- When starting in recover mode, nvidia-xconfig worked for me at first, I could bring up X by "/etc/init.d/gdm start", unfortunately the changes weren't saved and got blank screen in normal mode. Somehow this method stopped working. After that, I could bring up X no more so I had to go to windows for help (blerg).

What I did to solve this problem was "dpkg-reconfigure -phigh xserver-xorg" in recover mode, that way I could login with the nv driver. I fired up synaptic package manager and uninstalled linux restricted modules x86, nvidia-glx-new and all its dependencies. Reboot. Then installed nvidia-glx-new, restricted drivers with the packages it asked and reboot. Got 2 new entries in grub, 386 version instead of generic. I could log normally with the nv driver but there was no sound, I activated nvidia restricted drivers in the restricted driver manager and reboot.
Now everything goes well if I choose 386 version in grub, well, everything but the sound.

Hope this gives you a hint. Guess a reinstallation of the entire OS is better for me, I'll continue investigating:lolflag:

---

