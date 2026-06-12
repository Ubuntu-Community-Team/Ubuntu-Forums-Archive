---
title: "Remote debugger connection refused"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by awp2513_ on 2010-12-21
Hi,

I am trying to attach a remote debugger from a Windows machine to an Ubuntu 10.04 Netbook Remix VM (I want to debug the code running on the VM from Windows). Several posts suggested the solution was to run the application using the following:

```
java -jar -Xdebug -Xrunjdwp:transport=dt_socket,address=8001,server=y,suspend=y my.jar
```My development environment is Netbeans 6.7.1, and when I attempt to attach the debugger i get "Connection refused". It sounds as though this is on the Ubuntu end of things (although could be wrong). I was wondering if there are security settings I'm not aware of (I'm not at all familiar with Ubuntu's firewall, security, etc. settings).

I have tried a variety of other ports with the same result. Maybe there's a range I have to hit?

Any help would be appreciated.

---

### Post by awp2513_ on 2010-12-21
It ended up being an issue with my VM settings, not with Ubuntu. 

When I set up the Network Adapter of the VM, I selected "NAT: Used to share the host's IP address"

I changed this setting to "Bridged: Connected directly to the physical network" and checked the sub-item "Replicate physical network connection state".

The connection is no longer refused.

---

