---
title: "eth0:0 in /etc/network/interfaces doesn't come up on reboot."
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by awclemen on 2009-09-15
I'm running Ubuntu 9.0.4 server on a Dell 2650.  I wanted to add another IP address to my ethernet port, so I edited /etc/network/interfaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.2.0.103
        netmask 255.255.255.0
        network 10.2.0.0
        broadcast 10.2.0.255
        gateway 10.2.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.2.0.110 10.10.12.110 10.10.12.111
        dns-search XXXXX.com

auto eth0:0
iface eth0:0 inet static
      address 10.2.0.184
      netmask 255.255.255.0
      network 10.2.0.0
      broadcast 10.2.0.255

```

ran /etc/init.d/networking restart and eth0:0 comes up and is working.  If I reboot the machine, eth0:0 does not show up until I rerun /etc/init.d/networking restart.

What am I missing?  Do I need to run something else?

Thanks in advance,

--Andy

---

### Post by Iowan on 2009-09-15
Try using **eth0:1** instead.

---

### Post by awclemen on 2009-09-15
Thanks for your reply Iowan.  I had to reboot twice (for some reason) but they came up on the second reboot. Kudos!

---

### Post by Iowan on 2009-09-15
I don't claim to understand aliases... why do you need an alias in the same subnet? Does it work if you switch eth0:1 network to 10.2.1.0 (address:10.2.1.184, broadcast: 10.2.1.255)?


[edit] well... nevermind.

---

### Post by awclemen on 2009-09-18
I was still having problems with this in my Dell Optiplex Desktop GX620 - but finally found a solution.  Appearantly if you remove the wireless-tools file from /etc/network/if-pre-up.d directory - the eth0:1 will come up on reboot.

[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/123773](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/123773)
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/114457](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/114457)

---

