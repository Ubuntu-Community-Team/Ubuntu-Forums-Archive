---
title: "Update took out Network-Manager icon"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by Idiens on 2011-05-27
Using Ubuntu 10.04 (2.6.32-31)on a Dell studio today.

Update manager offered four updates, one about networking. I accepted. After restart the Network-Manager icon had vanished from the tool bar and was replaced by a second loudspeaker control icon. No ability to link to the internet. Starting Network-Manager from the pull-down menus did not help.

Muggins Noob thought, un/re-install Network Manager. Duh! Uninstall is fine, but re-installing from the web without Network-Manager, tricky. Sadly no ethernet wire available, either wifi or GSM/3G.

Help please.

I do have an old version of 10.04 on a CD. Is it possible to load Network-Manager off it? How?

The machine works correctly with internet under Vista (this message).

---

### Post by Iowan on 2011-05-27
It's possible that adding a Notification Area back to the panel might have been enough. Have you tried modifying */etc/network/interfaces* to create a connection? It's been a few versions since I've tried, but you could add these lines:```
auto eth0
iface eth0 inet dhcp
```
Then restart networking (or reboot).

---

### Post by Idiens on 2011-05-28
Thanks Iowan,

OK file modified, but with no apparent effect. What I really need is the ability to download and install Network Manager without having an Internet connection -i.e. somehow using another machine which does and transferring the files.

---

### Post by Iowan on 2011-05-28
System>Administration>Synaptic Package Manager>Settings>Repositories *should* let you include the CD as a source.

---

### Post by Idiens on 2011-05-28
Thanks, tried that.  I get "E:Failed to mount cdrom".
I tried using apt-cdrom, it did not help either.

Equally my attempts to load 11.04 are ending in bug reports.

---

