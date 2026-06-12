---
title: "Can't connect to Windows shares."
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by gseward on 2009-10-24
Network problem

I have three Windows XP computers [two Pro SP3, one Home SP3] currently online, one Ubuntu 9.10 Beta, and this one.

Windows computers can see, and use, each others shares, Ub computers can't.

Currerently on Ubuntu 9.04, new install, updated to default level.

I click Network, it opens and shows my Windows workgroup [304wj], dclick 304wj, get error dialog:
"Unable to mount location
Failed to retrieve share list from server"

Same thing happens in my Ubuntu 9.10 Beta box.

Until recently, when I installed Ub 9.04, after updating,  I would immediately see and could access all windows shares.  In the last month or so this has quit being true, and the same is the case with 9.10b.  I blame the updates, although I have no idea what specifically is wrong.
I have spent many hours reading forums and googleing for this problem, and trying suggested solutions to no avail. Others seem to have the same issue.  In the last month I have not been able to connect any Ubuntu installation to my Windows shares.  I have reinstalled, installed different versions of Samba, edited /etc/samba/smb.conf, no change.
Interestingly My networked printer works fine, as does a shared printer on the XP Home machine.
I can Ping any computer, but Traceroute fails, as does Lookup.
Any explanation or help will be appreciated.
I don't know what logs to look at/attach, put will provide as required.
Gil
[email]sewardg@pacbell.net[/email]

---

### Post by dmizer on 2009-10-24
Please see the 6th link in my sig. :)

---

### Post by gareim on 2009-10-24
Hey, thanks for the help Dmizer! I went to your link, and found out that the problem was that my Windows computer was in the workgroup HOME. Never thought that that would affect it in any way. Thanks! =]

---

