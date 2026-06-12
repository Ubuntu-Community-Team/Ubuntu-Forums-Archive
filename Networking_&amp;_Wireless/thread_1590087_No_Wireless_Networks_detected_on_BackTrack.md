---
title: "No Wireless Networks detected on BackTrack"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by nbulchandani on 2010-10-07
Hello everyone,
i installed backtrack recently....and wireless networks are not detected....any idea which deb to install because it is based on ubuntu 8.10
Thanks

---

### Post by mysticdragon on 2010-10-08
Actually, I had downloaded Backtrack 4, and have issues with the wireless as well.  Went to I don't know how many sites, and each time did what was offered.  Nothing works.  From what I have been able to find so far, it is more an issue that Backtrack 4 is limited on the number of drivers it is supporting with respect to wireless.  I had a friend suggest downloading version 3.5 instead (which they have not had problems with).

Another thing to keep in mind is that Backtrack loads with the networking disabled, so when you complete your log-in, but before running startx, you need to start-network and wicd.

---

