---
title: "Broadcom BCM4312 dell studio issues"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by AMD_Man on 2010-06-10
Hi

I recently installed Ubuntu x64 on my dell studio 1535 using the windows installer (wubi).

All seems to be working fine apart from the built in wireless card, the proprietary driver (found in hardware drivers) installs and activates successfully and works perfectly. Until I shut down or restart the system. On the next boot the wireless card is 'disabled' and no longer works.

The card I have is a Broadcom Corporation BCM4312 802.11b/g

I am going to try a proper install on a second partition rather than using wubi later on but wondered if this was a commonly occuring problem?

The wireless card works as soon as the driver installs, however I am shown a "restart to activate driver" message and after restarting it's dead :/

Thanks!

---

### Post by AMD_Man on 2010-06-11
Could it be possible that a different conflicting driver is being loaded at startup?

---

### Post by gunfyter on 2010-06-11
Have you tried

SYSTEM>ADMINISTRATION>HARDWARE DRIVERS

It should then search for proprietary drivers you need for your Broadcom modem.   Then click on the Broadcom B43 driver.  You should get a green radio button saying the driver is activated.

Let me know if this works....

I have only been Ubuntu 2 weeks now.  So take this advice for what its worth.

---

### Post by Roasted on 2010-06-11
Make sure you take note of what driver you are getting. I had to use the Broadcom STA driver, and I have a Broadcom 4322. I know it's not a 4312, but just throwing that out there...

---

### Post by AMD_Man on 2010-06-11
I have installed the proprietary driver, sorry if my original post was confusing.

The problem is that the card works fine after installing the driver, until i restart or shutdown the machine. Once I next boot up the wireless is "disabled", could this be a conflicting driver or for some reason the card needs to be initialized?

Thanks

---

### Post by AMD_Man on 2010-06-11
Seem to have fixed it!

Installed ubuntu properly onto a separate partition and then after installing the proprietary STA driver I went to "system -> startup applications" and unchecked "check for new hardware drivers".

I am not 100% sure which of the two solved the issue but it's okay now :)

Thanks for the replies!

---

