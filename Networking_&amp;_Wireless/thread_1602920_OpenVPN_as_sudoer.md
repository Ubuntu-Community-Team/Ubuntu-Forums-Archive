---
title: "OpenVPN as sudoer"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by dinuzz on 2010-10-22
Hi there

When I try to start OpenVPN as the regular user, the connection to the server can't be established (see log message below).

```
Fri Oct 22 08:35:53 2010 Note: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1)
Fri Oct 22 08:35:53 2010 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Fri Oct 22 08:35:53 2010 Cannot allocate TUN/TAP dev dynamically
Fri Oct 22 08:35:53 2010 Exiting
```

When I start the OpenVPN with the sudo command, everything works fine. Presumably because the TUN/TAP can't be assigned dynamically withour root previledges.

Any advise on this to make this run without the sudo command? What is common usage? How should OpenVPN be used under Ubuntu? With a GUI or easily with a command script?

Many thanks

---

