---
title: "Won't recognize GT 430."
date: 2011-01-24
forum: Multimedia Software
---

### Post by KaptanKhronic on 2011-01-24
Installed Ubuntu before I got a new GT 430 and when I put it in and went on ubuntu, it was set to the stock resolution (800x600). Went to hardware settings and it doesn't even pick it up.  I also have another computer with an ATI card and it works fine.  Anyone have any thoughts?

---

### Post by BicyclerBoy on 2011-01-24
You need the nvidia-260-modaliases package.

Get this & the driver from
ubuntu Xteam ppa
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

This beats using the nvidia installer process...

You may have the nouveau kernel module problem.

cat /var/log/Xorg.0.log | grep nouveau
any sign of it & you might need to  blacklist the nouveau kernel module.

You need alsa 1.0.23 modules for HDMI audio..This is in your kernel or can be added.

---

### Post by KaptanKhronic on 2011-01-26
Thanks for the help man but can you tell me what this part is that you are talking about? 

cat /var/log/Xorg.0.log | grep nouveau
any sign of it & you might need to  blacklist the nouveau kernel module.

You need alsa 1.0.23 modules for HDMI audio..This is in your kernel or can be added.

---

### Post by cchhrriiss121212 on 2011-01-27
What you need to do is remove the open source driver (aka nouveau) first, then install the 260 series proprietary driver. 
You should find nouveau in synaptic package manager, remove anything you see there with the name. Then add the PPA and install the Nvidia driver, blacklisting if required should be done by the installer automatically so you don't need to worry about that.

---

### Post by realzippy on 2011-01-27
Please check System/Administration/HardwareDrivers for
offered NVIDIA driver.
If there is one,install it.Do not manually blacklist nouveau modules in this case...

---

### Post by fishissues on 2011-11-13
I removed the nouveau via synaptic and then i installed the nvidia drivers through the ppa.Worked as a charm.You can find detailed information concerning the ppa here : [http://linuxers.org/howto/how-install-software-ubuntu-ppa](http://linuxers.org/howto/how-install-software-ubuntu-ppa).

---

