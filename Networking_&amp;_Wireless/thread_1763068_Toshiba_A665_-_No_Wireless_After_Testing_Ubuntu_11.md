---
title: "Toshiba A665 - No Wireless After Testing Ubuntu 11.04"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by shawnc_nmb on 2011-05-20
Hello,

   I have been running Ubuntu 10.10 for a while now, and have had no problems.  A few hours ago, I decided I would try out Ubuntu 11.04 to see if I liked the Unity or not.  I decided to attempt to install it,  On install I noticed I did not have a Internet Connection so I canceled the Install and Rebooted.  Now My 10.10 doesn't see my wireless card.  I have noticed the Light that is on for the Wifi does not turn on and the Function keys to turn on/off the Wifi do not work.

I am baffled by what could have happened.  Right now I am using a very old USB Wireless D-Link card to Connect to the internet but this is not good as I use this computer everyday for work and for the past 3 hours have not found one solution to the problem.

So far,  I reinstalled the Kernel Headers hoping that would solve my issue but that didn't help.  Here's my lspci information

```

lspci | grep "Realtek"

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```

I'm not sure what relevent information I should post out of my dmesg or syslog honestly but I noticed it doesn't look like my old dmesg or syslog's when the wireless card worked.

Any help would be highly appreciated.

Shawn

---

### Post by shawnc_nmb on 2011-05-20
Ok,  I don't understand how this worked but.  I fixed the problem by starting to install Ubuntu 10.10, and quitting once I got to the checklist for Power, Internet Connection , etc.

After that I rebooted the machine and Auto-Magically my wireless worked.

If anyone can explain how this worked, I am dying to understand.  As it makes no sense to me since I never got to a point in either install to select a disc drive and partition  setup.

Anyway hope this helps someone, and if anyone has any ideas how this happened please inform me.

Shawn C

---

