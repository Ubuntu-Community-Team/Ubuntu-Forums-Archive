---
title: "Does Ubuntu have network security profiles?"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by ethanay on 2009-11-10
For Ubuntu 9.10 Karmic Koala on my laptop:

I am wondering how I can set up "security profiles" to easily switch between different levels of network security depending on my location.

For example, when on my "home network" or another "trusted network" I can share my entire home folder as everything I trust is hidden behind a firewall.  However, when I am on a coffee shop network, airport or other "untrusted network," I do not want to share my files or my computer presence with anyone else.

Is it possible to create different security profiles that allows easy me to choose the level of security appropriate for the network I am on?

---

### Post by doas777 on 2009-11-10
well, what you are describing seems to focus on firewalling. no, I don't really know of any firewall gui's that would support profiles, but I wonder if you need them. forgive me if I presume too much.

ubuntu by default exposes no open ports to the network. generally speaking, if you don;t have any network services installed you don't need a firewall at all. even if they ping your ports, theres nothing listening. do you have any services installed/enabled? (vnc/remote desktop, samba, ssh, http, etc)?

the firewall itself (IP tables) can be configured to apply differant rules to differant networks, so theoretically you could create configurations for networks you are commonly on (and allow service ports only to specific networks, like your home). I'm just not sure how it woudl react when your network is not present.

---

### Post by ethanay on 2009-11-23
How do you protect a laptop that has filesharing enabled and is on an unprotected or public wireless network?

---

