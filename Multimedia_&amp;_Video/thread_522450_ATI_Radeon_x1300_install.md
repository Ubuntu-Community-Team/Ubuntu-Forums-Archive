---
title: "ATI Radeon x1300 install"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by mfm3 on 2007-08-10
Hello,
I am trying to add a PCI ATI Radeon X1300 to my computer, running Dapper. And having problems.

The onboard card worked fine. I added the new card to the PCI slot, powered on, and started installing the fglrx driver. I used Methods 1 and 2, and neither of them work. Here's what happens:

I follow all the steps for installing the driver. I reboot, and set the PCI card as the primary VGA device in BIOS. Ubuntu starts to boot, and then when it gets to "Loading Hardware Drivers" it just hangs and never goes past that. 

If I do not set the PCI as primary, i get past this point but get an X error stating that it is not configured properly. I have tried to run dpkg-reconfigure xorg-conf to no avail.

I have read all the guides, wikis, howtos and posts I could find regarding this, however none seem to address this particular issue.

I'm obviously in over my head and I desperately need help. If someone could please help me, perhaps by letting me know what the correct procedure would be for adding a new PCI ATI card to replace the onboard card. Sorry for the Newb-ness of this post. I am at work and I really need this machine to work asap....

Thank you.

---

