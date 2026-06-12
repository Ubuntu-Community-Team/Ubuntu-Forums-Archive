---
title: "Lenovo B560/Intel 3400 - &quot;no soundcards found&quot; error"
date: 2011-05-24
forum: Multimedia Software
---

### Post by sloom22 on 2011-05-24
Sound is not working on my new Lenovo B560 laptop with Intel sound card. The sound card appears in the lspci output. But the Preferences->Sound->Hardware menu is empty, not listing any soundcard.

ALSA diagnostics are as follows:

[http://www.alsa-project.org/db/?f=4665a5aaed775b36e5d55b0ad486fcd4f72f4f4c]("http://www.alsa-project.org/db/?f=4665a5aaed775b36e5d55b0ad486fcd4f72f4f4c")

When I run "sudo alsa reload" I get the following output:
> 
[sudo] password for me: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/me/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel
And the program hangs while unloading the module! (I can kill it with a simple control-C)

From what I've read online, it seems that I probably need to add the right option to the snd-hda-intel module in /etc/modprobe.d/alsa-base.conf. But I have no idea which module to use, I don't even know where to find a complete list of them!

(Note: There are laptops sold as "Lenovo B560" with different internals. For example, unlike most people I've found by googling, my B560 has an Atheros AR9285 rather than Broadcom wireless card. The sound cards may differ too. Also, the B560 model may be different from and unrelated to the G560 model.)

Has anyone succeeded in getting this sound card working?

---

### Post by sloom22 on 2011-05-27
Problem solved after much effort.

The soundcard is a Realtek ALC269VB model. In Ubuntu 11.04 and Mint 11, which use ALSA 1.0.24, sound works right out of the box.

(As for wireless, which did not work after the upgrade, I had to fix it using the "blacklist acer-wmi" option, see [http://ubuntuforums.org/showthread.php?t=1723617](http://ubuntuforums.org/showthread.php?t=1723617) . I also installed linux-backports-modules-net-natty-generic, that might have helped.)

---

