---
title: "Network Manager and ipw3945"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by shoofy on 2006-07-09
I have an ipw3945 and I've managed to get it working correctly. I'd like to try using Network Manager to make switching between wired and wireless connections simpler (right now I frequently need to disable the wired connection after unplugging it before I can use the wireless). My problem is that Network Manager seems incapable of recognizing my wireless connection. Right nwo I am posting this wirelessly, an yet Network Manager reports "No network device found." I tried both the gnome and KDE version with the same result. Is the ipw3945 not compatible with Network Manager? Is there any way I can make it work? Is there an alternative app I can use that will accomplish the same thing?

---

### Post by ysse on 2006-08-10
I had the same problem with ipw2200, and it was because the wireless connection still was configured in the ordinary network settings (System - Administration - Networking). 

Network Manager will not try to handle any connections that are set up with the ordinary tools. So, you need to disable your wireless connection (use the Properties button and uncheck "Enable this connection). Deactivating is not enough.

After that little exercise, Network Manager should find your wireless connection. If not, then maybe ipw3945 isn't compatible after all.

---

