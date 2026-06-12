---
title: "VLC multicasting problems"
date: 2008-12-07
forum: Multimedia Software
---

### Post by flatulant on 2008-12-07
Hello, I'm trying to multicast a video.  I stream over udp/rtp with multicast address 239.255.100.101 and port 1234 with SAP announcements, but it does not appear on any other computer, and when I manually input the address, video does not appear, even though it is streaming from my computer.  Is it a port forwarding problem or something?  I"m using Ubuntu 8.04.

---

### Post by jmoorse on 2008-12-07
Are you within the same local LAN segment?  If so please post switching hardware information.

---

### Post by flatulant on 2008-12-07
I'm not trying to broadcast over a LAN, I'm trying to broadcast over the internet.

---

### Post by jmoorse on 2008-12-08
It is my understanding that the 239.0.0.0/8 addressing space is used for private multicast, thus is not internet routable.  (Much the same way one would make use of the 192.168.1.0/24 addressing space)

I would consult the VLC documentation to see if there is another way to make your video stream available.

---

