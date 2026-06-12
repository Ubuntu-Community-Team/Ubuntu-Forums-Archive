---
title: "Static IP keeps trying to switch back to DHCP?"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by victorhooi on 2011-12-21
Hi,

I've just installed Ubuntu Server 11.10 (AMD64) on a VMWare host.

I've setup static networking on the box, by editing /etc/network/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 10.180.3.6
netmask 255.255.255.0
gateway 10.180.3.250

```

When the machine starts up, it's fine, and has the static address (10.180.3.6). However after a period, it seems to revert back to a IP address in the DHCP range. I haven't measured how long it takes, but it "seems" to be a random thing.

Is there any reason it might be switching from static to DHCP like that all of a sudden?

Cheers,
Victor

---

### Post by chili555 on 2011-12-21
What do the system logs have to say?```
sudo cat /var/log/syslog | grep -e etwork -e eth0
```Thanks.

---

### Post by victorhooi on 2011-12-21
heya,

Hmm, there are some messages about DHCP in syslog:

[https://gist.github.com/1508808](https://gist.github.com/1508808)

Does that help at all?

Cheers,
Victor

---

### Post by Thylex on 2011-12-22
At a guess you have setups for eth0 both in the interfaces file and in Network Manager, and NM is setup to use DHCP via "Auto eth0" or something like that. If you are going to use static configs on the host I would strongly suggest to remove NM completely.

---

### Post by chili555 on 2011-12-22
> At a guess you have setups for eth0 both in the interfaces file and in Network Manager, and NM is setup to use DHCPThat was my suspicion, as well, however:> DHCPREQUEST of 10.180.3.220 on eth0 to 10.180.64.5 port 67
Dec 22 08:30:02 null-000c2997e7a1z dhclient: [COLOR="Red"]DHCPACK of 10.180.3.220 from 10.180.64.5[/COLOR]
Dec 22 08:30:02 null-000c2997e7a1z dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: No such file or directory
Dec 22 08:30:02 null-000c2997e7a1z dhclient: bound to 10.180.3.220 -- renewal in 3378 seconds.That suggests that the gateway address is actually 10.180.[COLOR="Red"]64.5[/COLOR] and not 10.180.[COLOR="Red"]3.250[/COLOR] as in the interfaces file. I'd think your interfaces file should be more like:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 10.180.[COLOR="Red"]64.6[/COLOR]
netmask 255.255.255.0
gateway [COLOR="Red"]10.180.64.5[/COLOR]
```

---

### Post by victorhooi on 2011-12-22
Hi,

@Thylex: This is Ubuntu 11.10 server - I don't have Xorg or any GUIs installed, and I assume NetworkManager isn't setup by default on server?

@chili555: I've just checked with our network guys, and they confirm that the static address should be 10.180.3.6, and the gateway for the subnet range should be 10.180.3.250.

Also, when I obtain the address via DHCP (10.180.3.220), that gateway (10.180.3.250) is the one assigned:

```
victorhooi@victor:~/graylog2/graylog2-web-interface$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.180.3.250    0.0.0.0         UG    100    0        0 eth0
10.180.3.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

Cheers,
Victor

---

### Post by chili555 on 2011-12-22
> I've just checked with our network guys,Do they have any idea where 10.180.[COLOR="Red"]64[/COLOR].x is coming from? Do they have an opinion as to whether the subnet is correct?

---

### Post by zerek on 2011-12-23
got exactly the same problem here. Random DHCP Ubuntu 11.10 server

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.100
network 10.0.0.0
broadcast 10.0.0.255
netmask 255.255.255.0
gateway 10.0.0.1

* might have installed WICD earlier for testing a wireless connection, I will doublecheck on that *

---

### Post by Thylex on 2011-12-29
10.180.64.5 is just the IP address of the DHCP server, it's in another subnet and the gateway has IP helpers set up to get requests thru.

I just did a check on a fresh install of 11.10 server, and network manager IS installed by default. Run this command to check:
```

aptitude search 'network-manager'
```Try removing those packages, or find some way of disabling them, maybe disable the start of NM.

---

### Post by victorhooi on 2011-12-29
Hi,

Hmm, I don't seem to have network-manager installed on this sytem - fresh install of 11.10 Server (AMD64):

```
victorhooi@victor:/var/data/elasticsearch$ aptitude search 'network-manager'
p   network-manager                                                                   - network management framework (daemon and userspace tools)                                  
p   network-manager-dbg                                                               - network management framework (debugging symbols)                                           
p   network-manager-dev                                                               - network management framework (development files)                                           
p   network-manager-gnome                                                             - network management framework (GNOME frontend)                                              
p   network-manager-gnome-dbg                                                         - network management framework (debugging symbols)                                           
p   network-manager-kde                                                               - transitional package for plasma-widget-networkmanagement                                   
p   network-manager-openconnect                                                       - network management framework (Openconnect plugin)                                          
p   network-manager-openconnect-gnome                                                 - network management framework (Openconnect plugin, GNOME UI)                                
p   network-manager-openvpn                                                           - network management framework (OpenVPN plugin core)                                         
p   network-manager-openvpn-gnome                                                     - network management framework (OpenVPN plugin GNOME GUI)                                    
p   network-manager-pptp                                                              - network management framework (PPTP plugin core)                                            
p   network-manager-pptp-gnome                                                        - network management framework (PPTP plugin GNOME GUI)                                       
p   network-manager-strongswan                                                        - network management framework (strongSwan plugin)                                           
p   network-manager-vpnc                                                              - network management framework (VPNC plugin core)                                            
p   network-manager-vpnc-gnome                                                        - network management framework (VPNC plugin GNOME GUI)
```
```
victorhooi@victor:/var/data/elasticsearch$ sudo aptitude remove network-manager
[sudo] password for victorhooi: 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```

Any other possibilities on what might be causing this?

Cheers,
Victor

---

### Post by gtr33m on 2012-01-19
I've got exactly the same problem.  Has any solution been found?

Mark

---

### Post by SeijiSensei on 2012-01-20
> Dec 22 08:30:02 null-000c2997e7a1z dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: No such file or directory

Perhaps there's no /var/lib/dhcp3 directory?  If the directory exists, what permissions does it have? Is there already a leases file, and if so, what permissions does it have?

---

### Post by gtr33m on 2012-01-20
I'll check on Monday when I'm back at work, but why would this cause an issue?  The server is not acting as a DHCP server and shouldn't be acting as a DHCP client.  I've got /etc/network/interfaces set as static.

Thanks,

Mark

---

### Post by gtr33m on 2012-01-22
The file exists in /var/lib/dhcp (not dhcp3)

Permissions are:

-rw-r--r--  1 root root    0 2012-01-06 16:08 dhclient.leases

---

### Post by drahst on 2012-02-13
Anything ever found on this issue? I've got a similar situation.

---

### Post by anon0 on 2012-06-19
I have the same issue on 11.10 too. Is this a bug?

Update: I rebooted and it got assigned the static IP again. I'll report back if I get another IP change.

---

### Post by jimmah6786 on 2012-08-28
I can confirm that this is still happening in 12.04 Server.

eth0 set to static, changes around 12:00am every night. No cron jobs, nothing in the logs.

---

### Post by Iowan on 2012-08-28
Is dhclient running on that machine?

---

