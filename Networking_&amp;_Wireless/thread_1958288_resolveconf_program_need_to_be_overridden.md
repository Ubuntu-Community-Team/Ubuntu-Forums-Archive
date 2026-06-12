---
title: "resolveconf program need to be overridden"
date: 2012-04-14
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2012-04-14
The resolvconf program is supposed to take nameserver information from sources like DHCP and make the /etc/resolv.conf file have this.  It's not working because there are no available sources.  There is no DHCP and no PPP logins.  The network is statically configured.  But the /etc/resolv.conf file is being emptied out at boot up time.

Before I take the drastic measure of uninstalling that package, is there another more preferred means to get a statically configured /etc/resolv.conf file?

I know what I can do to tear things out that aren't doing what I want.  But I want to check first before doing that to see if there are better ideas or suggestions, or descriptions of impacts.

---

### Post by papibe on 2012-04-14
Hi Skaperen.

Are you using network-manager to manage your network connection? If so, then I image that those settings are being overwritten after reboot?

or, Did you uninstall network-manager and you are managing your network by editing the necessary files?

Regards.

---

### Post by Skaperen on 2012-04-14
> **papibe said:**
> Hi Skaperen.

Are you using network-manager to manage your network connection? If so, then I image that those settings are being overwritten after reboot?

or, Did you uninstall network-manager and you are managing your network by editing the necessary files?

Regards.
I uninstalled network-manager, edited /etc/network/interfaces, and also added a couple scripts to add more IP addresses without pretending them to be more interfaces (to avoid triggering daemons so many times).

---

### Post by papibe on 2012-04-14
Then you could specify the DNS you want in the /etc/network/interfaces like this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
  address 192.168.1.2
  netmask 255.255.255.0
  gateway 192.168.1.1
**  dns-nameservers 192.168.1.1 8.8.8.8**
```
(as proposed by matt_symes [here]("ubuntuforums.org/showthread.php?t=1948780")).

I hope that helps, and tell us how it goes.
Regards.

---

### Post by Skaperen on 2012-04-15
> **papibe said:**
> Then you could specify the DNS you want in the /etc/network/interfaces like this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
  address 192.168.1.2
  netmask 255.255.255.0
  gateway 192.168.1.1
**  dns-nameservers 192.168.1.1 8.8.8.8**
```(as proposed by matt_symes [here]("http://ubuntuforums.org/showthread.php?t=1948780")).

I hope that helps, and tell us how it goes.
Regards.
How does that work with two or more interfaces?  Do they get merged?  Or each replaces the previous in order?  Or just the first is used?  Or do I just put that info on one of them?

---

### Post by papibe on 2012-04-15
I'm not 100% sure, but as far as I've read, all of them are added to the file /etc/resolv.conf as a 'nameserver' entries.

Regards.

---

### Post by Skaperen on 2012-04-20
> **papibe said:**
> I'm not 100% sure, but as far as I've read, all of them are added to the file /etc/resolv.conf as a 'nameserver' entries.

Regards.
That could make quite a mess.

---

