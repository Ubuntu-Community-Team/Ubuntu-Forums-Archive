---
title: "Router lost power -- server will no longer"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by streetlight708 on 2011-11-01
Hey everyone,

I have a development server in my house programmed with Ubuntu 11.04 Server. It was working perfectly for a while, but we recently lost power in my house and after the reboot, I can't seem to get the server connected to the internet (and therefore the LAN).

Does anyone out there have a solution? I'm still a bit new at Ubuntu, so any advice will be greatly appreciated!

---

### Post by Iowan on 2011-11-01
From a terminal, **ifconfig -a** should tell you if the machine has an IP address. Did you set up the machine with a static address or does it get a DHCP address?

---

### Post by streetlight708 on 2011-11-02
When I do that, it only comes up with the et0 and lo settings, neither of which have the LAN ip I used -- I'm pretty sure I never set up a static IP, so I'm guessing I'm using DHCP.

---

### Post by streetlight708 on 2011-11-14
Please help if you can. The problem has only gotten worse.

I went and created a static IP address in that /etc/network/interfaces file, which allowed it to work only for a brief period of time before going offline again.

I recently installed 'ubuntu-desktop,' which made it freakout slightly before trying to boot without 'full network configuration.' Now it seems stuck on that ubuntu load page forever. I figured if I had a GUI it may be easier to figure out exactly why I can't connect to the internet.

The problem is I have a lot of family photos I ftp'd into the server, and my family is probably going to kill me if I loose them all. If you have any tips that could help me sort this out, I'd really really appreciate it.

---

### Post by lisati on 2011-11-14
Are you able to login to the router's browser-based control panel from any of the machines on the LAN?

---

