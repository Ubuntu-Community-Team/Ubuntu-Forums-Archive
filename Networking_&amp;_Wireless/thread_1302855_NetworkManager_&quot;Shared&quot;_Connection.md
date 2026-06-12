---
title: "NetworkManager &quot;Shared&quot; Connection"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by MrFSL on 2009-10-27
Ubuntu Jaunty with gnome-network-manager.

I have been using the "Shared to other computer" setting to share a network connection between two machines. This settting assigns an IP address to my network interface (eth0) and then starts a DHCP service on that interface. 

My issue is that it assigns 10.42.43.1 to eth0 and assigns IP addresses via DHCP in the 10.42.43.0/24 range. I would like to modify these default settings.

For instance, can someone explain to me how to change the defaults so that 192.168.0.1 is assigned to eth0 with the DHCP service providing addresses is the 192.168.0.0/24 range?

Thanks.

---

### Post by MrFSL on 2009-10-27
To answer my own question - a grep of the network-manager source leads me to believe that the 10.42.43.1 IP is hard-set.

A work around is to set the interface with a static IP, then configure dnsmasq and iptables accordingly. Since I have been using the built in "Shared" setting perhaps the following grep output of daemon.log might be helpful to someone in the future:
```
> Oct 27 12:14:08 worktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT 
> Oct 27 12:14:08 worktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --jump REJECT 
> Oct 27 12:14:08 worktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT 
> Oct 27 12:14:08 worktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --out-interface eth0 --jump REJECT 
> Oct 27 12:14:08 worktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT 
> Oct 27 12:14:08 worktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT 
> Oct 27 12:14:08 worktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT 
> Oct 27 12:14:08 worktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT 
> Oct 27 12:14:08 worktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT 
> Oct 27 12:14:08 worktop NetworkManager: <info>  Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE 

```

```
Oct 27 11:13:26 worktop NetworkManager: <debug> [1256670806.509271] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --no-poll --except-interface=lo --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid 
```

If any Network Manager devs read this post - I really believe that this should be a configurable setting. - Automatic, or Manual - Manual set interface IP and DHCP range.

Thoughts?

---

### Post by MrFSL on 2009-10-27
Well here is my solution. (See attached Start and Stop scripts).

I ran tail on /var/log/daemon.log and copied the iptable and dnsmasq settings. This works for me but obviously I wish it were a more elegant solution.

Hope this helps someone else.

---

### Post by jpthompson23 on 2013-01-10
I can't believe it.  This was 2009, and the source code still hasn't changed.  The address is still hard coded.  What moron hard-coded this parameter that should obviously be left for the user to edit?

---

