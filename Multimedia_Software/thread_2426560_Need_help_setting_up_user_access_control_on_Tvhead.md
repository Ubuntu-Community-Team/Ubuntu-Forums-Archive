---
title: "Need help setting up user access control on Tvheadend"
date: 2019-09-10
forum: Multimedia Software
---

### Post by mehrdad_v on 2019-09-10
Hey guys,


This is my setup:



[LIST]
[*]Tvheadend is installed on a machine running Ubuntu Server 18.04.
[*]2x Intel NUC running Ubuntu 18.04 + Kodi + TVHeadEnd PVR are connecting to server from different rooms.
[/LIST]

I have an IPTV subscription that allows only one stream at a time and is added as a network on Tvheadend server.


I want to be able to watch TV on both clients at the same time, so I purchased another IPTV account.


Now I need to create another user on Tvheadend server so each client connect with their own user and access that particular network that is setup for them.


In short, I have networks “A” and “B” configured under “DVB Inputs > Networks” and I want to restrict user “A” access to only network “A” and user “B” to only network “B”.


i would appreciate your thought/advice on this. Thank you.

P.S. I have already posted this in Tvheadend's reddit and forum but not a single response, hence posting it here.

---

### Post by kalinkitechukat on 2019-09-11
I'm not sure that completely understand your setup, but when you have two different networks, you can use iptables for example.

The rules for network-1 used by user A will allow access only from ip address of user A to the servers ip-1 address.

The rules for network-2 used by user B will allow access only from ip address of user B to the servers ip-2 address.

---

### Post by mehrdad_v on 2019-09-11
> **kalinkitechukat said:**
> I'm not sure that completely understand your setup, but when you have two different networks, you can use iptables for example.

Thank you for your reply kalinkitechukat.
All devices are in one subnet. By "network" I mean TV network that is configured in Tvheadend.

---

