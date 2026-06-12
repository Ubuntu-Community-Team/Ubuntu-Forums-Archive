---
title: "Unable to set up my network connection"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by rmcellig on 2010-08-17
All of the computers on my LAN (all wired) have complete network access. They are all set up as DHCP. My Ubuntu machine is the only one that doesn't seem to work (worked fine before when I set it up with a manual IP address but now with DHCP, no connection is established. Enclosed is a screenshot of my iMac configuration as well as my Ubuntu configuration.

What do I have to do to get my Ubuntu 10.04 machine working again?

---

### Post by Iowan on 2010-08-17
[Here's]("http://ubuntuforums.org/showthread.php?t=1156441") a Jaunty problem/fix - but it hasn't solved many problems lately. Some routers don't seem to like Linux/Ubuntu - what kind are you using? You can try **sudo dhclient** - probably will see something ending similar to:
```
...
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by rmcellig on 2010-08-17
Looks like I fixed it (crossed fingers) I created a new network connection as DHCP and everything now works. Hope it stays that way :)

---

