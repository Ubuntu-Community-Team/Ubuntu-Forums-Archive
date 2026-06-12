---
title: "network manager vpnc/static ip questions"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by asv on 2006-06-01
Can anyone point to me to a deb or repo for the vpnc addon to the official ubuntu network manager package? Also, does anyone know a quick and easy way to handle a static ip connection? 

Thanks!

---

### Post by coldrick on 2006-06-01
It's in the repos - universe or multiverse, forget which

Edit: Sorry, I thought you meant vpnc itself. A quick google turns up [http://revu.tauware.de/details.py?upid=2283](http://revu.tauware.de/details.py?upid=2283)

---

### Post by asv on 2006-06-01
Yeah, thats the cvs version of 0.5.9, what I'm looking for is a standalone plugin that will be compatible with the 0.6.2 available in the repo. 

[QUOTE=coldrick]It's in the repos - universe or multiverse, forget which

Edit: Sorry, I thought you meant vpnc itself. A quick google turns up [http://revu.tauware.de/details.py?upid=2283](http://revu.tauware.de/details.py?upid=2283)[/QUOTE]

---

### Post by Belibem on 2006-06-02
[QUOTE=asv]C Also, does anyone know a quick and easy way to handle a static ip connection? 

[/QUOTE]
route command is fairly easy to use:
route add {-host|-net} [netmask N]  [gw Gw] 
if you want more specific info, specify excactly the route that you need.

---

### Post by asv on 2006-06-02
[QUOTE=Belibem]route command is fairly easy to use:
route add {-host|-net} [netmask N]  [gw Gw] 
if you want more specific info, specify excactly the route that you need.[/QUOTE]

I'm well aware of how to set the interface on the command line, but I was wondering if there is any plugin or plans for how network-manager will handle static ips?

---

### Post by Simian on 2006-06-04
[QUOTE=Belibem]route command is fairly easy to use:
route add {-host|-net} [netmask N]  [gw Gw] 
if you want more specific info, specify excactly the route that you need.[/QUOTE]

Could you please type an example with actual data?
I find it so much easier to follow. Thanks

---

