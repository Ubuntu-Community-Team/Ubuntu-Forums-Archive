---
title: "network"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by tomdagreek on 2009-06-29
will ubuntu server see other versions of linux in the network window?
i can  ping using network tools (the desktop version of ubuntu server) but it will not bring "other" lol versions of linux...
i have a couple of diff boxes using linux and cannot get them to see each other.
put it this way the desktop will see ubuntu server but the server does not see the desktop.
would this be  a permissions problem? like adding a user or is there a app i can retreive to get these two to talk and play nice...
 i am trying to redirect traffic to the desktop from connection hitting the server.
any help would be appreciated
ubuntu server 8.04lts and various flavs of linux desktops

---

### Post by DGortze380 on 2009-06-30
> **tomdagreek said:**
> will ubuntu server see other versions of linux in the network window?
i can  ping using network tools (the desktop version of ubuntu server) but it will not bring "other" lol versions of linux...
i have a couple of diff boxes using linux and cannot get them to see each other.
put it this way the desktop will see ubuntu server but the server does not see the desktop.
would this be  a permissions problem? like adding a user or is there a app i can retreive to get these two to talk and play nice...
 i am trying to redirect traffic to the desktop from connection hitting the server.
any help would be appreciated
ubuntu server 8.04lts and various flavs of linux desktops

Sounds like you need to do a little research on TCP/IP Networking.

What exactly, specifically are your trying to do, maybe we can help.

---

### Post by dmizer on 2009-06-30
I'm not sure what you mean by "talk to". Technically, a successful ping is "talking to". I suspect that you mean that you'd like to share files between the various Linux machines? If so, please see the 4th link in my sig.

---

### Post by tomdagreek on 2009-06-30
sorry im a noob...
talking to < to me is i connect to shared files from a linux box to my windows box through "network"
obviously i can go on my deb box and extract files from the win box with no problem.
it is not the same with the server. when i use network(im am using a gui on this machine) it will not bring the deb box up as visible.
i am behind the same router on the network with both machines.
i can ping using network tools the llocal ip and it will show ports open to the server.
i was just making sure that it can be done.ubuntu server to deb machine.
i will research these replys when i get a chance.
btw ... im am redirecting traffic to http on the deb box bbut the connection is not being made.
i can ping http from my windows box and it seem to not have a prob
??
thanks tom

---

### Post by Iowan on 2009-06-30
In the file-sharing context, only "servers" will be visible to "clients". Ubuntu comes with samba-client pre-installed, but to share files (and be visible to other boxes wishing to see them) requires samba-server to be installed.  The link in **dmizer**'s sig is the same one I'd propose.

---

