---
title: "How find what set ip address for my computer? Static but not in /etc/network/interfac"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by 6tr6tr on 2013-05-21
I have Ubuntu running with a static ip (it's always 192.168.1.103) but I can't figure out where I set that. I looked in /etc/network/interfaces and it's not in there. How do I find where this is set?

When I run "nm-tool" from command line, it shows:

>   IPv4 Settings:
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



But when I run  nm-connection-editor, it shows that same "auto eth0" interface as never used and when I click "edit" under ipv4, it shows it as DHCP (which I know it is not, it is definitely static).

---

### Post by steeldriver on 2013-05-21
Are you sure it's not DHCP but you reserved 192.168.1.103 on your router?

---

### Post by prodigy_ on 2013-05-21
> **6tr6tr said:**
> How do I find where this is set?
```
sudo -i
for path in /etc /var; do grep -R '192\.168\.1\.103' $path; done
```

---

### Post by Bucky Ball on 2013-05-21
Right click network icon, edit connections, click wireless tab, IPv4 setup tab. That's where I set mine on our four machines (make sure the router is not trying to serve an IP via DHCP in that range, naturally).

---

### Post by 6tr6tr on 2013-05-23
> **prodigy_ said:**
> ```
sudo -i
for path in /etc /var; do grep -R '192\.168\.1\.103' $path; done
```

Thanks, I'm getting a lot of lines like:

```
/var/lib/dhcp3/dhclient-70a58dde-82a0-41e6-8a13-5e9bf7bbff6d-eth2.lease:  fixed-address 192.168.1.103;
```

and

```

/var/log/daemon.log.1:May 15 16:55:00 desktop dhclient: DHCPOFFER of 192.168.1.103 from 192.168.1.1
/var/log/daemon.log.1:May 15 16:55:00 desktop dhclient: DHCPREQUEST of 192.168.1.103 on eth2 to 255.255.255.255 port 67
/var/log/daemon.log.1:May 15 16:55:00 desktop dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
/var/log/daemon.log.1:May 15 16:55:00 desktop NetworkManager: <info>    address 192.168.1.103
/var/log/daemon.log.1:May 15 16:55:00 desktop avahi-daemon[581]: Joining mDNS multicast group on interface eth2.IPv4 with address 192.168.1.103.


/var/log/daemon.log:May 22 17:54:26 desktop avahi-daemon[584]: Registering new address record for 192.168.1.103 on eth2.IPv4.
/var/log/daemon.log:May 22 17:54:26 desktop dhclient: bound to 192.168.1.103 -- renewal in 36784 seconds.
/var/log/daemon.log:May 23 01:50:39 desktop dhclient: DHCPREQUEST of 192.168.1.103 on eth2 to 255.255.255.255 port 67
/var/log/daemon.log:May 23 01:50:39 desktop dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
/var/log/daemon.log:May 23 01:50:39 desktop NetworkManager: <info>    address 192.168.1.103
/var/log/daemon.log:May 23 01:50:39 desktop avahi-daemon[595]: Joining mDNS multicast group on interface eth2.IPv4 with address 192.168.1.103.


```

What does this mean?

---

### Post by steeldriver on 2013-05-23
It looks like you *are* using DHCP, and the DHCP server in your router (192.168.1.1) is giving you 192.168.1.103

That may be just because the router remembers what address the client had before and has no reason to change it (my Netgear router seems to do that) or you may actually made an 'address reservation' where you tell the router to always hand out that address when it receives a lease request from that client (based on its interface's MAC address).

FWIW since you are using NetworkManager you can also get DHCP info using the nmcli command (at least with newer versions of the network-manager package)

```
nmcli dev list | grep DHCP
```

---

