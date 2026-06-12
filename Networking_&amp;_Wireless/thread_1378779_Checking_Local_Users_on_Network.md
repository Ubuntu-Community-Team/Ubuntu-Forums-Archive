---
title: "Checking Local Users on Network"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by Qualia on 2010-01-11
I remember back when I used Windows, there was a shell command call "net view", which would allow me to see all the other users on my wireless net.

Is there any command or application that can do this? I dont mind if it is a terminal command either, but I would really like to know a way that I could see other users on my network. :D

---

### Post by changingstate on 2010-01-11
Tried smbstatus?

---

### Post by Qualia on 2010-01-11
I just did, and I got this output from the terminal:

Traceback (most recent call last):
  File "/usr/bin/smbstatus", line 18, in <module>
    from samba import irpc, messaging
ImportError: cannot import name irpc

---

### Post by changingstate on 2010-01-12
I'm going to hazard a guess you're using the samba4 packages, given there's a bug open that the moment for this exact issue ( [https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/346515](https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/346515) ). You can confirm this by searching synaptic for samba and seeing you've got the samba4 packages installed.

If running this command is important to you, I suggest downgrading to the samba 3 packages, smbstatus runs fine on my jaunty and karmic machines with those. The following command should install them for you, if I've missed something, please let me know.

sudo apt-get install smbfs samba smbclient samba-common nautilus-share

---

