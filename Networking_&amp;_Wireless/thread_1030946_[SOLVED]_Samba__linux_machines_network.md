---
title: "[SOLVED] Samba  linux machines network"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by Kidwell on 2009-01-04
3 weeks linux experience total
1 laptop ubuntu ibex
1 desktop ubuntu ibex
1 desktop vista soon to be ibex

[global]  
workgroup = PlugBoys
security = user
name resolve order = host bcast
update encrypted = yes
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
lm announce = yes
lm interval = 20
preferred master = yes
domain master = yes
announce as = NT
browse list = yes
browseable = yes
auto services = Public
local master = yes

[Public] 
available = yes
browseable = yes
path = /home/kidwell/Public
guest ok = no
read only = no
hosts allow = localhost 127. 192.168.4

that's my smb.conf file on both linux machines
i've registered a user on both machines with smbpasswd -a
i can see them in the network browser but they will not connect to the opposite one.  Example: Laptop can connect to Laptop Public but not Garage Public even though it can see Garage Public.  And standing at the Garage Desktop: Garage can connect to Garage Public but not Laptop Public even though it can see Laptop Public on the network.
I can not connect via smb://Garage/Public either...
I've also tried the connect to server option in the places menu, no luck.
What does work is installing SMB4k and using it to handle the shares... but i don't like it and it seems pointless to use extra software if Samba can do this configured properly.  I'm sorry if i missed something and take it easy on me cause i'm a linux retard.  But if it makes you feel better i concede 15+ years of die hard windows use to just 3 days of Ubuntu Ibex before i wiped Vista completely off two of my 4 machines.  Help me with this and i swear no more windows.

---

### Post by Iowan on 2009-01-04
There's a big difference between being new or inexperienced and being a retard.  Not intended as a fix, but see if this works:
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by sloopveedub on 2009-01-05
I am still learning Samba myself, but it sounds like you have set up both machines to act as a server.  This seems odd to me.  Perhaps there is a good reason to do this, but perhaps it is causing your problems??

---

### Post by dmizer on 2009-01-05
If your entire network is composed of Linux machines, I suggest you use a Linux file sharing protocol like NFS. Samba is not an ideal file sharing protocol for Ubuntu, and NFS is much faster. NFS is also significantly easier to configure.

Please see the 4th link in my sig for a good howto on setting up NFS servers and clients.

---

### Post by theacerguy on 2009-01-05
vista doesnt work unless you use samba 2 i think but the linux machines should work

---

### Post by Kidwell on 2009-01-06
> **dmizer said:**
> If your entire network is composed of Linux machines, I suggest you use a Linux file sharing protocol like NFS. Samba is not an ideal file sharing protocol for Ubuntu, and NFS is much faster. NFS is also significantly easier to configure.

Please see the 4th link in my sig for a good howto on setting up NFS servers and clients.

Your NFS walk through did the trick.
It was easy and works almost flawless.
But I'm still curious... will samba just not work between two linux machines... or am i doing something wrong. Is it an IBEX thing?

---

### Post by dmizer on 2009-01-06
> **Kidwell said:**
> Your NFS walk through did the trick.
It was easy and works almost flawless.
But I'm still curious... will samba just not work between two linux machines... or am i doing something wrong. Is it an IBEX thing?

Samba will work just fine. I had it working for years, and I still test it occasionally. But it is far more difficult to get set up properly. If you'd like to decide that for yourself, please see the first link in my sig for the SMB server howto, and the second link in my sig for the CIFS (samba client) howto.

Keep in mind, NFS is native to Linux. The open source version of Samba is a Windows protocol (closed source) that has been backwards engineered to provide integration into mixed networks.

---

### Post by Kidwell on 2009-01-07
Thanks again... that actually cleared up some of my resolving problems and everything is working perfect... I'm not sure how to do it, but i guess this topic is resolved?
Thanks for all your help!

---

### Post by Iowan on 2009-01-07
> **Kidwell said:**
>  I'm not sure how to do it, but i guess this topic is resolved? If problem is solved, resolved, or otherwise fixed, you can mark thread [SOLVED] using the Thread Tools pulldown.

---

