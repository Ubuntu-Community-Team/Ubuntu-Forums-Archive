---
title: "Terminal Services Client won't connect"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by npwanabe on 2009-06-17
I used to connect to my office Win 2000 server from my home ubuntu (Jaunty) computer with no problem. Now it doesn't work and I cannot find a solution. TSC returns the connection reset by peer message and gnome rdp returns the following:  Any help??


ERROR: recv: Connection reset by peer
ERROR: send: Broken pipe
X Error of failed request:  BadAtom (invalid Atom parameter)
  Major opcode of failed request:  23 (X_GetSelectionOwner)
  Atom id in failed request:  0x0
  Serial number of failed request:  56
  Current serial number in output stream:  56

---

### Post by Blue Wolf on 2009-07-08
I'm having the same problem, Can anyone point us in the direction of a solution??

Thanks in advance!

---

### Post by Blue Wolf on 2009-07-09
Bump

---

### Post by aquateen.carl on 2009-08-05
Same issue here. I can RDP into other machines on the network fine.
I can also RDP into the server thats having this issue from windows fine.
The only thing I can think of this server was recently updated and has all microsoft updates; so something related.

I managed to get it working, see my post here:

[http://ubuntuforums.org/showthread.php?p=7806861]("http://ubuntuforums.org/showthread.php?p=7806861")

---

