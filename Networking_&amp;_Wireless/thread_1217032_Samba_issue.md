---
title: "Samba issue"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by 7raTEYdCql on 2009-07-19
My networking skills are very noobish, i need some help here with sharing files over a wireless network


I don't really know what i have done. I have set up a wireless network, and my second laptop can connect to this network and therefore is wirelessly connected to the net. Now i want to use this network to share folders on my comp with my second comp. My comp runs Jaunty, while the second comp is still on windows xp.

The folder i wanted to share, i right clicked and shared it. From now on i refer to my comp as server, and second comp as client.

When i type, net view \\mehrzad-laptop(name of the server) on the client, it lists the name of the folders that i have shared over the network. But i can't access these folders on the client machine.

I go to network places and nothing about my shared folders is mentioned. I haven't edited my smb.conf file, i thought that right clicking and sharing is the gui way of sharing. Can someone help me and explain to me from basics about sharing a folder.

---

### Post by swerdna on 2009-07-19
The Nautilus shre tool seems to have worked. That will not create shares in the file smb.conf. It lodges the configuration for shares in the directory /var/lib/samba/usershares.

To enhance browsing from the windows box you should make the Server windows-like in the way share names are resolved. Make a Local Master configuration as detailed here:
[Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")
The chief points are to edit the line name resolve order so it looks like this:
```
name resolve order = bcast host lmhosts wins
```
make sure the line
```
workgroup = WORKGROUP
```
names a workgroup identical to the name in windows

and put in these three lines for the Local Master Browser:
```
local master = yes
preferred master = no
os level = 33
```

Refer to the tutorial for the full detail

---

