---
title: "eth0 not detcted in Ubunutu, fine in XP"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by Sam Jelfs on 2009-02-06
Hi all,

First post, and apologies, first for it being a call for help, and secondly if this has already been covered, I did search but turned up nothing...

I've for an Acer Aspire One (150) dual booting between Ubuntu and Windows XP Pro.

Up until today Ubuntu was working fine, but having booted it this morning, it is no longer detecting my ethernet controller.

ifconfig -a returns ath0, lo, pan0 and wifi0, but no eth0, and eth0 is not listed in /etc/networks/interfaces.

lspci -v does not detect eth0 either.

checking syslog I see...

[QUOTE=/var/log/syslog]
Feb 6 11:12:54 sam-laptop kernel: [  909.277948] pciehp: Card present on Slot(1)
Feb 6 11:12:54 sam-laptop kernel: [  909.326262] pciehp: Card not present on Slot(1)
Feb 6 11:12:54 sam-laptop kernel: [  909.330395] pciehp: Card present on Slot(1)
Feb 6 11:12:54 sam-laptop kernel: [  909.378706] pciehp: Card not present on Slot(1)[/QUOTE]

... and that repeats over and over for as much as the log I can see, every time I check it.

Now the thing is that the ethernet port works fine in Windows, so I am assuming it is not hardware at fault, esp seen as the machine is little over a week old...

I'm running Ubuntu 8.10, with kernal 2.6.27-11, but it also happens with the earlier kernal versions 2.6.27-9 and 2.6.27-7.

Any suggestions as to what to check regarding getting it working again? I hope I have been comprehensive in giving enough info to diagnose the problem...

Regards

Sam J

---

### Post by Sam Jelfs on 2009-02-06
adding some more information, if I disable pciehp by commenting it out in /etc/modules my eth0 connection comes back and works fin on reboot, but my card readers no longer do... it seems to be an issue a few if the eeePC users are having as well, but I'm yet to find a solution on my travels around the WWW, so if anyone has come across this before do please let me know.

Sam

EDIT - Found out that it is a kernel bug - more info here if anyone else is suffering... [https://bugs.launchpad.net/ubuntu/+bug/313866](https://bugs.launchpad.net/ubuntu/+bug/313866)

---

### Post by dxd_2009 on 2009-02-06
go to Bios


1


[http://www.freeimagehosting.net/uploads/c5b365b1ba.jpg](http://www.freeimagehosting.net/uploads/c5b365b1ba.jpg)





2


[http://www.freeimagehosting.net/uploads/a618cee753.jpg](http://www.freeimagehosting.net/uploads/a618cee753.jpg)


Not all Bios are same

---

### Post by Sam Jelfs on 2009-02-06
surely a) the BIOS would affect both the operating systems, not just 1, and b) a BIOS issue would have been present since the last BIOS update (prior to the problem starting), rather than at some random time...

Anyway, like I said in my above post, it seems to be a known kernel  issue which is currently being worked on. Shall have to see if it is fixed in the next set of updates...

---

