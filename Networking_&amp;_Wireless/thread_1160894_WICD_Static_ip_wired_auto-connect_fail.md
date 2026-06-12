---
title: "WICD Static ip wired auto-connect fail"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by Mr.P1ckl3s on 2009-05-16
_**Solved:**_ sorry major noob doesn't know how to add solved tag to thread. :P
So after being rather vexed by the fact that network manager still refuses to do static-ips in 9.04 I switched over to wicd. I've got everything working except that the auto-connect for my *wired* network never seems to happen. If I click the icon, expand the wired network information by clicking the arrow, and then click connect I'm up and running. This isn't a big deal for me but the rest of my family uses this computer so I'd rather like to get auto connect to work.
After searching the interweb all I found was two people with this error in 8.10 with an older version of wicd, no solutions though.
Anyhow thanks in advance for any and all help
-me

---

### Post by t0mppa on 2009-05-16
I thought that one of the main reasons for updating to NetworkManager 0.7 was to allow the user to manually configure his interfaces (for instance a static IP) in /etc/network/interfaces and then setting the managed mode as true in /etc/NetworkManager/nm-system-settings.conf. So, that's bugged and doesn't work?

---

### Post by Mr.P1ckl3s on 2009-05-16
I know that I could set up the network in /etc/network/interfaces but I thought that required that I get rid of network manager altogether, which isn't what I want to do.
The second part of your post is new to me could you explain it.

---

### Post by Mr.P1ckl3s on 2009-05-16
bump

---

### Post by chili555 on 2009-05-16
> required that I get rid of network manager altogether, which isn't what I want to do.Is this a stay at home computer, or do you need to take it down to the cybercafe/library/university? Why do you feel you do not want to remove NM?

---

### Post by Mr.P1ckl3s on 2009-05-16
Well i've been having router issues so i want to be able to switch to dhcp quickly. Anyhow set up another interface in network manager via something i found with google [html]http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/[/html] and that's got it all working.

---

### Post by t0mppa on 2009-05-17
> **Mr.P1ckl3s said:**
> I know that I could set up the network in /etc/network/interfaces but I thought that required that I get rid of network manager altogether, which isn't what I want to do.
The second part of your post is new to me could you explain it.

Network manager is by default in unmanaged mode, where applying configurations manually through the interfaces file overrides its behavior, but if you change the mode in nm-system-settings.conf to managed, then it uses the settings you specified in the interfaces, but still continues to manage your interface otherwise.

That's the theory anyway, haven't seen anyone try this out, so don't know how it works out.

---

