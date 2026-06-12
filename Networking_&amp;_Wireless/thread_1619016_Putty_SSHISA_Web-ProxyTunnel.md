---
title: "Putty SSH/ISA Web-Proxy/Tunnel"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by Skavenger0 on 2010-11-11
On my network I'm behind a M$ ISA http proxy server.

On the inside of that proxy server are several linux servers. The one I'm working on now is Ubuntu server for Enterprise Cloud.

After scouring the net and forum for a solution I have found that ISA will not allow apt to get through. I do have a sort of solution which is to run ntlmaps everytime I connect however I want to know if this is possible:

I only need to get through ISA to get apt working when I am logged in.
Is it possible to create a tunnel using putty from my windows machine to the ubuntu server which will send traffic through ISA to the server?

Currently I have tried creating a dynamic tunnel with ISAs IP (lets say 192.168.0.1 for arguments sake) and port 8080.

Then set the apt.conf to [http://usrname:password@127.0.0.1:8080](http://usrname:password@127.0.0.1:8080)

I dont know if i'm going down the right route, but this would be perfect as I could save the settings into putty and automatically have access to the internet when I log in.

Any other suggestions would be appreciated.

---

