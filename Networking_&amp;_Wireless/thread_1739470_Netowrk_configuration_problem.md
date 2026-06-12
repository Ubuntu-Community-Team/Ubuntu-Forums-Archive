---
title: "Netowrk configuration problem"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by MichaelVaknine on 2011-04-26
hi,

I have a weird problem with networking
i have a UBUNTU 10.04 server configured as static address but every 4 days (which is probably the lease time on my DHCP the computer gets a DHCP address.
when i execute /etc/init.d/netowrking restart it gets his original IP.
i would appreciate any help 
this is my interfaces file content

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
      address 192.168.80.23
      network 192.168.80.0
      netmask 255.255.255.0
      broadcast 192.168.80.255
      gateway 192.168.80.254


Thanks
Michael

---

### Post by Charlietje on 2011-04-26
Hi,

Are you using a headless server, or is it a desktop installation you are using as server?

If it is a desktop installation, you could try to uninstall or disable the gnome NetworkManager

to disable:
```
sudo update-rc.d NetworkManager remove
```

to remove
```
sudo apt-get remove network-manager
```

---

### Post by MichaelVaknine on 2011-04-26
Hi Charlie,

It is a server instalation not desktop.
I tried and network-manager is not installed
I cant find NetworkManager in /etc/init.d/

thnaks
Michael

---

### Post by Charlietje on 2011-04-26
do you have a dhclient running?

you can check with: ps aux

---

### Post by MichaelVaknine on 2011-04-26
hi,

I have dhclient3 running
do you know which package should i remove?

Thanks
Michael

---

### Post by Charlietje on 2011-04-26
you can remove it by:

```
apt-get remove dhcp3-common dhcp3-client 
```

---

### Post by MichaelVaknine on 2011-04-26
thank you Charlie,

I removed the packages and killed the running proccess.
I hope the problem is solved now, will found out in 3 days.

Michael

---

### Post by lz1dsb on 2011-04-26
That's rather interesting problem. The lease time for the DHCP servers is usually something like 24 hours. You could check if you have something in the following forlder:
```
/var/lib/dhcp3
```If you have some files there, each of them is showing the DHCP lease paramethers which are shown there. Here's an example of what I have on my machine:
```
@ubuntu:/var/lib/dhcp3$ ls
dhclient-34486f55-d189-4f88-bdcb-b650042d69fb-eth0.lease
dhclient-4120802d-bcde-46a1-8ad3-c852b6030955-eth0.lease
dhclient-541d83e8-bb51-479d-9bd7-3465f68ef96b-eth0.lease
dhclient-5e864b92-8510-4b7b-bd3f-97282871bf3b-eth0.lease
dhclient-75689376-d332-444a-b3f8-c0d4a5c1ec59-eth0.lease
dhclient-9743cf6d-8da4-4940-8cc1-5b755e358489-eth0.lease
dhclient-b7e91111-2120-45a3-be81-efcd5770a140-eth0.lease
dhclient-b944d41e-ea18-4530-9280-eb4f9cd34854-eth0.lease
dhclient-c50026a0-df8d-4e9c-b187-3c44aede7e1e-eth0.lease
dhclient-cdae2ac2-b637-41e8-9226-f754bd601953-eth0.lease
dhclient-e21137bd-d043-4f50-8910-cc8f4a22405a-eth0.lease
dhclient-e5f34a49-5fc5-4603-9274-b4aa96e6bae0-eth0.lease
dhclient.leases
@ubuntu:/var/lib/dhcp3$ cat dhclient-34486f55-d189-4f88-bdcb-b650042d69fb-eth0.lease 
lease {
  interface "eth0";
  fixed-address 192.168.1.11;
  option subnet-mask 255.255.255.224;
  option routers 192.168.1.1;
  option dhcp-lease-time 86400;
  option dhcp-message-type 5;
  option domain-name-servers 212.50.10.50;
  option dhcp-server-identifier 192.168.1.1;
  option broadcast-address 192.168.1.31;
  option domain-name "sotirov-bg.net";
  renew 6 2011/04/23 23:26:49;
  rebind 0 2011/04/24 09:31:15;
  expire 0 2011/04/24 12:31:15;
}
@ubuntu:/var/lib/dhcp3$ 
```

---

