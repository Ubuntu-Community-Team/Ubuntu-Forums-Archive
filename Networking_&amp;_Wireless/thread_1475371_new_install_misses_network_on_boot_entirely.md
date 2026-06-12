---
title: "new install misses network on boot entirely"
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

Any help apprciated.

---

### Post by talkingwires on 2010-05-07
I'm having the exact same problem, and I am equally baffled. Help?

---

### Post by relay_man on 2010-05-07
I've just had this happen to  me also.
I also went to the terminal and typed in "ifconfig" and found that the 
usual Eth0 was not present.

My install of Lucid is only a few days old and I the update manager ran last night, so maybe it was something in the updates...?

At any rate, I did the following and got going again.

1. Shutdown and power off.
2. Restart and gave the machine several minutes to complete all startup tasks.
3. The network icon in the upper panel again indicated that there was no network connection so I right clicked on it and unchecked the enable networking box.
4. I did another shutdown and power off.
5. Restart again allowing several minutes for all startup tasks to complete.
6. Right click on the network icon again and checked the box to enable networking.

It appears after this that the dhcp configuration took place automatically and I've now got my connection back.
I'm going to do a few more restarts from complete shutdown and power off to see if I have trouble again.
Then I'm going to let the computer go to suspend to see perhaps if this problem stems from an unsuccessful resume from suspend.

Hope this helps.

---

### Post by talkingwires on 2010-05-08
After some extensive searching, I think I narrowed the problem down. The Realtek 8139 chipset (what I've got) works terribly on Debian-based Linux distros. Here's a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/156496"), which was opened in 2007. Lots of progress there, let me tell ya. I found [many]("http://ubuntuforums.org/showthread.php?t=91746") [posts]("http://ubuntuforums.org/showthread.php?t=1436322") [from]("http://www.backtrack-linux.org/forums/beginners-forum/27775-networking-problems-realtek-rtl8139.html") [people]("http://bbs.archlinux.org/viewtopic.php?id=46583") struggling with this problem, as well as a [potential solution]("http://ubuntuforums.org/showthread.php?t=538448") that didn't work for me, unfortunately.

Just so I don't accidentally hijack another user's thread with a different problem, what chipset are you using, idella?

---

### Post by webdebbyjoss on 2010-05-08
Hi, guys

I have exactly the same problem. My "eth0" just disappeared a few minutes ago after some upgrade were installed. 

How can I help to investigate this? What information do we need?

My hardware is ASUS EeePC 1005 HA 

```

# ifconfig -a

```

doest shows "eth0" at all

```

# lshw -C network

```

shows only Wireless interface, and there is no any wired Ethernet interface available

```

# lspci -v

```

no Ethernet available

---

### Post by webdebbyjoss on 2010-05-15
Hi, I can reproduce this problem again from fresh install.

1. Install fresh Ubuntu 10.04
2. Install the "eeepc-tray"
3. Reboot.

Ethernet is gone!! :confused:

---

