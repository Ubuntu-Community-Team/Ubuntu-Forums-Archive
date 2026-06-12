---
title: "Peer to peer with OSX"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by mmcmonster on 2006-07-02
Are there any pointers or how-to articles to get peer to peer file sharing with computers running Mac OSX?  I just want to hook up an ubuntu box with a mac via airport extreme and be able to share a few directories between the two computers.

---

### Post by mmcmonster on 2006-07-06
Bump.

Anyone with experience in this?  I'm just trying to have two-way access of files between an OS X box and an Ubuntu box on the LAN.

I don't really care to make the whole thing secure, since it lies behind my router and there are no MSWindows systems I have to deal with (decreasing the risk of viruses).  So anonymous logins from the LAN would be prefered.

---

### Post by spd106 on 2006-07-06
As far as I know OSX supports the SMB protocol so try installing samba on the ubuntu machine. There are multiple guides around to show you how. Maybe start [here]("https://help.ubuntu.com/community/SettingUpSamba").

You may also want to investigate avahi and gnome-share for bonjour-like access.

Good luck

---

