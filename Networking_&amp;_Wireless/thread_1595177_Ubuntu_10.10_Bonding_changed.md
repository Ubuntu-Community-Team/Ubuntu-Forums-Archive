---
title: "Ubuntu 10.10 Bonding changed?"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by ghettofreeryder on 2010-10-13
I just did a fresh install of Maverick Server.  I installed vlan and ifenslave, and copied my interfaces file over.  However, the config seems to be failing when trying to bring up the bond.

Here is the contents of /etc/network.interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto bond0
iface bond0 inet static
	address 10.0.10.200
	netmask 255.255.255.0
#	gateway 10.0.10.1
	bond-slaves none
	bond-mode 4
	bond-miimon 100

auto eth1
iface eth1 inet manual
	bond-master bond0

auto eth2
iface eth2 inet manual
	bond-master bond0

auto eth3
iface eth3 inet manual
	bond-master bond0

auto eth4
iface eth4 inet manual
	bond-master bond0

auto vlan5
iface vlan5 inet static
	address 10.100.10.254
	netmask 255.255.255.0
	gateway 10.100.10.1
	vlan_raw_device bond0
```

Any ideas?

---

### Post by cake2 on 2010-10-14
I have exactly the same problem.
Loading the module with modprobe and restarting networking only plumb the bond0 interface but the bond module starts in "round-robin" mode.  I can see /proc/net/bonding/bond0 in "round-robin".  In the /etc/network/interface file, I specify "active-backup" (mode 1 don't work neither)...

---

### Post by ElllisD on 2010-10-14
Similar problem here.

This is how I was able to bring up the first bond device.
If that's all you need it should work for you.

etc/network/interfaces
=================
```
auto bond0
iface bond0 inet static
    bond_miimon  100
    bond_mode balance-rr
    address  xxx.xxx.xxx.xxx
    netmask  255.255.255.0
    gateway  xxx.xxx.xxx.xxx
    up /sbin/ifenslave bond0 eth0 eth1
    down /sbin/ifenslave -d bond0 eth0 eth1
    dns-nameservers  xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
    dns-search  sub.domain.suffix
```

/etc/modprobe.d/aliases.conf
=====================
```
alias bond0 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200
```

---

### Post by Scottaroo on 2010-10-24
Greetings:

I had the same problem with a fresh 10.10 install.  My bonded configuration would not work.  Now, what's really weird is that I put 10.04 back on the server and upgraded from 10.04 to 10.10 using do-release-upgrade, and now it works properly.  I have no earthly idea what's different.  Here's the configuration file that works properly on an upgraded 10.10 but not a fresh 10.10:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto bond0
iface bond0 inet manual
        bond-slaves none
        bond-mode 4
        bond-miimon 100

auto eth0
iface eth0 inet manual
        bond-master bond0
        bond-primary eth0 eth1

auto eth1
iface eth1 inet manual
        bond-master bond0
        bond-primary eth0 eth1

auto vlan1
iface vlan1 inet static
        address 10.59.43.13
        netmask 255.255.255.0
        network 10.59.43.0
        broadcast 10.59.43.255
        gateway 10.59.43.1
        vlan_raw_device bond0

```

The behavior that I was seeing looked like the bond0 interface was coming up before eth0 and eth1 were ready.  The bond0 interface was up, but neither eth0 nor eth1 were up.  After the system booted up, if I issued the commands:
```

ifenslave bond0 eth0 eth1
ifup vlan1

```
everything worked properly.  It just wouldn't come up properly at boot.

@ElllisD:

The solution that you have there is the "old" way of doing it.  It was deprecated with the release of 9.10 and the upstart method of starting processes.  If you look in the 9.10 release notes([https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes]("https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes")) you will find a section about how bonding configurations have been changed.  The file /usr/share/doc/ifenslave-2.6/examples/two_hotplug_ethernet has the basic bonding configuration of the "new" way to do it with upstart.

