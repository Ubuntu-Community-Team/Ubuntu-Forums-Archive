---
title: "Wireless not responding after dead battery shut off"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by something_clever on 2010-10-19
system: hp pavilion dv7 running ubuntu 10.04

Today my laptop battery died and after i plugged it in and restarted it said that networking was not enabled. hitting the networking key didn't re-enable it. i right clicked the wireless icon in the tray and clicked "enable networking" and it enabled it but no networks showed up as available and the networking status light on my keyboard stayed red. I've restarted the computer several times to no avail. anyone know what i need to do?

ps, this is being posted from a hardwired desktop.

---

### Post by Iowan on 2010-10-20
A couple of threads to check:
[http://ubuntuforums.org/showthread.php?t=1484913]("http://ubuntuforums.org/showthread.php?t=1484913")
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")

 Also, Right-click Network Manager and verify Networking (and wireless) are enabled.

---

### Post by something_clever on 2010-10-20
i looked at those threads and i hardwired my laptop with an ethernet cable and started trying to make stuff work and i think my problem may be that my laptop is no longer reading my wireless card. i open /var/lib/NetworkManager/NetworkManager.state and it reads as

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true

when i rewrite WirelessEnabled=false as WirelessEnabled=true and save and restart it goes right back to being value false. also when i right click on my network manager icon "enable wireless" is blacked out and i cant click on it. this make me think that for some reason my wireless card isnt registering anymore.

---

