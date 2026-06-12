---
title: "connectivity to local Windows 7 box lost"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by RoyT on 2010-09-01
On my LAN I have boxes running Windows 7, XP, and Ubuntu 10.4. I have been using the "Connect to Server..." panel on Ubuntu 10.4 to connect to a share on the W7 box. Suddenly, I can no longer connect. I get the Password panel and it just keeps re-displaying every time I retype in my password. As far as I can tell nothing has changed. I have shutdown all the systems on the network and restarted them without help. I wonder if any one knows of an update to Windows 7 (or, ubuntu 10.4) that might have lead to this problem. (I can still connect to my Ubuntu box from my Windows 7 using SAMBA and I can still connect to my XP box from my Ubuntu box using "Connect to Server...")

---

### Post by Morbius1 on 2010-09-01
> I wonder if any one knows of an update to Windows 7 (or, ubuntu 10.4) that might have lead to this problemHave you installed Windows Live Sign-in Assistant to Win7.

It's a known Samba bug: [https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

And the fix until samba is updated is to remove Microsoft Live Sign-in Assistant : [http://social.technet.microsoft.com/For ... 79a5597527]("http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527")

---

### Post by RoyT on 2010-09-01
Thanks! That was it. I don't remember Live Sign-in getting installed, but it was there and uninstalling it fix my connectivity problem.

---

