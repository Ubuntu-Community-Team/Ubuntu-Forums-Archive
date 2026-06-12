---
title: "Network Manager not Running at Boot"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by Gogsyd on 2012-12-30
Hi,

Network Manager does not seem to want to start automatically when the system boots up and I have to type in 

```
sudo service network-manager start
```

to get any network connectivity.  Having a quick search round I see mention of upstart jobs and init.d and rc.local but to be honest as I'm just starting to delve into the world of Linux it's a bit double-dutch to me.

Any ideas where to go?  Simple terms appreciated lol

Thanks

---

### Post by Andy45 on 2012-12-30
[LIST=1]
[*]Open a terminal and type in "sudo su" to switch to root
[*]Type in "nano /etc/rc.local"
[*]In the line between the last comment and the word 'exit', type in "service network-manager start".
[/LIST]
Whenver you want a command to be run at boot, add it to /etc/rc.local, as the contents of this file are executed at boot. By default it does nothing.

---

### Post by Gogsyd on 2012-12-30
Hi Andy, thanks for that it seems to have done the trick.  I notice on the splash screen (and this was happening before) that it says "waiting for network connection/configuration (not sure which)" and then says "waiting up to 60 seconds for network connection".  Is this normal until the command kicks in from rc.local? Just seems odd that it delays the boot process.
Thanks again

---

### Post by Dennis N on 2012-12-30
> **Gogsyd said:**
> I notice on the splash screen (and this was happening before) that it says "waiting for network connection/configuration (not sure which)" and then says "waiting up to 60 seconds for network connection".  Is this normal until the command kicks in from rc.local? Just seems odd that it delays the boot process.
Thanks again

Lubuntu 12.10 - same issue: "waiting up to 60 seconds for network connection.." message. This noticed after installing with the alternate installer (but not the regular installer - that may be just a coincidence). 

One or the other of the following fixed that (also a connection that was dropping repeatedly).

1) look at /etc/network/interfaces. it was misconfigured. It should look like this:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

If there are more lines, comment them out with a # in front.

2) [B]Main Menu > Preferences > Network Connections > Select connection > 
Edit[/B]
ipv6 settings: set method to Ignore and "available for all users" checked at the bottom of window.

After that, no problems. Maybe it will help you.

Good Luck

---

### Post by Gogsyd on 2012-12-31
Hi Dennis,  That worked a treat thanks.  For the record I ended up having to do both but it worked fine.

Thanks again to you both.

---

