---
title: "windows drives on lan"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by barry.yarl on 2010-06-03
In Ubuntu when I access any WINDOWS pc on LAN I get to see all the drives present on that pc even though they are not shared (like C$ , D$) and also I can access these drives if I know the login Username, password of that computer . My question here is, why I can see all these drives n access them? and why some windows pcs do not allows access to these drives? (I guess there is some setting which doesn't allow access to these drives and what is it ?) I'd like to post a picture for more clarity but I don't know how to post it here.
[IMG]file:///home/bharat/Desktop/Screenshot-Windows%20shares%20on%20122.0.0.173%20-%20File%20Browser.png[/IMG]

---

### Post by suseendran.rengabashyam on 2010-06-04
Hi,

In your Windows Machine go to 'My Computer' -> right-click on 'E:' -> Properties -> Sharing -> Check 'Do not share this folder' -> Apply

This would make sure that your E drive is not shared over LAN.

Hope this helps.

---

### Post by bananas4370 on 2010-06-04
All the C$ D$ etc shares are administrative shares designed for remote access support by domain administrators.

To get rid of them showing up, please refer to this [article]("http://www.windowsnetworking.com/kbase/WindowsTips/WindowsXP/AdminTips/Network/DisableWindowsNTW2KXPHiddenAdministrativeShares.html").

Hope that helps.

---

