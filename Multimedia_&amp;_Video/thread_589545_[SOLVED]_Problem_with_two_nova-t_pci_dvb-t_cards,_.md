---
title: "[SOLVED] Problem with two nova-t pci dvb-t cards, one remote and Feisty"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by oscarsfriend on 2007-10-24
Hi,

I have two nova-t pci cards installed (just installed the second).  They work fine, as far as watching/recording TV goes.  However, I have a problem getting the remote to work properly.  It worked fine when I had the one card, but Feisty has an annoying habit of switching device numbers.  This means that sometimes it works, and other times it doesn't (unless I switch the plug around on the back).  I tried plugging both receivers in but the second one registers some keys on the remote as well, which doubles up the key presses for those keys.  Anyone solved a similar problem or have any ideas what to do?

Any help will be much appreciated,

Oscar's friend

---

### Post by oscarsfriend on 2007-10-24
I may have found a fix, which so far seems to work.  Originally I had the following udev rule to map the remote to /dev/input/irremote:
> 
KERNEL=="event*",SYSFS{vendor}=="0x14f1",SYMLINK="input/irremote"

But this doesn't work with two identical devices installed.  Instead I tried:
> 
KERNEL=="event*",SYSFS{vendor}=="0x14f1",KERNELS=="0000:01:09.*",SYMLINK="input/irremote"

KERNELS=="0000:01:09.*" should locate the PCI card slot by a unique number.  Note that the * is needed as one time it was 0000:01:09.2 and another time 0000:01:09.0 (most likely as the card shows up as three different devices).  You can find out the correct number doing this: udevinfo -a -p $(udevinfo -q path -n /dev/input/eventX ) where X is number of the ir device (on that particular boot).

More testing needed to confirm fix...

---

### Post by oscarsfriend on 2007-10-24
Well, I've been rebooting every few minutes for the last hour, and it seems to work every time.  I arrived at my solution after stumbling across this post: [http://lists.debian.org/debian-user/2007/10/msg00090.html](http://lists.debian.org/debian-user/2007/10/msg00090.html)

---

### Post by SeanHodges on 2007-12-24
To confirm your fix:

[http://ubuntuforums.org/showthread.php?t=222672](http://ubuntuforums.org/showthread.php?t=222672)

Shame I didn't get here earlier.

---

