---
title: "Cannot add torrents thru Transmission-daemon webUI"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by antiartist on 2011-08-01
[FONT=Courier New]Running Transmission-Daemon on headless server (Ubuntu Lucid 10.04.2 LTS) with  Transmission-Daemon 1.93, which is the most current version for Lucid ([http://packages.ubuntu.com/search?keywo ... ection=all]("http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=all&section=all")).  It should also be noted that I  am running Java 6 (1.6.0_26-b03).
 
Using any torrent URL to add the torrent through the WebUI, the torrent does not show up and as far as I can tell, nothing is downloading.  For sake of example, this torrent ([http://www.osst.co.uk/Download/DamnSmallLinux/current/dsl-4.4.10.iso.torrent](http://www.osst.co.uk/Download/DamnSmallLinux/current/dsl-4.4.10.iso.torrent)) has been confirmed working but I am unable to add it manually through Transmission webUI (clutch).

Have restarted the transmission-daemon service several times.
Have refreshed the webUI page and restarted Java.

Looking thru the syslog, the failed attempts to add a torrent don't seem to generate an entry.  I did notice that whenever I start the transmission-daemon service, an entry shows up in the syslog: 
```
tranmission-daemon requiring authentication
```but since I am able to log into the webUI without issue, I'm assuming this entry is not related to my issue.

I'm not sure what else to put here that might be relevant...

Any help would be appreciated![/FONT]

---

