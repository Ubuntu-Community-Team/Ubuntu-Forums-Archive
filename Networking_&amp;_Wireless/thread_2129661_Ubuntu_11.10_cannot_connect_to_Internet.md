---
title: "Ubuntu 11.10 cannot connect to Internet"
date: 2013-03-26
forum: Networking &amp; Wireless
---

### Post by ryann2k1 on 2013-03-26
I am having a [similar problem.]("http://ubuntuforums.org/showthread.php?t=1956423"), but my connection sometimes is on and sometimes off. Im connecting to the Internet using through wired nics. I have tried to append:

auto eth0 iface eth0 inet dhcpand reboot but it becomes worse, no connection at all.
Looking forward to your assistance.
Thanks

---

### Post by Iowan on 2013-03-26
I moved your post from an old thread to it's own.
You *should* be able to configure your adapters through Network Manager.
NM doesn't really play nice with */etc/network/interfaces*.  Ordinarily, that file contains only a definition for the loopback device (lo).

---

