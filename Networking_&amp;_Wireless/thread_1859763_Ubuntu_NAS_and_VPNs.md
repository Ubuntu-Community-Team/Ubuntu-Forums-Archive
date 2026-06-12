---
title: "Ubuntu NAS and VPNs"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by lynus on 2011-10-14
Hi all,

On experience, I only have a couple of weeks experience with linux (and networking) but am really impressed with what's possible so far - so much so that I set up ubuntu 11.10 as a dual boot (the easy way) with Windows 7 last night.

The other day I took an old netbook that I had stopped using (XP died reinstallation dvd) and installed ubuntu 11.04.  As the power chord isn't the most reliable, I wanted to keep this computer in a fixed location so I decided to use this computer as a NAS server.

So far, I have got the NAS up-and-running with Samba and have added apache web server, Mediatomb media server, ssh, Tightvcn server, and have experimented with SickBeard.  Everything is working brilliantly on my home network.  On the tightvnc, I have been able to connect to the NAS with ssh through a VPN connection (to mimic a connection from outside my home network) but haven't been able to view the desktop with tightvnc (through VPN connection only).  Is this even possible?  I have forwarded port 5900 on my router to the NAS - does this need to match the desktop (i.e. if tightvnc shows Netbook:1 on the terminal, does the port need to change if tightvnc shows Netbook:2?)

Another thing I would like to do, if possible, is to control how other networked devices connect to the internet through the NAS.  For instance, I have a PVR and a PS3 and I would like to connect to a UK VPN server so that these can access BBC iPlayer, etc (I've temporarily moved from the UK and these are now blocked.)  My router doesn't seem to allow for VPNs nor is there an option on either device to connect to a VPN.  Is there any way to get the PVR and PS3 to use the NAS to connect to the router and get the NAS to connect to my VPN server (or to route those connections to different VPNs)?

Any pointer in the right direction would be great as I would like to learn as I go.

---

