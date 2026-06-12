---
title: "nvidia driver won't stay loaded"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by raeb on 2006-10-19
I'm having a hard time trying to get the nvidia driver working properly.  After trying many things to get it to load, I am currently at the point where I have to (from a cold boot) boot into x with my driver set to vesa.  When I've logged in, I run the commands: 

lrm-manager
depmod -a (as sudo)

After those I edit the xorg.conf driver back to nvidia, restart the gdm with ctrl-alt-backspace, and it'll load the driver.  The problem is that upon any reboot, x does its usual cool trick of not working.  The problem it gives me is a 

Fatal: Could not open /lib/modules/2.6.15-27-386/volatile/nvidia.ko

Any suggestions?  I'm a unix noobie so if it's something obvious go easy on me  :(

---

### Post by dutchmega on 2006-10-19
Same problem here. Edgy Eft, with latest updates. I tried an onofficial driver and the official one (just apt-get install nvidia-glx) but still the same error.

I have 2.6.17-10-386 though

---

### Post by dutchmega on 2006-10-19
Update: Downloading the newest driver from nzone and install it. It works fine here :)

---

### Post by raeb on 2006-10-19
> **dutchmega said:**
> Update: Downloading the newest driver from nzone and install it. It works fine here :)

The beta driver?  I tried it and it said it couldn't be installed because of some missing/mismatched kernel sources.

---

### Post by raeb on 2006-10-19
Fixed my own problem, I think.  After doing a lot of searching around, I found this thread, [http://ubuntuforums.org/archive/index.php/t-60591.html](http://ubuntuforums.org/archive/index.php/t-60591.html), which basically had my exact same problem.  The second to last post by sean, he did this:

> 
I got it working by editing /etc/init.d/xorg-common and inserting the following line:

/sbin/lrm-manager

After the sourceing of rcS

However, since I'm running on dapper, there is no /etc/init.d/xorg-common file.  Instead, the file is /etc/init.d/X11-common.  I did as sean described in the quote and it worked like a charm.  Hope this helps anyone else having my problem.

---

