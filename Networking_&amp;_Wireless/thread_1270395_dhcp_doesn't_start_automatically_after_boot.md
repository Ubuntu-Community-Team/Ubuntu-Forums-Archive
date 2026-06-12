---
title: "dhcp doesn't start automatically after boot"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by Dosshell on 2009-09-19
I have an ubunto system wich works as a NAT. The problem is that the DHCP3-server doesn't start automatically when the system starts. If i execute "sudo /etc/init.d/dhcp3-server start" everything works great! How can i get the dhcp to auto start so i don't have to start it manually after each boot?

---

### Post by falconindy on 2009-09-19
Add it as a service which will start on boot.
```
sudo update-rc.d dhcp3-server defaults
```

---

### Post by Dosshell on 2009-09-19
It sas:
```
System startup links for /etc/init.d/dhcp3-server already exist.
```But still, it doesn't start.

EDIT:
I added
```
auto eth1
iface eth1 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        broadcast 192.168.0.0
        network 192.168.0.0
```
to "/etc/network/interfaces"

The DHCP starts fine now, but my eth0 (Internet) connection does not get any ip-addres. eth0 disappears from "System->Preferences->Network connections" also. Can it be that dhcp3-server starts before any connections gets there addreses and there for fails on boot?

How can i change so that dhcp3-server starts after my connections are ready || How can i fix my eth0 connection ?

---

### Post by falconindy on 2009-09-19
You probably want to sift through `dmesg` after a boot to see if there's any reason the dhcp server didn't start, then.

---

### Post by Dosshell on 2009-09-19
i ran "dmesg > k" and reed the k file.
I have no clue what to look for. All i could understand was it detected my networkcards correct, loaded profile "/usr/lib/NetworkManager/nm-dhcp-client.action", "/usr/sbin/dhcpd3" and last issued "warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)".

I hope this helps someone to help me.

---

### Post by falconindy on 2009-09-19
That's not useful at all... is there a log generated in /var/log/ ?

---

### Post by Dosshell on 2009-09-19
I added:
```
auto eth0
iface eth0 inet dhcp
``` to the "/etc/network/interfaces" and now everything works nice. Thanks for the help.

---

### Post by falconindy on 2009-09-19
Not that I really helped much... glad it's sorted.

---

