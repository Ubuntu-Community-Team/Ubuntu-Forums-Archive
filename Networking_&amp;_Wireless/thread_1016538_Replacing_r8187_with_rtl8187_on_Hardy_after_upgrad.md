---
title: "Replacing r8187 with rtl8187 on Hardy after upgrade"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by almikul on 2008-12-20
Some of the users complained that after updating the kernel on Hardy 8.04, Realtek stopped working. This happened to me after kernel 2.6.24-19 was replaced with 2.6.24-22. The card simply stopped working completely, and it didn't even see any wireless networks around. 

I found out that the driver *rtl8187* was replaced with *r8187*. However, I noticed that rtl8187 was still present in the new kernel in the same place as before. It just did not get loaded. I took a wild guess (I am a very green Linux user) and blacklisted current *r8187* in /etc/modprobe.d/blacklist and added line "rtl8187" in /etc/modules . After doing that the wireless works again! lsmod confirmed that rtl8187 indeed replaced r8187. 

This is a very simple and naive procedure, but it worked for me, so I hope it may work for someone else. At home I use WPA2 with passphrase, and it works fine with wicd.

[UPDATE]
The connection seems to drop randomly within 30-60 minutes. It is still unrelated to the above problem.

---

