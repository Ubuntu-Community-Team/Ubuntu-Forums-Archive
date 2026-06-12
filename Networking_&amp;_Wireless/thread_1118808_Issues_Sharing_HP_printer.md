---
title: "Issues Sharing HP printer"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by neanderslob on 2009-04-07
Hi all,

I'm running 8.04 w/ kde3.5 and am hooked up via a USB port to an HP psc1315. I'm trying unsuccessfully to share said printer with a laptop running 8.10 w/ gnome.  Of course the printer works fine with the 8.04 computer via USB, and all the share boxes are checked off in the printer configuration menu.  The 8.10 computer can see the shared printer and so I added it as a new printer and selected the recommended drivers.  However when I go to print on the laptop, I get the error message "printer may not be connected."  When I access the printer on the 8.10 machine's manager and look at its properties it says "[ip] is busy, will retry in 30 seconds."  I've tried reinstalling all the drivers on both machines and the result is the same.  Any ideas are appreciated.

---

### Post by superprash2003 on 2009-04-07
when connecting to the printer try specifying ip instead of hostname.. also are you sharing via samba?

---

### Post by neanderslob on 2009-04-08
No I'm using CUPS.  The printer's profile shows the correct ip number.  Is there any other way of specifying it?

---

### Post by superprash2003 on 2009-04-08
ive been able to successfully share the same printer via samba.. hope this helps [http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html](http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by neanderslob on 2009-04-13
Yea, I thought about doing it with samba but it seems like such a cop out, being the windows way of sharing and all.  I was hoping to do it with CUPS but samba might be the way.

---

