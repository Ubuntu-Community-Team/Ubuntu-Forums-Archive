---
title: "Wireless set up in Dapper"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by joplass on 2006-06-02
Dapper came with wireless listed as "eth1" in "Networking" but it does not work.  Is there a way to make it work?  Or can I remove it and use old ndiswrapper?  As a matter of fact I tried ndiswrapper but it did not work meanwhile ndiswrapper -l said hardware and driver are present.  
Some help please,

---

### Post by j-strap2 on 2006-06-02
I had problem getting wireless to work, but OK now. Which wireless card are you running? My card had a broadcom chipset. For some reason, the Dapper kernel has a dodgy Broadcom-compatible module which loads by default. I had to disable this, then I loaded the windows drivers with ndiswrapper -i and managed to configure networking OK. I had to manually add ndiswrapper to the list of modules loaded at boot.

---

### Post by polo_step on 2006-06-02
[FONT="Courier New"]I believe there's an easier way, but it would probably be more effective to ask about this in the "Wireless Support" forum here.

Good luck![/FONT]

---

### Post by joplass on 2006-06-02
Got it!  I am in business now

---

