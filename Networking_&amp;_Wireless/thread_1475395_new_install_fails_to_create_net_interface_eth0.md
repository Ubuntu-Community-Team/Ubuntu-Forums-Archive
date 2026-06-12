---
title: "new install fails to create net interface eth0"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by idella on 2010-05-06
I have a new install and I am quite surprised it just misses networking**.**  That is, **NO** networking.

ifconfig comes up with inly lo.  Nothing else, most primal.

It should use dhcp to connect, bit it fails to create the eth0 interface.
Such a fundamental flaw is one I can't work on. Forget looking in network manager in the desktop, that's still being installed, but it's no help.
I've checked the basic files in etc against karmic.


idella@squeeze:~$ cat /mnt/lucid/etc/network/interfaces 
# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp
iface wlan0 inet dhcp

This one had me puzzled.  I was attempting to bring it up as a vm, and it just rejected the line

allow-hotplug eth0.

It accepted hotplug eth0, then didn't do it.


idella@squeeze:~$ cat /mnt/lucid/etc/networks
# symbolic names for networks, see networks(5) for more information
loopback        127.0.0.0
link-local 169.254.0.0

idella@squeeze:~$ cat /mnt/lucid/etc/resolv.conf
nameserver 61.9.242.33
nameserver 61.9.226.33

Any help appreciated.

---

### Post by Iowan on 2010-05-07
I presume this is not a standard install...
My Lucid box has no */mnt/lucid* directory and no */mnt/lucid/etc/networks* (or even */etc/networks*) directory. A Network Manager-controlled machine typically has only the two lines defining "lo" in */etc/network/interfaces*. 
VM is still something I haven't tried...

---

### Post by idella on 2010-05-08
I'll try a second time.
Can some one give me a correct content for /etc/network/interfaces for lucid.

It's new ofcourse but bootup just misses the network.
It doesn't create eth0, a fundamental problem.  file content is currently 


# The loopback network interface
#auto eth0
#lo
#eth0
#iface eth0 inet dhcp

# The primary network interface
#hotplug eth0
#iface eth0 inet dhcp
#iface wlan0 inet dhcp
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp
#iface wlan0 inet dhcp

I think I overwqrote the initial one.  I've tried a few versions.
This is a version from karmic   It just doesn't translate.
The important line is 

auto lo

from [http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

We have  auto eth0

iface eth0 inet dhcp 

however, it's dated 2006.

The document desperately needs updating.  It doesn't work.

ifconfig just includes  lo.  I searched threads but they were mostly for prior vesions.

Since karmic's doesn't work, it must have changed.

I have had it create eth0 on a different setting, but I didn't record it.  It then failed to complete bootup anyway.

and 

linux-rf2t:/home/idella # grep eth0 /mnt/lucid/var/log/dmesg
[    0.000000] Command line: root=/dev/xvda2 ro ip=:::::eth0:dhcp
[    0.000000] Kernel command line: root=/dev/xvda2 ro ip=:::::eth0:dhcp
[    1.712103] IP-Config: Device `eth0' not found.

If I enter 

auto eth0

It prevents it from even completing boot.

Please. I can't use lucid properly now.

Cancel that.  I fixed it.   etjh0 was being renamed to eth2

---

### Post by Iowan on 2010-05-08
Threads merged.
From CoC:> Please do not cross post, or post the same thing in multiple locations.
Glad you found a solution!
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

