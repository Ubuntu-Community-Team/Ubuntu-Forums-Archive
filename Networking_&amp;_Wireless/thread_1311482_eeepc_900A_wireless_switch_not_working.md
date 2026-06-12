---
title: "eeepc 900A wireless switch not working"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by NTolerance on 2009-11-02
Running Ubuntu 9.10, I can successfully turn off the wireless by pressing the wireless switch function key.  The blue wireless LED goes out and Network Manager disconnects.  

Problem is, I can't turn the wireless back on.  If I hit the function key again the blue LED comes back on, but Network Manager can't find the interface and it doesn't show up in ifconfig.  

If I try to manually bring up the wlan0 interface with ifconfig I get this error:

```
sudo ifconfig wlan0 up
SIOCSIFFLAGS: Input/output error
```

Here's some dmesg output:

```
ath5k phy0: failed to wakeup the MAC Chip
ath5k phy0: can't reset hardware (-5)
```

---

### Post by hmpl on 2009-11-16
Hi,
if you haven't found it already:
You have to pass the following parameters to the kernel command line:
pciehp.pciehp_force=1 pciehp.pciehp_poll=1

This could be achieved by editing in /etc/default/grub the line with GRUB_CMDLINE_LINUX_DEFAULT :

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;pciehp.pciehp_force=1 pciehp.pciehp_poll=1 quiet splash&#8221;

and doing a "sudo update-grub2" afterwards.

Regards
Markus

---

### Post by Sven6210 on 2009-11-16
Great, that worked very well for me. Thank you for solving my last open topic with Ubuntu 9.10

---

### Post by NTolerance on 2009-11-30
> **hmpl said:**
> Hi,
if you haven't found it already:
You have to pass the following parameters to the kernel command line:
pciehp.pciehp_force=1 pciehp.pciehp_poll=1

This could be achieved by editing in /etc/default/grub the line with GRUB_CMDLINE_LINUX_DEFAULT :

GRUB_CMDLINE_LINUX_DEFAULT=”pciehp.pciehp_force=1 pciehp.pciehp_poll=1 quiet splash”

and doing a "sudo update-grub2" afterwards.

Regards
Markus

Thanks a ton for this fix.  I have tested it and it works great.  With this now implemented, Karmic is dare I say, fully functional on my 900A.  

Only two config file edits are required to get Karmic to this sweet state - the one provided here and another to get the touchpad working properly.

:)

---

