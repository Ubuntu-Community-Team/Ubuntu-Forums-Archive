---
title: "Need beginners help with network connect with XP"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by RoyT on 2008-12-09
I have a network consisting of a Windows XP box and a Windows Vista box. I am trying to integrate a box running ubuntu. I have looked for a step-by-step help for FAQ without success. When looking at the Network I see an icon with the "WORKGROUP" title but clicking on it does not show either of my Windows boxes. When I look at "servers" it appears to take me though some steps to mount a share via "smb", but again nothing seems to show up. I am sure there is something simple that I am missing. So, a step-by-step process for integrating a ubuntu box into a Windows network would really be helpful.
Thanks.

---

### Post by gregphil on 2008-12-10
If you are hoping to get ubuntu 8.04 or 8.10 to be able to browse Windows shares you are doomed to failure (unless you allow un-authenticated users to connect to your Windows box, ie guest or anonymous).

There was a bug introduced to one of Ubuntu's gnome libraries when Hardy was released that broke authentication between Ubuntu and Windows.  This effects all gnome GUI app's that try to browse Windows shares. (They can't display a list of the available Windows shares).  You CAN connect to a share if you enter the entire share name, but that is not browsing, you must know the full share name ahead of time.

Since Kubuntu does not use gnome it does not has this problem, so for a work around you can switch to KDE until the gnome libray is fixed.

---

### Post by superprash2003 on 2008-12-10
presuming you wish to access the windows xp shares on ubuntu.. follow this [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)
if you still have problems.. post output of ifconfig from the ubuntu terminal..

---

### Post by corman420 on 2008-12-10
Thanks for the heads-up regarding the bug in Gnome. I was tryign to get my Ubuntu 8.04 box to connect to my Windows Vista box for 3 hours now. Every forum I went to didn't have an answer.

Any news if this bug will be fixed any time soon? Thanks.

---

### Post by RoyT on 2008-12-10
Thank you very much. That got me going with ubuntu on my network.

---

### Post by corman420 on 2008-12-10
> **RoyT said:**
> Thank you very much. That got me going with ubuntu on my network.

How did you get it to work? Was there an update released to fix the authentication issue?

---

### Post by gregphil on 2008-12-11
Bug(s) are still open:

[Bug #209520 in gvfs (Ubuntu): “SMB error: Unable to mount location when server configured with security=share”]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520") 

[Bug #207072 in gvfs (Ubuntu Hardy): “nautilus does not display samba shares for machines inside an ADS network.”]("https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072")

---

### Post by josephpmh on 2008-12-14
> **superprash2003 said:**
> presuming you wish to access the windows xp shares on ubuntu.. follow this [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)
if you still have problems.. post output of ifconfig from the ubuntu terminal..

Thank you!  I've been trying to figure this since April (not as important as other things, I suppose).  It works!

---

