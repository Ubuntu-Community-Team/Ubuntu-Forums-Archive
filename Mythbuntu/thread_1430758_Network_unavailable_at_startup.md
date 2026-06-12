---
title: "Network unavailable at startup"
date: 2010-03-15
forum: Mythbuntu
---

### Post by 4dognight on 2010-03-15
When I start my FE, the network isnt available soon enough. This causes the FE to think there is no backend. Is there some way to delay the FE from starting or have it wait until the network is up?

---

### Post by iitywygms on 2010-03-15
[http://ubuntuforums.org/showthread.php?t=1310458](http://ubuntuforums.org/showthread.php?t=1310458)
Maybe help?

---

### Post by 4dognight on 2010-03-15
Hmm, Well In my case, I only have a frontend. That post was dealing with a BE. I do know that the FE is part of the XFCE autostart. I can pull up the config screen for it, and I do see both the network manager and mythfrontend in there. What order do the apps get started? I dont see of anyway to have it start the network manager before the FE.

I suppose I could modify the startup script for the FE, to wait until the network is up. Seems a bit clunky though, to have to resort to that.

---

### Post by Chris Musampa on 2010-03-15
I used to have the same problem with a previous release (8.10 I think) on my upstairs wireless FE, installing WICD solved the problem, I think it fires up the network before login.

---

### Post by 4dognight on 2010-03-15
well i installed wicd and it still does it. :frown:

---

### Post by nickrout on 2010-03-15
> **4dognight said:**
> well i installed wicd and it still does it. :frown:

enable your networking in /etc/network/interfaces to add this sort of thing (obviously your details will vary from mine)

```
auto eth0
iface eth0 inet static
        address 192.168.1.11
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1

```

---

### Post by 4dognight on 2010-03-16
Ok, after 2 reboots it is working properly. Keep my fingers crossed.
Thanks

---

