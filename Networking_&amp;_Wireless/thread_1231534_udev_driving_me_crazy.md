---
title: "udev driving me crazy"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by latev on 2009-08-04
My mobo came with 2 NICs, so I decided to configure them as a bridge. That way I'll be able to hook up my laptop to the other nic and access the inet.
I managed to configure the bridge fine using the command line. It worked fine until the next reboot. To my surprise Ubuntu had it all totally messed up:

1) The two NICs originally eth0 and eth1 were renamed (WTF?!) to eth2 and eth3

dmesg |grep eth

[    8.405980] udev: renamed network interface eth1 to eth2
[    9.405672] udev: renamed network interface eth0 to eth3

2) Two new lines were created in /etc/udev/rules.d/70-persistent-net.rules

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:55", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:22:33:44:55", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

Judging by the MAC addresses assigned to them - it has something to do with the bridge, since 00:11:22:33:44:55 is the MAC I assigned to it

3) My original eth0 and eth1 appeared to have vanished
ifconfig eth0
eth0: error fetching interface information: Device not found

4) My internet connection doesn't work!

5) I tried to get rid of the two extra lines in  /etc/udev/rules.d/70-persistent-net.rules but upon restart they are automatically recreated again now!

6) A mysterious pan0 bridge was automatically created for me (WTF!)
brctl show
bridge name     bridge id               STP enabled     interfaces
pan0            8000.000000000000       no

7) eth0 and eth1 are NOT members of the bridge any more /they were supposed to/

Here's my interfaces file

auto lo
iface lo inet loopback

auto br0
iface br0 inet static
bridge_ports eth0 eth1
address 192.168.1.11
netmask 255.255.255.0
gateway 192.168.1.1

8) I tried to revert back to my original configuration by erasing the two lines again in 70-persistent-net.rules and getting rid of the bridge altogether by commenting out the relevant lines in the interfaces file, but after the reboot things didn't change, besides the br0 now being gone

So - this whole thing is driving me crazy - feels like Ubuntu is thinking instead of me. Am I missing something? How do I revert to my original config? HHow do I get prevent the OS from creating eth's and renaming eths around? how do I make my *working* bridge configuration permanent?

Any ideas/comments/suggestions are welcome!

Thanks

---