It's ironic that the "old" way is working properly for you and the "new" way seems to be broken.  I'm not trying to say that you should change what you're doing or that you're wrong, I just didn't want people coming across this to introduce configuration changes that are likely to cause them problems later without a warning.  It's no longer the recommended configuration.

---

### Post by Rural on 2011-01-24
I'm seeing this too. Has anybody submitted a bug to Ubuntu? I'm not seeing one.

---

### Post by kelargo on 2011-01-24
I have a problem, similar to this..

I finally have bonding working with mode=4. not mode=round-robin.
my switch is a cisco 2950 with two gigE ports. my server has two gigE ports in the bond. 

It doesnt seem to work after booting. I may still have something wrong in /etc/network/interfaces. but it bonds, if I manually type in a few commands. i figure I can put these commands into a script and have it run at boot. 

first - /etc/modprobe.d/aliases.conf
I dont understand how this is referenced.. 
> 
alias bond0 bonding
options bonding mode=4 miimon=100 lacp_rate=1 downdelay=200 updelay=200


second - /etc/network/interfaces - 
note - I originally had a 4 port PCI-X network card that I removed. 
hence, the reference to eth4 & eth5, as that didnt go away.. :-/
> 
# The loopback network interface
auto lo
iface lo inet loopback

# The bond interface - mode 4 is 802.3ad LACP. No slaves are defined here.
auto bond0
iface bond0 inet manual
	bond-slaves none
	bond-mode 4
	bond-miimon 100
	address 192.168.0.50
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	up /sbin/ifenslave bond0 eth4 eth5
	down /sbin/ifenslave bond0 eth4 eth5
	dns-nameservers 8.8.8.8 8.8.8.4
	
 
auto eth4
iface eth4 inet manual
	bond-master bond0
	bond-primary eth4 eth5

auto eth5
iface eth5 inet manual
	bond-master bond0
	bond-primary eth4 eth5



the essence of my manual scripting.. to bring up the interface --
I put the sleep in there to help avid any race conditions and I put ntp
stop/start in there because it seemed to have problems in syslog.

Just doing /etc/init.d/networking stop/ start isnt "good enough".. 

> 
modprobe bonding
sleep 20
ifconfig bond0 192.168.0.50 netmask 255.255.255.0
sleep 20
ifenslave bond0 eth4 eth5
sleep 20
route add default gw 192.168.0.1
sleep 20
/etc/init.d/ntp stop
sleep 20
/etc/init.d/ntp start

 
and the cisco2950 config snippet.  fyi - I'm not using vlan1.

> 
!
interface Port-channel1
 description bond0 to Server
 switchport access vlan 160
 switchport mode access
 switchport nonegotiate
 arp timeout 60
 spanning-tree portfast
 hold-queue 300 in
!

interface GigabitEthernet0/1
 description Server port eth4
 switchport access vlan 160
 switchport mode access
 switchport nonegotiate
 speed 1000
 duplex full
 channel-group 1 mode active
 spanning-tree portfast
!
interface GigabitEthernet0/2
 description Server port eth5
 switchport access vlan 160
 switchport mode access
 switchport nonegotiate
 speed 1000
 duplex full
 channel-group 1 mode active
 spanning-tree portfast
!
interface Vlan160
 ip address 192.168.0.220 255.255.255.0
 no ip route-cache


---

### Post by kelargo on 2011-01-24
fyi - when I get more time.. tomorrow.. or so, I'll make my /etc/networks/interfaces look more like what @Scottaroo suggests.. just to see what happens.  For now, I'm happy I got it working at this level.. :-D

---

### Post by HubertB on 2011-06-07
I just run into the same issue (bonding not working on 11.04 server). There is a bug report (and a solution) about this: [https://bugs.launchpad.net/ubuntu/+source/ifenslave-2.6/+bug/714904](https://bugs.launchpad.net/ubuntu/+source/ifenslave-2.6/+bug/714904)

Apparently, the fix didn't made it into the repositories of 10.10 and 11.04 yet :-(

---

