---
title: "Internet in BackTrack 4"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by manishrana2009 on 2009-10-28
Can anyone tell me how can i use Internet in Linux BackTrack 4 ..I have a USB data card TATA photon..

---

### Post by bgeraghty on 2009-10-28
Networking is turned off by default in Backtrack. (For added sneakiness when entering a network, I suppose.)

```
/etc/init.d/NetworkManager start
```
Should get it fired up, and..


```
update-rc.d NetworkManager defaults
```
will do that automatically at every boot.


Lastly,
```
/etc/init.d/wicd start
```
enables the wireless manager.

---

