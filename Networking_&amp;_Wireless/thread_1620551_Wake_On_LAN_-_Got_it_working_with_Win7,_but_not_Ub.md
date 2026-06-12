---
title: "Wake On LAN - Got it working with Win7, but not Ubuntu"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by kimalekst on 2010-11-13
I want to enable WOL, keep the NIC active, when i power off from ubuntu.

I've been sifting through a lot of forum posts (Googled) that all say the same thing. Basically "ethtool -s eth0 wol g".

What I've done:
run the command in the terminal
added it to /etc/rc.local

Result:
Now the status led on the router doesn't turn off (when the computer does).
But WOL still won't work.

Been using dd-wrt router firmware to power on my computer for a long time. And it still works, when i power off from windows. So it's got to be possible from Ubuntu as well.

---

