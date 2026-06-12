---
title: "is there a way to run wireshark without root"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by koba101 on 2010-03-24
I'm asking this question cause I see that the only way I could monitor any interface is having wireshark run as a root user.  

This is something I do not want to do (for obvious reasons)

Any ideas?

---

### Post by DGortze380 on 2010-03-24
> **koba101 said:**
> I'm asking this question cause I see that the only way I could monitor any interface is having wireshark run as a root user.  

This is something I do not want to do (for obvious reasons)

Any ideas?

You must run wireshark as root. A normal user does not have sufficient privledges to access the low level network resources wireshark needs.

---

### Post by koba101 on 2010-03-24
it's pretty dangerous to have something like that run as root...what if there's a security flaw in it,,,then it could compromise the whole system

I found this link  [http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges)  that seems to ease the problem a bit, but in the end, could wireshark be made part of a special group that only has access to say the networks resources for example?

---

### Post by DGortze380 on 2010-03-24
> **koba101 said:**
> it's pretty dangerous to have something like that run as root...what if there's a security flaw in it,,,then it could compromise the whole system

I found this link  [http://wiki.wireshark.org/CaptureSetup/CapturePrivileges](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges)  that seems to ease the problem a bit, but in the end, could wireshark be made part of a special group that only has access to say the networks resources for example?

That group would still need low-level access to network resources. There wouldn't be a difference.

That's the nature of the program. It would be far more dangerous to have low-level access to network resources available to unprivileged users.

---

### Post by 2hot6ft2 on 2010-03-24
That's the nature of pentesting tools. If you're not comfortable running with godlike (root) powers you shouldn't use wireshark or other pentesting tools. You really should have known the risks before attempting it.

---

### Post by koba101 on 2010-03-25
guess the best solution would be to run it in a virutalbox

---

