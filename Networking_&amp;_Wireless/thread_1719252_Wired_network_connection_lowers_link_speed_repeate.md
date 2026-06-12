---
title: "Wired network connection lowers link speed repeatedly."
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by P_i_n_k on 2011-04-01
I believe I'm running Kubuntu 10.04, but don't quote me on that. Here's the version string from dmesg.
Linux version 2.6.32-31-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #60-Ubuntu SMP Thu Mar 17 22:15:39 UTC 2011 (Ubuntu 2.6.32-31.60-generic 2.6.32.32+drm33.14

I have an emergent problem with my wired ethernet resetting the connection on a frequent basis. When it resets it re-negotiates the link speed and I often end up with a 10Mb/s link and on some occasions a 100Mb/s. The configured speed for the link is 1000Mb/s full duplex using a preup ethtool command.

I do not use NetworkManager but have the interface configured in /etc/network/interfaces.

```
kitchen@lenir:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
pre-up /usr/sbin/ethtool -s eth0 speed 1000 duplex full
address 192.168.1.66
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255

```When this happens I use ethtool to force it to renegotiate and it quite happily establishes a 1000Mb/s link again. It can be anywhere from a few seconds to a few hours before the link drops again and renegotiates and it only ever seems to happen when the network is actively in use (even the smallest amount of traffic such as a ping).

On reboot the link correctly configures itself using the defined settings, but it used to do that without explicitly defined preup/ethtool settings.

An example of what I typically see is below.
```

kitchen@lenir:~$ sudo ethtool eth0
[sudo] password for kitchen: 
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  Not reported
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes
kitchen@lenir:~$ date
Fri Apr  1 18:28:11 BST 2011
kitchen@lenir:~$ sudo ethtool -s eth0 speed 1000 duplex full
kitchen@lenir:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  Not reported
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: No
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

```What I tend to see in the messages log is a pattern something like this one.
```

Mar 31 21:48:51 lenir kernel: [   31.866928] eth0: link up.
Mar 31 21:48:51 lenir kernel: [   31.867845] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Mar 31 21:48:54 lenir kernel: [   35.226029] Registering the dns_resolver key type
Mar 31 21:48:54 lenir kernel: [   35.226079] Slow work thread pool: Starting up
Mar 31 21:48:54 lenir kernel: [   35.226907] Slow work thread pool: Ready
Mar 31 22:01:16 lenir kernel: [  758.926741] eth0: link down.
Mar 31 22:01:33 lenir kernel: [  776.515891] eth0: link up.
Mar 31 22:33:52 lenir kernel: [ 2714.890028] eth0: link down.
Mar 31 22:34:10 lenir kernel: [ 2732.720995] eth0: link up.
Mar 31 22:40:10 lenir kernel: [ 3093.586066] eth0: link down.
Mar 31 22:40:30 lenir kernel: [ 3113.460595] eth0: link up.
Mar 31 22:40:41 lenir kernel: [ 3124.097284] eth0: link down.
Mar 31 22:40:59 lenir kernel: [ 3141.981987] eth0: link up.


```Where 
"Mar 31 21:48:51 lenir kernel: [   31.866928] eth0: link up." is the machine booting.
"Mar 31 22:01:16 lenir kernel: [  758.926741] eth0: link down." is the link going down and resetting.
"Mar 31 22:33:52 lenir kernel: [ 2714.890028] eth0: link down." is me resetting it with ethtool. 
"Mar 31 22:40:10 lenir kernel: [ 3093.586066] eth0: link down." is it going down again.
With the final pair of down/up being me resetting it with ethtool again.

Does anyone have any idea as to how I can force it to renegotiate to 1000Mb/s? The addition of the preup command in the interfaces file only seems to work on boot and not when the link is dropped.

I've yet to investigate hardware failures (cables, rj45 socket), but it always happily gives me 1000Mb/s when manually using ethtool, hence I assume it is not using the preup apart from on boot.

---

### Post by Fire_Chief on 2011-04-01
That almost definitely sounds like a hardware problem or a duplex/speed mismatch between the workstation and the switch. You mentioned that the problem mostly appears when the link is under load. Do you see the same stability problems if the speed/duplex settings are lowered to a slower rate?

---

### Post by P_i_n_k on 2011-04-01
The hardware used hasn't changed in the 6 months or so I've been running this. It's unlikely to be an actual hardware mismatch between the switch and the NIC as it was running fine for many months at full speed. The only thing that has changed is me applying updates to Ubuntu. As a result of this issue occurring I added the pre-up line as an attempt to fix it.

I have still to check several hardware elements, network socket on the wall, use another machine, another cable, another OS. As I need to do that in a methodical manner so as to only change one element at a time I need to set aside some time for it.

The strange thing is, if it was hardware I would expect it to fail sometimes when using the ethtool command but it always (and I really do mean always, test data being about 30ish times in the last two weeks) returns 1000Mb/s when running the command manually. Also it can drop again within a second or two of me running ethtool, return 10Mb/s before I've even moved away from the command line and I run the ethtool command immediately and it returns 1000Mb/s again. 

From this I would expect when it drops the link that it would sometimes return 1000Mb/s but it never seems to, only ever 10Mb or 100Mb (this is less conclusive as I'm not always around to see the link drop necessarily).

I see from the ethtool output that 'Autonegotiate' is turned on, I don't know whether this means negotiate speed or autonegotiate a link when a cable is plugged in (ie bring the interface up) so I haven't tried to fiddle with that.

I'll try and get the hardware tests done sometime soon, I was looking to find a way to force 1000Mb/s when the hardware/driver/networkstack drops the connection, as at least then it would simply be a temporary outage of the network and wouldn't have much of an effect on streaming or data transfers. It's annoying when you're transferring something and you have to ssh in and renegotiate the link before continuing to get a reasonable speed.

---

### Post by P_i_n_k on 2011-04-01
Sorry, also meant to say I shall try setting it to 100Mb/s explicitly and see if it drops then at all.

---

