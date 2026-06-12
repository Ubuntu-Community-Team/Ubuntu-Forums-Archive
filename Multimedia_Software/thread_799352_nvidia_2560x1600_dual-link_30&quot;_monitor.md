---
title: "nvidia 2560x1600 dual-link 30&quot; monitor"
date: 2008-05-18
forum: Multimedia Software
---

### Post by iaw4 on 2008-05-18
dear experts:  i want to switch from gentoo to ubuntu.  alas, I cannot figure out how to install the nvidia support to drive a 30" monitor that runs at 2560x1600 (dual link).  yes, it runs under gentoo's nvidia-drivers module.

nvidia-server-settings tells me that I need to edit my X config file (just run nvidia-xconfig as root and restart the server).  alas, how does one restart the X server under ubuntu??  

I run nvidia-xconfig from bash, and it just tells me that it wrote an /etc/X11/xorg.conf .  nothing changes, though---right now, I am looking at a glorious, scaled, almost unreadable 800x600 display.

could someone please let me know exactly what one needs to do just to use native res on a 30" monitor?

sincerely,

/iaw

---

### Post by chewearn on 2008-05-19
To restart Xorg, press CTRL+ALT+Backspace.


To set-up the resolution you wanted, try the nvidia-settings first.  If this didn't work for you, you can consider manual editing of xorg.conf.

If you are in Hardy, you need to install nvidia-settings (you don't need to do this in prior version):
```
sudo apt-get install nvidia-settings
```

Run nvidia-settings with sudo, so it will be able to write to xorg.conf (after you have adjusted the screen to your satisfaction):
```
sudo nvidia-settings
```

.

---

### Post by iaw4 on 2008-05-19
thanks for the response.  I should have known about how to exit the X server.  It just did not ring a bell that it would then restart.

unfortunately, I still get same result.  Doing everything as su: first, I run nvidia-settings.  This gives me a warning panel

> **You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.**

So, I run nvidia-xconfig.  (Interestingly, it is installed, even though I have not selected/installed nvidia-xconfig in synaptics.)  I then restart the X-server.  I run nvidia-settings again.  same problem.

on my system, there are 22 packages that start with nvidia-*.  I currently have only nvidia-settings, nvidia-kernel-common, nvidia-glx-new installed.  It is not exactly clear whether this is the right combination of these 22 packages.  I am sure I need nvidia-drivers (the gentoo name), but I do not know which of these 22 drivers it is).

more help appreciated.  fwiw, this is something that would be nice to work out of the box, or at least have a clear FAQ somewhere.  This is not complex game related glx stuff--just basic resolution.

/iaw

---

### Post by iaw4 on 2008-05-19
very frustrating.  I randomly clicked around various nvidia related packages.  eventually, I stumbled upon linux-restricted-modules.  (Does nvidia-settings depend on it?  If so, it does not seem to be marked.)  I installed it, found system->hardware drivers, and enabled the nvidia drivers.  then I restarted.  now it tells me that they are in use.  good.

alas, nvidia settings still gives me the same error message, claiming that I am not using the nvidia driver.

lsmod tells me that I am running
nvidia               4579820  0 
whatever this may be.

my whole system also seems incapable of recognizing my monitor, despite the fact that it is a DVI monitor, which should be able to identify itself and its resolution just fine.

this is getting to the point where even Windows seems superior.

/iaw

---

### Post by chewearn on 2008-05-19
They update to Xorg 7.3 in Hardy.  This has resulted in nvidia driver problem for some people.  There is now automatic detection of screens and displays, that unfortunately, is not 100% working.

Coming from gentoo, you might have realize by now, ubuntu is hiding a lot of the details under the hood (in a manner of speaking).  For instance, there is less need to poke around the various nvidia* packages.  As you have already discovered, click a checkbox in Hardware Drivers got nvidia going.

However, it seemed something else might have broken, since nvidia-settings cannot be activated.  At this point, I'm not fully confident in giving straight instruction on fixing this.

Two things you might do (both which could mess things up further, or fix it):
1. Purge all nvidia related packages (completely remove, including settings); then, reinstall, but this time by using the simple GUI in "Hardware Drivers" and then install nvidia-settings again.

2. Go directly to nvidia website and install the driver manually.

.

---

### Post by iaw4 on 2008-05-20
I noticed that there is a kernel version mismatch between the ubuntu kernel and the xorg driver in the dmesg log.  so my best guess is a mismatch between the xorg and nvidia drivers.

actually, gentoo linux, despite its reputation for difficulty, managed to integrate the basic nvidia drivers quite nicely.  **emerge nvidia-drivers** updates both the linux kernel and the xorg driver.  however, it has many other tinkering shortcomings of this nature, which I wanted to get away from.  I think I will use this as a test case---to see when ubuntu becomes more user-friendly.

I don't want to start fiddling with ubuntu.  gentoo is by nature designed for tinkering.  everything source.  kernel-source installed.  expect to recompile, regrub, etc.  ubuntu is not designed for it afaics.  I am afraid I will run into weird issues trying to learn how ubuntu handles the linux kernel.  last time I tried ubuntu in a much earlier version, I couldn't even figure out where to get a copy of the linux kernel, and/or how to update the kernel to a newer version.  most of the time, I would be fine sticking with whatever the mainstream ubunto kernel is---I am just not brave enough to tinker with a no-tinker system in order to get my monitor to work.

hopefully ubuntu 9.xx will fix this.  when 2560x1600 becomes a "ubuntu-click" operation, someone please drop me a note.

(PS: in principle, this should not be too difficult.  clicking on nvidia-settings should know precisely what other packages should be installed and what other packages must not be installed.)

thanks everyone.

/iaw

---

