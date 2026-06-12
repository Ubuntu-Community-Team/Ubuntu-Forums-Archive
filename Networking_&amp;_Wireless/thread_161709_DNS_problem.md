---
title: "DNS problem"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by tsvim on 2006-04-17
Ok, I have some trouble with my networking config. I'm quite a newbie to linux in general and am quite lost. I installed ubuntu on my Thinkpad a while ago and started playing around with linux. :) 
Networking was quite fine (not 100%, the other problem I'm posting in another thread as it is not really related) up till about a week ago where for no apparent reason the laptop wouldn't automatically find dns servers which are defined on my router. As I connect from different places this is quite a hassle.

I don't know what I did to cause the problem, please help.

```
/etc/hosts

127.0.0.1 localhost.localdomain localhost TTMOST-LAPTOP

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I changed the following according to my understanding of a post over here
```
/etc/dhcp3/dhclient.conf

prepend domain-name-servers 127.0.0.1;
```

```
/etc/resolv.conf

nameserver 212.143.212.143
nameserver 194.90.1.5

```

Although I always have to change it manually on reboot for some odd reason. Except for that as I mentioned I change location often so the ISP I'm using changes as well.

```
/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
gateway 10.200.1.1

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep

# The primary network interface



iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid lev

auto eth0

```

Now, this file needs some work on on which I'm writing another post.
Please, help me. :confused: :confused: :confused:

---

### Post by tribaal on 2006-04-17
I had much trouble with networking until I changed /etc/nsswitch.conf the following way:

the line that says
```
hosts: files dns
```

Should be :
```
hosts: files dns wins
```

This really made all my problems disapear. Hope it'll help you too :)

Oh yeah and make sure winbind is installed... a quick ```
sudo apt-get install winbind
``` will sort it out ;)

- trib'

---

