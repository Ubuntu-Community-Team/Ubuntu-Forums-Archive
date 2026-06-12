---
title: "Accept Remote Connections in Services API"
date: 2014-05-04
forum: Mythbuntu
---

### Post by sixy on 2014-05-04
Hello! I'm running Mythbuntu 12.04 and trying to set up the MythRecordings plugin for Plex which is on a different machine. It seems that my Services API refuses all connections  unless I point the browser to 127.0.0.1:6544 from that machine. How can I make it listen for connections from a remote machine?

---

### Post by sixy on 2014-05-04
Nevermind, I figured it out!

If anyone else runs into this, I had the backend IP set to 127.0.0.1. 

From [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#General:](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#General:)
Enter the IP address of this (backend) machine. Use an externally accessible address if you are going to be running a frontend or Slave Backend on a different machine than this one. (ie, not 127.0.0.1)

---

