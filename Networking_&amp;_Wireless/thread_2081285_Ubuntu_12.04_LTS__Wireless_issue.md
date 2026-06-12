---
title: "Ubuntu 12.04 LTS  Wireless issue"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by rogersaavedra on 2012-11-06
I am new to Linux.  I just installed Ubuntu 12.04 LTS on a Dell Latitude - 430, wireless is not enabled.  First I ran Ubuntu from a disk, which showed the driver (Broadcom STA wireless driver) it is a proprietary driver. (please see screen shots).

When I installed Ubuntu on the machine and went to check for additional drivers, i receiver error messages: "Downloading package indexes failed..." then "No proprietary drivers are in use on this system." (screen shots attached).

Then I went into "Ubuntu Software Center" "Universal Access" that lists the driver, when I open it, shows the driver as "Installed".

How do I enable it, how do I resolve this issue?  I will appreciate any help.

Thanks.

---

### Post by gordintoronto on 2012-11-06
There are several wireless controllers available for the Latitude D430, the Intel 4965, Intel 3945, Dell Wireless 1390 and Dell Wireless 1490. The solution will depend on which one you have. To find you, open Terminal and type in this command: lspci

About a dozen lines will appear, and one of them should contain "802". That identifies your wireless adaper.

Did you use a wired Internet connection when you tried to check for Additional Drivers?

---

### Post by rogersaavedra on 2012-11-10
No I did not use wired connection.  How do I activate the driver so I connect to the internet?

---

### Post by gordintoronto on 2012-11-10
> **rogersaavedra said:**
> No I did not use wired connection.  How do I activate the driver so I connect to the internet?

Universal access has nothing to do with wireless.

Use an Ethernet cable to connect to your router. Run Software Centre. Select Edit/Software Sources. Click on the "additional drivers" tab. Select the driver for your wireless. Shut down your computer and disconnect from your router.

---

### Post by rogersaavedra on 2012-11-13
This is what I get when I run "lspci":

Ethernet controller: Broadcom Corporation Netxtreme BCM5752 Gigabit Ethernet PCI Express
Network controller: Broadcom Corporation BCM4311 802.11a/b/g

I don't have an router at home, just just wifi signal that I connect with my Windows system.
Can I try what u suggested using a LAN drop at school?

---

### Post by ahallubuntu on 2012-11-13
Sure, if your LAN drop at school is connected to the internet, you can use that to download/activate/install your wireless driver for your Broadcom wireless card.  If it doesn't automatically work, while you're online there dig up past posts about the Braodcom BCM4311 card that you have - plenty of solutions posted for it.

---

### Post by rogersaavedra on 2012-11-13
Thanks for your help.  The wired connection worked.

---

