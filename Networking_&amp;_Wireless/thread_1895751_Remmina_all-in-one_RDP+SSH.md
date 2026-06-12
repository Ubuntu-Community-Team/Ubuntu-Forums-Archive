---
title: "Remmina all-in-one RDP+SSH"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by dennis1200 on 2011-12-15
Since you should never do straight RDP for security reasons, I'm trying to figure out how to configure Remmina to combine RDP with an SSH tunnel. I'm currently combining putty for the tunnel and remmina for the rdp. Here's my setup:
Ubuntu 11.10 accessing remote XP computer
Remote computer IP linked to DynDNS address (name:XXXX)
Remote router forwards port DynDNS:XXXX to remote-computer:ZZZZ
Putty connects to SSH at DynDNS:XXXX and forwards localhost:YYYY to remote-computer:ZZZZ - the latter part of this is the step I'm having most trouble with
SSH is authenticated with a password-protected key file pair - also having trouble with this in Remmina, but that may be the previous step

localhost:YYYY needs to be mapped to remote:ZZZZ, but I don't see how to do that in Remmina. It's nowhere near as configurable as putty, but this seems like a key part of SSH configuration. Any help is appreciated, since one tool would be nicer that two.

---

