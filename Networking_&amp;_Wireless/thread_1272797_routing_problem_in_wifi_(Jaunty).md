---
title: "routing problem in wifi (Jaunty)"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by Pollywoggy on 2009-09-22
I have a HP 2133 Mini-Note and I had wifi working until I reinstalled Ubuntu (Jaunty).

Wired networking is working but although I can connect wirelessly, it appears I have a routing problem because I am unable to browse anything other than the server that is on the same network as the wireless router.

How can I fix this routing problem, if that is what it is?


thanks

---

### Post by Iowan on 2009-09-22
Getting IP address via DHCP? What is in */etc/route* and */etc/resolv.conf*?

---

### Post by Pollywoggy on 2009-09-22
> **Iowan said:**
> Getting IP address via DHCP? What is in */etc/route* and */etc/resolv.conf*?

I have a static IP address when using a wired connection but I use DHCP for wifi.

I forgot to check /etc/route but /sbin/route showed two routes as the default route.  At the moment it looks like this but I am now on a wired network:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

When I was connected to the wifi network, there was another line in addition to the above, something like this:

default         10.0.0.1     0.0.0.0         UG    100    0        0 eth1

The IP address was as shown above at one wifi network and at another (a university), the address was a routable address on the university's network.


Because of this (because two default routes were shown), I think perhaps what I need to do before I start the wifi connection is 'sudo ifdown eth0' but I did not need to do that before reinstalling Ubuntu.  Something was taking care of it for me, apparently.

This is what /etc/network/interfaces has:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.25
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1
        dns-search mydomain.com


/etc/resolv.conf is interesting.  When I connect to wifi, network manager replaces the "wired" version of the file with something that looks like this:

nameserver 123.456.67.89


and another line, pointing to the host domain
search somedomain.com

The nameserver IP address that appears (as above) is an address on the wifi network.
BTW, I have bind9 installed on my netbook.  I would like to use the nameserver on the laptop, if possible.


I do not have the resolvconf package installed but when I was a Debian user, this package would cause problems of this type and I would remove it.  The default install in Jaunty did not install the resolvconf package.

---

### Post by Iowan on 2009-09-22
You *should* be able to use the "prepend" line in */etc/dhcp3/dhclient.conf* to put your choice nameserver at the top of the list. [Here]("http://ubuntuforums.org/showthread.php?t=971064") is a thread that... well, hopefully doesn't apply.

---

### Post by Pollywoggy on 2009-09-22
> **Iowan said:**
> You *should* be able to use the "prepend" line in */etc/dhcp3/dhclient.conf* to put your choice nameserver at the top of the list. [Here]("http://ubuntuforums.org/showthread.php?t=971064") is a thread that... well, hopefully doesn't apply.

Thanks, I will try that.  I went back to the university to try again (it is a short walk) and I was able to connect and use my web browser.  Before connecting to the wireless network, I did "sudo ifdown eth0" and this worked.  Something was taking care of this before I reinstalled Ubuntu, but I will need to do it manually now.

The university apparently blocks many outgoing ports, so if I want to connect to my home machine via ssh, I would have to employ a trick, such as setting my SSH port as port 80.
I don't want to do that.  At least I can surf the web from the library now.

---

### Post by Pollywoggy on 2009-09-22
> **Iowan said:**
> You *should* be able to use the "prepend" line in */etc/dhcp3/dhclient.conf* to put your choice nameserver at the top of the list. [Here]("http://ubuntuforums.org/showthread.php?t=971064") is a thread that... well, hopefully doesn't apply.

As for the second part of your answer, I do not have that problem.  That seems like what the resolvconf package would do in Debian and I would therefore remove that package whenever I did a new Debian install.  Resolvconf had its own ideas about what nameservers I should use.

---

