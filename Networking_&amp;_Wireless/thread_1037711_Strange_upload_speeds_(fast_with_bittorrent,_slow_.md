---
title: "Strange upload speeds (fast with bittorrent, slow with everything else)"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by swakya on 2009-01-12
The upload speed of my machine (Ubuntu 8.10) tops at 200KB/s with bittorrent, but with other protocols it doesn't go above 30KB/s. I tried to upload a file with ftp and scp so far.

I don't have a physical access to the machine (it's in France and I'm in the US) but I have sudo rights through ssh.

I apologize for not giving more data but since I have no clue about what the origin of the problem might be, I don't know what to test for. Also, the machine is behind a router (remotely configurable as well).

---

### Post by cb34 on 2009-01-12
for ftp let's say.. maybe try changing the ports that it runs on, maybe those certain ports you're using are limited by the internet provider.

im not an expert or anything, and dont really know what im talkin about..lol.. but that's the first thing that comes to mind.. and to basically check all the firewall/router rules in general.. on both ends.

---

