---
title: "Samsung Tab USB Tether quit after Gingerbread update"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by trendal.toews on 2011-11-08
I am running 10.04. Was using a Verizon Samsung Tab with USB tether for an internet connection.  Yesterday my tab updated to the Gingerbread OS and apparently hosed my USB tethering.  Unfortunately it works in MS XP.  I am stumped. It doesn't work in 9.04 either and it used to.  

Originally I just plugged it in and it popped up the USB connection in the network tab on the top right.  Now it is just dead.  Doesn't pick up the network connection at all, while I can still browse the tab as a folder over the USB connection.

---

### Post by trendal.toews on 2011-11-09
Here is what fixed it.

Verizon says the tab should not be able to tether, never mind the fact that I have been tethering with it for the last six months.

Putting all that aside, I download the free version of Easy Tether from the Android market, installed the software on my Ubuntu 10.04 install and tried it, and it worked.

At first it was kind of a mess to set up.  You had to turn the Android app on, plug in the usb, open a terminal on Linux and run `easytether connect` and then you had a terminal window hanging around while you were connected.

After doing some snooping I found if you leave the app running on the Tab, and create and save a bash script that has the one liner, `easytether connect`.  Then in the '/etc/udev/rules.d/70-persisten-cd.rules' there is a line that looks like this - " SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="SAMSUNG_UMS_CD-ROM_34315AE5315600EC-0:0", SYMLINK+="cdrom6", ENV{GENERATED}="1" 

Add " RUN+="path/to/your/bash_script" right after the SYMLINK+="cdrom6", save and restart udev with `sudo /etc/init.d/udev restart` ....

...then when you plug your usb cable in it takes about a second or two and your connection comes up with no input needed.

---

