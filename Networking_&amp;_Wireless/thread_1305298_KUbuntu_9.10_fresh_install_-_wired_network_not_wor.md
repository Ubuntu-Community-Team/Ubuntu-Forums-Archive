---
title: "K/Ubuntu 9.10 fresh install - wired network not working"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by seiska on 2009-10-29
Hello,

I tested upgrading from fully working 9.04 to 9.10 and everything worked fine - specially wired network was functioning OK.

Then proceed to wipe that setup and did fresh install of 9.10 via alternative installer (as that was only way around of raid driver install which desktop installer forced).

Install went OK, other than not able to configure network with DHCP.

Banged my head a while, and tryed many things:

- Live CD of kubuntu 7.10 gets wired network connection
- Live CD of kubuntu 9.04 cannot get wired connect
- Live CD of kubuntu 9.10 cannot get wired connect
- Installing wicd (downloading packages on other computer) didn't help, as it usually does when facing problems with net.


$ lspci | grep net
00.12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

I remember having similar problems after installing 9.04, but IIRC those went quickly away after some kernel update.

----

Any ideas on what to do with this issue? Just wait for new some updates which might fix this issue?

---

### Post by seiska on 2009-10-30
After some sleep, I got my mind clear and remembered that I had to set some parameters for forcedeth to get wired connection - in 9.04.

Instructions given in document below gives me proper connection.
[https://bugs.launchpad.net/ubuntu/+bug/136836]("https://bugs.launchpad.net/ubuntu/+bug/136836")

---

