---
title: "wake on wireless"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by wannabegeek on 2010-08-17
hi all,

I wish I could use wol but my media server is across the house from my router and not possible to move either machine.

I have read that wake on wireless can work if the wireless card has a connection to the power bus...?

my media server is an IBM A50 with WOL, WO ring and wake on PCI ....
I figured I could get wake on pci to do something for me...when I hibernate the computer from the Desktop, there are no lights on the wifi card....

not sure if this will ever work, any thoughts  ?

tia
wbg

---

### Post by wannabegeek on 2010-08-17
I bringing the server machine to the router just for testing of WOL. Plugged in power for IBM and ethernet cable to router....hit wakeonlan -i xx.xx.xx.xx  12:34:56:78:89:99

nothing...
now, I am confused about hibernate and shutdown...there are shutdown options in the bios, S1 or S3.
I think this whole time I have been hibernating and not shuttingdown...can someone say which is required for WOL, S1 or S3 ?

thanks...

UPDATE: so I used the wrong MAC since I was trying to wake earlier with the wifi...need ethernet card MAC...and should use S3 I think which is standby. Switched IRQ to 10 in BIOS...BIOS says there is ACPI but APM options are there too...really confusing

---

