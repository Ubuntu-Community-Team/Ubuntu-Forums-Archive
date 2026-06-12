---
title: "Cannot config network connection"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by buster.swank on 2009-10-31
I have an old IBM thinkpad T21, 800mhz with 256mb ram that i decided to install Xubuntu 9.10 on. Previously it had XP running. Since changing to Xubuntu the network connection is shot. Xubuntu indicates that there are no network connections and I guess I would have to manually hardcore in some settings in a new wired connection instance? 
 
Ubuntu I've had no problems in the past but I realize Xubuntu is a bit more stripped down, which was the idea with such an old machine. Any suggestions? I'm clueless on this one and don't know where to start. Haven't been able to find any postings on this already using Xubuntu. Could this be related to the version of Xubuntu? 9.10 vs 8.04.1?

---

### Post by Iowan on 2009-10-31
Karmic seems to be having some networking issues - what kind of connection do you have (DSL seems to be a real issue, so far)? I can't remember what Xubuntu used for a network manager (on previous version), or if it uses */etc/network/interfaces*.

---

### Post by nanikore on 2009-11-03
I just clean installed 9.10 and see odd behavior with the wired connection. It works fine out of the box in DHCP, but if I try to set a static IP, it just refuses to take it. Even when I edited the interfaces file directly, it refuses to take it. When I attempted to remove NetworkManager, it allowed it, but (kind of as expected) the networking side started to fall over, despite my (previously known good) interfaces settings. Reboots between settings changes failed to help.

(FWIW, I did alter the authorization to allow me to change network rights)

I'll give it a few weeks to see if it's just my setup, and if so I might shuffle over to Debian 5. No knocks though - I've been a Xubuntu fan since 8.04 and hope to come back, just static IP is a bit of a deal killer for me (as odd as that sounds).

---

### Post by sandman42 on 2009-11-03
> **nanikore said:**
> I just clean installed 9.10 and see odd behavior with the wired connection. It works fine out of the box in DHCP, but if I try to set a static IP, it just refuses to take it.

Basically the same problem here. I've been able to set ip, netmask and gateway, but I can't set in any way DNS, i.e. resolv.conf.

What I actually do is to modify by hand /etc/resolv.conf at any boot, but it's not the correct behavior. IMHO, or network manager works, or I'd been able to remove it an to use the good old /etc/networks/interfaces, /etc/resolv.conf and so on.

Are we going to be worst that windoze with all that gui stuff for click monkeys?

:confused:

---

### Post by Iowan on 2009-11-03
I found [this]("http://ubuntuforums.org/showpost.php?p=8228761&postcount=3") hint to disable NM.

---

