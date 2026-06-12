---
title: "Problem with inet_addr()"
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by EdisonAlbuquerque on 2012-12-28
I wrote a small program in C++.
To populate the socketaddr_in I used inet_addr, to convert from dotted decimal to binary, in bigendian order.
The problem is that, despite the program runs and shows that the message was sent, nothing appears on the Wireshark screen. If I use htonl(inet_addr()), Wireshark show my datagram but with the IP address reversed (from 127.0.0.1 to 1.0.0.127, which is understandable). I wonder if any of you already had this problem and could help me.
Tks.

---

### Post by The Cog on 2012-12-28
If you are sending to 127.0.0.1 then you need to get wireshark to look at interface lo (or all interfaces) rather then looking at eth0. Don't know if that's your problem, just a wild guess.

---

### Post by EdisonAlbuquerque on 2012-12-29
It worked very well. My code is allright. The problem was configuring Wireshark the right way.
Thanks a lot.

---

