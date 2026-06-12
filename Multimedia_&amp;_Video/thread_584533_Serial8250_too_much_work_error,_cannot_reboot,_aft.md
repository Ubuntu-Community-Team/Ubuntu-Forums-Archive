---
title: "Serial8250 too much work error, cannot reboot, after trying out new effects in gutsy"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by fuzzy_umbra on 2007-10-21
Hello,
I...
- Upgraded from 7.04 to 7.10.
- Installed the non-open source video card driver.
- Tried to enable the desktop effects, but got an error that "composite" was not turned on.
- Turned on "composite" in /etc/X11/xorg.conf, per an article I read on Ubuntu's site. (I backed up the file that was present.)
- Enabled the effects.  They were too processor intensive, so I disabled them.  But the processor was still swamped when moving windows around, even after rebooting, even after confirming that the effects were still set to "none".  By swamped, I mean it took 3-5 seconds for a window to redraw after click/dragging it with the mouse.  It didn't do this previously.
- I switched back to the open source driver.
- I replaced xorg.conf with the backup I made.
- Upon rebooting, I get the error "Serial8250: too much work for irq11" many times.  I cannot boot.

In retrospect, maybe I should have reverted to the backed up xorg.conf before reverting to the open source driver, since I made the backup while the non-open source driver was being used.  Maybe that's an issue, maybe not.  Either way, what can I do now?  I am probably going to just wipe and reinstall, since my data's backed up anyway, but it would be great to fix it instead.  I'll wait a couple days for a response first, though.

I've already looked at this:
[http://ubuntuforums.org/showthread.php?t=28025&highlight=too+much+work+for+irq11](http://ubuntuforums.org/showthread.php?t=28025&highlight=too+much+work+for+irq11)
from 2005, but it remains unsolved, so my expectations are low.  But hey, I'll give it a shot.

I saw this workaround:
"...my workaround for this was to set different IRQs for the PCI devices in BIOS..."
but this machine has seen a few versions of Windows, a few distributions of Linux, and a few versions of Ubuntu, in the past, and it hasn't been a problem, so I'm not interested in going there.

The video card is a Radeon, I think 9600 XT...it's been a while.
The machine is a Dell 8100, 1.6 MHz CPU, 750 MB RAM, and has run previous versions of Ubuntu with no hassle.  Well maybe a little hassle.  OK, with hassle.  But it always works out in the end.

Thanks all!

---

### Post by fuzzy_umbra on 2007-10-24
FWIW if anyone sees this, I solved it:
- Booted from the live CD.
- Copied that /etc/X11/xorg.conf to replace the other one that was on my hard drive.
- Rebooted. I was able to reboot and have graphics again, yippee, but performance was still poor.  e.g. To type in the search field for the forums, it took about 1 second for each letter to appear.
- The System Manager showed that "xgl" was eating all my cpu.
- I saw this:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/136650](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/136650)
- I removed xserver-xgl.
- Performance is good again.

So, I guess the upgrade installs xserver-xgl for you, or starts using it in a way that 7.04 did not, and that kills performance with some video cards.

---

### Post by fuzzy_umbra on 2007-10-25
PPS: After a clean install of 7.10, it works beautifully!

---

