---
title: "server on S3 standby/hibernate - wake on ping?"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by kacheng on 2009-09-11
bump

originally posted [http://ubuntuforums.org/showthread.php?t=505450]("http://ubuntuforums.org/showthread.php?t=505450")
-----


I've been looking into trying to achieve the following behaviour:

- server running fileshare
- server uses CPU frequency scaling to minimize power usage while running

- server to go to standby(s3)/hibernate mode when not in use to save energy and reduce heat output
- when server is pinged, server should awaken and resume as normal after a short delay, there should be no need for a 'magic packet' as typically required by Wake on LAN (WOL)


I've been able to get WOL functionality working by enabling WOL in the BIOS and that seems to work if I send a 'magic packet' to the MAC address of server to awaken it.

However, I've seen some Windows XP tutorials to enable a 'wake on ping' type functionality that would not require a 'magic packet'. Typically this is chosen in the network card configuration dialog.

Is there a way to do this in Ubuntu?

---

