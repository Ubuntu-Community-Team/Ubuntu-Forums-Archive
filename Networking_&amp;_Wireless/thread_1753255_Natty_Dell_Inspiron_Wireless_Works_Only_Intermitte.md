---
title: "Natty Dell Inspiron Wireless Works Only Intermittently"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by eclipsechasers2 on 2011-05-08
I know there are many similar threads in this forum. Mine seems slightly different from all of them. I am using Wubi and Windows 7 on this machine; have never had a problem with the wireless card on Windows 7, and never had a problem with Ubuntu 10.10. After upgrading to Natty 11.04, wireless card detects no wireless connections on most boots (maybe 4 out of 5 times), but recognizes them sometimes. I can overcome this by using a USB wireless card, as I am doing now, but, obviously, would prefer not to.

I tried many of the solutions in the other threads (e.g. installing fwcutter, or reverting to the 10.10 version of bmwlc-kernel); none have worked successfully. I have used the "additional drivers" dialog to remove and reinstall the Broadcom STA driver. This has also proved ineffective.

I am attaching the output of the lshw command for one of the sessions when wireless wasn't working. It detects the card (BCM4313), but I don't know enough to see if there is any other information there that would help resolve this problem

---

### Post by garvinrick4 on 2011-05-08
Sef has the answer:

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by eclipsechasers2 on 2011-05-08
No, that's not the answer. STA is already installed, and, according to "additional drivers", in use.Nevertheless, tried to install ...lpphy..., but install failed (subprocess installed post-installation script returned error exit status 1). Will report that error through normal channels.

---

