---
title: "Strange Hamachi Problem"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by computer13137 on 2010-04-22
I am having an odd problem using Hamachi on Ubuntu.  I've tried it on Ubuntu 9.10 both x86 and x64.  They both do exactly the same odd thing.

[http://www.supware.net/HamachiUbuntuHowto/](http://www.supware.net/HamachiUbuntuHowto/)

I followed that quick guide, and everything worked as expected.  For about, 30 seconds.  After like 30 seconds, the VPN will disconnect.  I then have to stop and restart Hamachi, and it will work for another 30 seconds or so.  It happens every single time. The only solution I've found is to run a constant ping to an IP of another system on the VPN.  This keeps the VPN link active, and for some reason prevents it from caving in on itself. 

Does anyone else here know of a better solution?

(I know this is kind of a weird time to ask with 10.04 around  the corner... but I'm hoping the upgrade to that won't break my Hamachi configuration).

Cheers,
Kirk

---

### Post by byStanderone on 2010-04-23
...open your firestarter window, if you have it installed and focus on events, there might be a port/ip that is being block by the firewall.

---

### Post by computer13137 on 2010-04-23
> **byStanderone said:**
> ...open your firestarter window, if you have it installed and focus on events, there might be a port/ip that is being block by the firewall.

I'm not sure what you're referring to by "firestarter" window.  I am simply using the "hamachi" command line utility.

Also, this server is connected directly to the Internet.  It's in a small office, and is configured to be the router (iptables and a dhcp server) for the office computers.  It has no firewall, I have ufw turned off at the moment.

Kirk

---

### Post by byStanderone on 2010-04-24
firestarter is the 'gui' for configuring ubuntu'firewall (ufw)...it is a good practice to have a firewall installed..i suggest that you install firestarter...well aren't you using any firewall at all?

---

### Post by byStanderone on 2010-04-24
oh....i see, the firewall then is on the router itself, check on it and find out if one of the ports that hamachi uses is blocked....

---

### Post by geofurtado on 2010-04-26
You need to use the "old" hamachi software ([http://files.hamachi.cc/linux/](http://files.hamachi.cc/linux/)).  The new software does not yet work in Linux.

---

