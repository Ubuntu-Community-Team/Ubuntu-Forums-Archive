---
title: "Set primary ip?"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by sammex on 2009-02-01
hi, tried to search for this but haven't found anything.

I got a ubuntu server acting as dhcp, firewall and router for my network. It got two network interfaces, eth1 and eth2. When i reboot it i cant access Internet from any of the computers in my network. I have to disable and re-enable the internal nic to make it work. I am no expert on the subject :P but i believe this is because the internal nic is the "primary" interface and when i disable it i make the external nic "primary".

This haven't been a problem in the past since rarely reboot it but now when i try to set up a voice chatter server it only listens on the internal ip. This means that no one outside my lan can connect to it, which is really irritating.

Any ideas?

---

### Post by Iowan on 2009-02-01
What's in */etc/network/interfaces*?
(And what happened to eth0?)
**ifconfig -a** after reboot should show which interface gets what address.  Again after your trick might show what changes.

---

### Post by sammex on 2009-02-01
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

#auto eth3
#iface eth3 inet dhcp

auto eth1
iface eth1 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        up /root/scripts/azer-fw.sh

```

I don't use eth0 and eth3. the script is my iptables.

eth2 gets ip from my isp's dhcp and eth1 is static since its the gateway in my internal netowork. I must be some setting about what interface to use for accessing the internet, right?

---

### Post by Iowan on 2009-02-01
There is a  file that sets aliases between cards and addresses - */etc/udev/rules.d/70-persistent-net.rules.*  I don't know if you might be able to manually edit which card gets which alias...

---

