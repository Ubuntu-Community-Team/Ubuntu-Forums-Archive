---
title: "Detect changed IP address"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by DennyBeach on 2011-10-26
I am running Ubuntu 11.10 and need to run a script to update DNS entries whenever my IP address changes. (I am using likewise-open for Active Directory and need to call the lw-update-dns command)
 
I can detect a change via a cron script, but it would be run for no reason many times and then be delayed when the address actually does change.
 
I discovered the /etc/dhcp/dhclient-*-hooks.d folders, but those scripts are only called when someone manually runs the dhclient command, not when the system boots or the interface is restarted.
 
Is there a way to only run a script exactly (or within a few seconds) when the address changes, or is there a better way to accomplish this?
 
Thanks

---

### Post by surfer on 2011-10-26
i use this to configure routes whenever an interface is brought up (i have some "special" network configurations): [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/").

check the passage in the config file on this site around "
# A more complicated ethernet setup, with a less common netmask, and a downright
# weird broadcast address: (the "up" lines are executed verbatim when the
# interface is brought up, the "down" lines when it's brought down)
"

that sounds like you can run pretty much everything whenever the interface is brought up or down.

please report back; i'd be interested if that works.

---

### Post by DennyBeach on 2011-10-26
It looks like the only thing defined in /etc/network/interfaces is the loopback interface. Here are the contents of my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback
```
 
Are the network interfaces created dynamically somehow? If so, is there a way to hook into that method?

---

### Post by surfer on 2011-10-26
on ubuntu-desktop it is the network manager (nm-applet) that takes care of the connections. but you are free to edit /etc/network/interfaces.

---

### Post by DennyBeach on 2011-10-26
Okay, I see it now. When I add the interface config info to /etc/network/interfaces, the NetworkManager gui won't control that interface any more and it releases the interface to the normal system mechanisms.
 
Here is what I did that works now:
 
Added to /etc/network/interfaces:
```
 
auto eth0
iface eth0 inet dhcp

```
 
Created /etc/dhcp/dhclient-exit-hooks.d/likewise-open (and chmod'ed to executable):
```

#
# Update AD/DNS on new DHCP address
#
case $reason in
        BOUND|RENEW|REBIND|REBOOT)
                /usr/bin/lw-update-dns
                ;;
esac

```
 
 
It looks like it would be possible to write a daemon program to listen to dbus signals from the NetworkManager gui, but that sounds like more work than I want to do right now.
 
Thank you for pointing me in the right direction.

---

