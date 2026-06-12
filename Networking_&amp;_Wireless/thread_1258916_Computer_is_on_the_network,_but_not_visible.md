---
title: "Computer is on the network, but not visible?"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by lildigiman on 2009-09-05
I have 4 Computers on my network, all in my room. 2 Ubuntu, 1 XP, 1 win2k (wireless).

Each is named something like CMDU01 or 02 (for ubuntu) CML2k01 for win2k and xp06 for XP.

All of them are connected to the internet through my wireless network via a Router/Receiver (easier than wireless cards for each of them).

Anyway, CMDU02 does not show up on the network at all, and I cannot remote to it or anything. It tells me the connection is closed. (I can ping it).

On another note, CMDU02 sees all the other computers (and remotes/pings them), but cannot see itself. 

What's going on?

---

### Post by pastalavista on 2009-09-05
Have you installed Samba on the Ubuntu that isn't seen? Ubuntu comes with the Samba client so it can see the other computers but you need to install the Samba server so they can see it. It's in the Synaptic repositories.

---

### Post by lildigiman on 2009-09-05
Well Thanks? I don't know what Happened I sudo-apt get installed samba (which I thought I had...) and rebooted and its fine now.

Thanks.

EDIT: Spoke too soon. Looks like the other computers cannot see it still, but it can see itself now.

---

### Post by jordilin on 2009-09-05
do you have some kind of firewall (iptables) set up in that one?

---

### Post by lildigiman on 2009-09-05
Not that I know of. It is a fairly clean install of Ubuntu on a new rebuild of old hardware (See my Signature).

I still can ping the IP but I cannot do any more than that.

---

