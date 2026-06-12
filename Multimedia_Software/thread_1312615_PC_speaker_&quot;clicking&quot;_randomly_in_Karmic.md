---
title: "PC speaker &quot;clicking&quot; randomly in Karmic Koala"
date: 2009-11-03
forum: Multimedia Software
---

### Post by wribeiro on 2009-11-03
Ubuntu Karmic Koala 64, clean install from CD after entire disk format.
All multimedia softwares working fine, sounds are played as expected, everything is OK, except for one reason: PC speaker "clicks" all the time, whenever sound system is accessed by any program.
For example: each time an alert sound is about to be executed, or when mouse pointer is over a mp3 file, or when Sound Preferences window is opened, or in many other moments, there is a loud click in PC speaker, even if sound volume is zero, or if headphone is plugged.
Any solution for this troublesome problem?

Ubuntu 9.10 Karmic Koala AMD64
Gnome 2.28.1
Kernel Linux 2.6.31-14-generic

HP Pavilion dv6000
AMD Turion 64x2
Sound: HDA-Intel - HDA NVidia

---

### Post by chiques on 2009-11-03
I have the exact same problem only that I'm using the 32 bit version.

> user@user-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
user@user-laptop:~$ 


user@user-laptop:~$ uname -a
Linux user-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux


---

### Post by Bumbler on 2009-11-03
There are a whole range of issues arising from the hda-intel hardware. That's because it's possible for the manufacturer to configure it in so very many different ways. I was chasing similar problems on my Inspiron 545 MT. I posted my tale of woe [here]("http://jehurst.wordpress.com/2009/10/31/ubuntu-karmic-koala-on-inspiron-545-mt/").

There is a page for that in the Help Wiki for Ubuntu [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto"). Pay particular attention on how to determine your codec.

I would add, in Karmic the documentation now includes a whole extra page just for Intel HDA: ```
/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
``` This will help you identify which particular model matches your codec.

I'm not a Linux audio expert, but I believe you'll find this information useful.

---

### Post by whoop on 2009-11-03
Same issue here, I have not yet looked into this problem...
using 82801H (ICH8 Family) HD Audio Controller at the moment...

Anybody know if there is a bug report on this?

---

### Post by whoop on 2009-11-03
This looks like a similar bug report on this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)

It seems to have a workaround via disabling the power save feature for the time being.

---

### Post by chiques on 2009-11-03
I found something that fixed mine

Go to **/etc/modprobe.d/** and comment the line shown below in ***alsa-base.conf*** by using the **# **symbol as shown below


> # Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=10 power_save_controller=N


I had to reboot for the changes to take effect.


Apparently in the midst of the Ubuntu community trying to be a bit greener, they added this feature to put the sound card in sleep mode to save a little energy. I personally appreciate the effort.

---

### Post by BigBananaMan on 2009-11-15
Thanks chiques, this was driving me nuts.  Instead of commenting it out I just changed the 10 seconds to 300.  I don't mind it every now and again, just not constantly.

---

