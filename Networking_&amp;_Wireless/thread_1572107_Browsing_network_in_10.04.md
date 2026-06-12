---
title: "Browsing network in 10.04"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by RivalMarco on 2010-09-10
Hello,

Before 10.04 came out, i was running 9.10.. in 9.10 i was able to see other machines/servers in any workgroup, at any place.

Now i am running 10.04 for a while, and now i cant. Everytime i browser the Network (eventually the 'Windows Network'), i get an en error 'Could not get list from the server'.

I tried to install samba, to configure the workgroup.. but this did not really help anything.

I *can* access a share by typing smb:\\192.168.1.81 in Nautilus (where 192.168.1.81 is my NAS).. but smb:\\server would not work. (Where server is my NASs hostname)

Is there any setting i should change, so i can see everyone in the network again?

Thanks!

---

### Post by RivalMarco on 2010-09-11
Wowa!

Its working again =) In the end.. this single command solved
all my problems.

[HTML]sudo ufw disable[/HTML]

---

