---
title: "Who is connected to my adhoc???"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2010-11-17
Is it possible to see if someone is connected to my adhoc network? either netstat command or nmap, not connected to pc just borrowing wireless

---

### Post by e79 on 2010-11-17
I would personally use Zenmap/Nmap to scan my network and check at the IP addresses it founds (Assuming you know which one are supposed to be connected, speaking of your PCs) . You can install them from the Software Center.

just my $0.02

---

### Post by spiky001 on 2010-11-17
Will that scan the wireless only, Not if someone is connected to pc I can scan the pc ok but that only tells me if someone connected to pc not just borrowing wireless, or maybe i dont know the command:redface:

---

### Post by spiky001 on 2010-11-17
Ok google fixed it, nmap -sP ip/24

---

