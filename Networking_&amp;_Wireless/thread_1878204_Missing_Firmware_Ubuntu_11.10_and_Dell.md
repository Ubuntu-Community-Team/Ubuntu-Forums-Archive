---
title: "Missing Firmware Ubuntu 11.10 and Dell"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by mechchild on 2011-11-09
Hello,

I have just installed a fresh install of ubuntu 11.10 on my machine, that dual boots to windows pro

Everything seems to be working except my wireless internet - dell wireless 1470 dual band mini pci card

I have tried to install ndiswrapper, but to no avail.

any ideas what to do?

Thanks

Tim

---

### Post by Roasted on 2011-11-09
Majority of the time, "Dell" wireless cards are actually Broadcom. Broadcom is a difficult company to deal with on any platform, let alone Linux. The easiest thing would be to plug in to the internet via ethernet cable, then navigate to "Additional Drivers." Once there, see if a Broadcom entry comes up. Once installed, reboot, and see if your wireless behaves accordingly.

---

### Post by mechchild on 2011-11-09
did some more research and found out that it is a broadcom card - the driver for windows is BCMWL5 - 

I have gone to additional drivers, but it does not come up with anything.

any other ideas?

---

### Post by pdc on 2011-11-09
tell the forum what

> lspci.......says.......

.......just the broadcom bit would do ......

.......you might this to be rewarding reading.....

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Roasted on 2011-11-11
Ironically, I just ran into this last night with a Dell who came to me with an infected/corrupt XP install and wanted to try Ubuntu. It too had a Broadcom card.

I googled quick and found:

sudo apt-get install b43-fwcutter firmware-b43-installer

After that, I was in good shape. Try that perhaps?

---

