---
title: "Youtube crashing my wireless"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by horde on 2010-05-13
After recent apt-get dist-upgrade that installed new kernels I'm having a really strange time with my wireless.  Whenever I try to watch a streaming flash video over the web my wireless card disconnects from my AP and I need to unload/reload the driver with modprobe to get it to reconnect.  Have reproduced  this fault with YouTube, LiveLeak, and BBC iPlayer. 

It also happens very occasionally when doing other things (eg. streaming flash (and other) video over my LAN, normal web surfing, etc.), but is most consistent with flash video over the web.

Am using Intel Wireless 3945ABG card with iwl3945 driver (running on a Dell Inspiron 9400).  It happens with with 2.6.32-21-generic and 2.6.32-22-generic kernels but not with 2.6.31-21-generic (as such have am using 2.6.31.21 kernel now).

Kern.log reports the following:
> kernel: [32938.500505] No probe response from AP 00:11:22:33:44:55 after 500ms, disconnecting. *NOTE* not the real mac address

kernel: [32939.129035] iwl3945 0000:0c:00.0: Error sending REPLY_RXON: time out after 500ms.

kernel: [32939.129044] iwl3945 0000:0c:00.0: Error setting new configuration (-110).

kernel: [32939.628273] iwl3945 0000:0c:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.

kernel: [32941.128071] iwl3945 0000:0c:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.

Any help would be greatly appreciated.  Thanks in advance.

---

### Post by Khuutra on 2010-05-19
I don't know how kosher it is to bump threads after a week, but I'm having close to the same problem here.

---

### Post by danielbair on 2010-07-05
Same problem here. Probably an Intel Wireless driver thing. It is nice that the wireless works now without any needed kernel mods like before, but bugs like this are very annoying!

---

