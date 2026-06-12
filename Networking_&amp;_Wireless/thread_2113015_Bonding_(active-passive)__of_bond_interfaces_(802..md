---
title: "Bonding (active-passive)  of bond interfaces (802.3ad)"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by alexdh on 2013-02-06
Hello,

We have a server with 4 NICs.
We would like to make a configuration like this :

- 2 NICs in lag (802.3ad) on one switch        --> bond0
- 2 NICs in lag (802.3ad) on another switch --> bond1

And to have these 2 bond0 et bond1 in active-passive.

We try this configuration :

 # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# bond0
auto eth0
iface eth0 inet manual
        bond-master bond0
auto eth1
iface eth1 inet manual
        bond-master bond0

auto bond0
iface bond0 inet manual
bond-mode 802.3ad
bond-miimon 100
bond-slaves none
bond-lacp-rate 1

#bond 1
auto eth2
iface eth2 inet manual
        bond-master bond1
auto eth3
iface eth3 inet manual
        bond-master bond1
auto bond1
iface bond1 inet manual
bond-mode 802.3ad
bond-miimon 100
bond-slaves none
bond-lacp-rate 1

# bond 2

auto bond2
iface bond2 inet static
address X.X.X.200
netmask 255.255.255.0
gateway X.X.X.1
broadcast X.X.X.255
network X.X.X.0
bond-mode active-backup
bond-miimon 100
bond-slaves bond0 bond1
bond-lacp-rate 1

bond0 and bond1 are up, we could see the eth interfaces in the /proc/net/bonding/bond*

But the bond2 is up, but with no relation to bond0 and 1.

Anyone have an idea to solve this?
Is it possible to have a such configuration?

Thanks in advance !

Alexdh

---

### Post by me5 on 2013-08-13
Hi Alex,

did you proceed with this Problem? I had the same Idea, but can't google "if it's possible" to bond a bond? If you have found more information about this topic, i'm glad to hear...

Thx
John

---

### Post by Josh_Simmonds on 2014-01-21
I was trying to create almost this exact setup, but instead of active-passive, I was shooting for multi-mode/load-balanced for my third bond.  Below is my scrubbed interfaces file from attempting to create a third bond, which I think is *almost* there.  I don't think you need your "lacp-rate fast" inside bond2 config, though.

Logically, I wouldn't think it impossible to accomplish what we're after, but I couldn't quite get there.  After a lot of playing around and googling, I can't get two bonds to be bound together.  I've resorted to bridging to create one logical interface, and it looks like that, at least for the time being, gives me what I'm looking for (in my test, it's 4 nics of LACP per switch, and then a bridge to let it balance between them).  The functioning bridge interface is below the first set of notes (with some jumbo frames for good measure).

Hope this helps!

---

NON-Functional Bonding Config (trying to multi-mode two lacp bonds).

auto bond2
    iface bond2 inet manual
    bond-slaves none
    bond-size miimon 100
    bond_xmit_hash_policy layer2+3+4
    mtu 9000
    bond-mode 802.3ad
    bond-master bond3
        bond-downdelay 200
        bond-updelay 200
        post-up ifconfig $IFACE up

auto bond1
        iface bond1 inet manual
        bond-slaves none
        bond-size miimon 100
        bond_xmit_hash_policy layer2+3+4
        mtu 9000
        bond-mode 802.3ad
        bond-master bond3
        bond-downdelay 200
        bond-updelay 200
       post-up ifconfig $IFACE up

auto bond3
        iface bond3 inet static
        address xxx.xxx.xxx.32
        netmask 255.255.255.0
        network xxx.xxx.xxx.0
        broadcast xxx.xxx.xxx.255
        bond-slaves bond1 bond2
        bond-size miimon 100
        bond_xmit_hash_policy layer2+3+4
        mtu 9000
        bond-mode 6
    bond-downdelay 200
    bond-updelay 200
      post-up ifconfig $IFACE up

------

Functioning Bridge Config:

auto bond2
    iface bond2 inet manual
    bond-slaves none
    bond-size miimon 100
    bond_xmit_hash_policy layer2+3+4
    bond-mode 802.3ad
    bond-downdelay 200
    post-up ifconfig $IFACE up

auto bond1
    iface bond1 inet manual
    bond-slaves none
    bond-size miimon 100
    bond_xmit_hash_policy layer2+3+4
    bond-mode 802.3ad
    bond-downdelay 200
    post-up ifconfig $IFACE up

auto br0
    iface br0 inet static
    address xxx.xxx.xxx.32
    netmask 255.255.255.0
    network xxx.xxx.xxx.0
    broadcast xxx.xxx.xxx.255
    bridge_ports bond1 bond2
    bridge_stp off
    bridge_maxwait 0
    bridge_fd 0
    post-up ifconfig bond1 mtu 9000 && ifconfig bond2 mtu 9000 && ifconfig br0 mtu 9000

---

