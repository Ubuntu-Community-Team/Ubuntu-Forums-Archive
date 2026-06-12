---
title: "Can setup bond on Broadcom but not Intel NICs?"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by Schorschi on 2009-04-08
Calling all NIC bond gurus!  Can setup bond on Broadcom but not Intel NICs?  Have Dell 2950, with 2 Broadcom NICs embedded, and PCI 4 port Intel NIC card.

Bond0 comes up fine, Bond1 Does not just fails.

Details...

root@Beta04:~# lspci | grep -i ether
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)
0c:00.0 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
0c:00.1 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
0d:00.0 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
0d:00.1 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)

root@Beta04:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth5
iface eth5 inet static
        address 192.168.15.93
        netmask 255.255.255.0
        network 192.168.15.0
        broadcast 192.168.15.255
        gateway 192.168.15.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.15.2 192.168.15.1
        dns-search Dachshund-Digital.Org

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto eth3
#iface eth3 inet dhcp

auto eth4
iface eth4 inet manual

# The bonded network interfaces

auto bond0
iface bond0 inet static
        pre-up modprobe bond0
        hwaddress ether 00:15:17:1e:ba:a0
        address 192.168.15.43
        netmask 255.255.255.0
        network 192.168.15.0
        broadcast 192.168.15.255
        gateway 192.168.15.1
        up ifenslave bond0 eth0 eth1
        down ifenslave -d bond0 eth0 eth1

auto bond1
iface bond1 inet static
        #pre-up modprobe bond1
        hwaddress ether 00:19:b9:b2:48:b3
        address 192.168.15.53
        netmask 255.255.255.0
        network 192.168.15.0
        broadcast 192.168.15.255
        gateway 192.168.15.1
        up ifenslave bond1 eth2 eth3
        down ifenslave -d bond1 eth2 eth3

root@Beta04:~# cat /etc/modutils/actions
# Probe for bond
probeall bond0 eth0 eth1 bonding
probeall bond1 eth2 eth3 bonding

root@Beta04:~# cat /etc/modprobe.d/aliases
# Aliases
alias eth0 bnx2
alias eth1 bnx2
alias eth2 e1000e
alias eth3 e1000e
alias eth4 e1000e
alias eth5 e1000e

# Alias for bond
alias bond0 bonding
alias bond1 bonding
options bonding mode=0 miimon=100

---

### Post by Schorschi on 2009-04-08
Output...

root@Beta04:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                           * if-up.d/mountnfs[eth5]: waiting for interface eth4 before doing NFS mounts
 * if-up.d/mountnfs[eth5]: waiting for interface bond0 before doing NFS mounts
 * if-up.d/mountnfs[eth5]: waiting for interface bond1 before doing NFS mounts
 * if-up.d/mountnfs[eth4]: waiting for interface bond0 before doing NFS mounts
 * if-up.d/mountnfs[eth4]: waiting for interface bond1 before doing NFS mounts
 * if-up.d/mountnfs[bond0]: waiting for interface bond1 before doing NFS mounts
SIOCSIFHWADDR: No such device
Failed to bring up bond1.
                                                                                                                         [ OK ]

---

### Post by Schorschi on 2009-04-08
I figured this one out, based on an odd reference to /sys/class/net/bonding_masters not explicitly having more than bond0 defined by default.  This was I guess RTFM, but I did not recall the bond_masters reference, but it was the clue I needed.  Also realized that I was bonding Broadcom to Intel ports, which is not desired in this case, so I corrected that as well.

Aliases should read...  For my specific hardware in this case...  Don't we just love PCI bus enumerations?

alias eth0 e1000e
alias eth1 e1000e
alias eth2 bnx2
alias eth3 e1000e
alias eth4 e1000e
alias eth5 bnx2

And the trick to add or remove a bond name?

Add...

# echo +bond1 > /sys/class/net/bonding_masters

Validate...  If two bonds desired...

# cat /sys/class/net/bonding_masters
bond0 bond1

Remove...

# echo -bond1 > /sys/class/net/bonding_masters

Validate...  If bond1 removed...

# cat /sys/class/net/bonding_masters
bond0

---

### Post by ElllisD on 2010-10-14
> **Schorschi said:**
> # echo +bond1 > /sys/class/net/bonding_masters

Validate...  If two bonds desired...

# cat /sys/class/net/bonding_masters
bond0 bond1


Thanks, that did it.

EDIT:

Except on 10.10 w/ 2.6.35-22 at least- it doesn't persist beyond the next reboot. Not to mention having 2 bonds up simultaneously somehow disbles sftp & ssh transfers. odd.

---

