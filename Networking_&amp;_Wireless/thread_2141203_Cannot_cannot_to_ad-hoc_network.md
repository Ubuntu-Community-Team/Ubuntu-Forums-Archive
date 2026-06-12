---
title: "Cannot cannot to ad-hoc network"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by Fire Phoenix on 2013-05-01
I'm trying to connect to a VNC server on a robotic platform using an ad-hoc connection, but it's failing because the computers on the network aren't properly communicating.

A few things:

1. Works using dlink network on both Ubuntu and Windows.

2. No ability to test whether I can connect using Windows (I have no Windows computer right now with VNC and the permissions to modify network settings), but I know it works without issue using Mac (course coordinator can connect to the exact same hardware on his Macbook). It seems to be an issue only occurring with Ubuntu (or Linux in general?).

3. The PC wouldn't connect to the ad-hoc network at all at first, but would apparently connect after manually assigning an IP on the PC. Platform seems to be hosting the network without trouble because non-Ubuntu can connect.

4. Ping test says host unreachable when I try to the ping robot, so even though it's apparently connecting, something isn't right. I've heard Ubuntu sometimes has issues with ad-hoc networks, but the wiki instructions and YouTube videos on the matter haven't helped.


_System Information_
Robot Platform using Ubuntu 12.04 LTS ARM on Pandaboard (unsure on exact Pandaboard model).
PC using Ubuntu 12.04 LTS (Intel x64) and Netgear WG111v2 USB network adaptor.


PS. In case you wonder why ad-hoc is necessary, the dlink network often has many robots connected at once and it very quickly becomes unstable and unusable. Ad-hoc is the only practical option.

---

