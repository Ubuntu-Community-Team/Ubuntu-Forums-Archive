---
title: "how do you switch from ar9170 to carl9170 before installing ubuntu?"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by triam_hayashi on 2011-09-27
Hi,

I'm running a different linux system right now, but I want to try ubuntu.  I noticed my ubuntu installation was really slow(didn't finish after 6 hours).  I tried the 'try ubuntu' option instead.  The usb dongle I use (netgear WNDA3100) seems to be operating at really low speeds using the ar9170 driver.  On my current os, I switched the driver from the ar9170(deprecated version) to the carl9170, and that did the magic.  

I'm wondering if I could switch the network drivers from ar9170 to carl9170 for my usb dongle like I did with the current os while I'm just in the 'try ubuntu' mode or the livecd version before starting the installation.  I figure if I can do this, I might be able to do the install with high speeds.  I just don't know how to switch the drivers in ubuntu.  I did it using a gui in my current os.  I couldn't find a way to change the drivers the dongle used.  I'm really not opposed to using the terminal, but I am relatively new to linux.

If I could get some help with switching drivers before I do the installation, I'd appreciate it :)

Thank you!

---

### Post by praseodym on 2011-09-27
Hi,

in the Live-system unload both drivers and reload the carl:

```
sudo modprobe -rf ar9170usb carl9170
sudo modprobe -v carl9170
sudo depmod -a
sudo service network-manager restart
```
In the installed system the ar9170usb needs to be blacklisted:

```
echo "blacklist ar9170usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reload the carl9170 driver or reboot.

---

### Post by triam_hayashi on 2011-09-27
Thank you very much!  That did the trick :)

---

