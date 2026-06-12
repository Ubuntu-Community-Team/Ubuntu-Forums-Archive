---
title: "nm-applet woes"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by Calamus on 2006-07-11
I have Network Manager running, and I have an icon in the Notification Area, but there is no wireless indication.  If I left-click the icon, it shows a radio button for Wired Network and nothing else.  About says NetworkManager Applet 0.6.2.  What the heck am I doing wrong?

---

### Post by mgor on 2006-07-11
are you sure your wlan card work?
try `iwconfig` in a terminal.

---

### Post by nanotube on 2006-07-11
look here [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

specifically refer to the section below called "Dapper". most relevant quote:

> If it is not managing your network connections after upgrading to Dapper, you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces to let NetworkManager handle them.

so just try following that advice, comment things out except two lines for "lo", reboot, and try again

---

### Post by Calamus on 2006-07-11
Doh!  I had commented those lines out, but had inadvertently dropped the trailing 's' off 'interfaces', so I had /etc/network/interface and it turns out that doesn't do anything :P

---

