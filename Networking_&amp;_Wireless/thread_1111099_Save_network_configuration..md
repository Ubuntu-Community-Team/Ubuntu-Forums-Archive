---
title: "Save network configuration."
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by muxecoid on 2009-03-30
Hello. I used the newbie-friendly GUI network manager to configure eth0 to use local network with static pre-set IP. After every reset it goes back to auto DHCP which is undesirable. Also I want it to be active even when I start the system without X. Where do I put the configuration? Where does GUI network manager takes data from?

---

### Post by Iowan on 2009-03-30
Network Manager stores its settings in */etc/NetworkManager/nm-system-settings.conf *. Static addresses have been a problem (dunno if it's been fixed). I listed a few How-To's [here]("http://ubuntuforums.org/showthread.php?t=1110384").

---

