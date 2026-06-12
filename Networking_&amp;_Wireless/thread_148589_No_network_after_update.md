---
title: "No network after update"
date: 2006-03-22
forum: Networking &amp; Wireless
---

### Post by Ishamael on 2006-03-22
I recently did an automatic update in Kubuntu (Breezy), updating the kernel and some other stuff I do not remeber.
And now, after rebooting, I can no longer reach the network :-| (even if I choose the old kernel in grub).
Any ideas as how to fix it?

The ethernet card I use is the one integrated on my nForce 3 motherboard.

When I try to ping anything I get
"connect: Network is unreachable"

"lsmod | grep Eth" returns nothing

ifconfig eth0
```
eth0      Link encap:Ethernet  HWaddr 00:15:F2:16:2E:4A  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3378 (3.2 KiB)  TX bytes:684 (684.0 b)
          Interrupt:10 Base address:0xe000 
```

cat /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp
```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

sudo dhclient eth0
```
There is already a pid file /var/run/dhclient.pid with pid 9493
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/eth0/00:15:f2:16:2e:4a
Sending on   LPF/eth0/00:15:f2:16:2e:4a
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted
/etc/dhcp3/dhclient-script: line 35: /etc/resolv.conf.dhclient-new: Permission denied
/etc/dhcp3/dhclient-script: line 41: /etc/resolv.conf.dhclient-new: Permission denied
chown: cannot access `/etc/resolv.conf.dhclient-new': No such file or directory
chmod: cannot access `/etc/resolv.conf.dhclient-new': No such file or directory
mv: cannot stat `/etc/resolv.conf.dhclient-new': No such file or directory
bound to 192.168.0.3 -- renewal in 1004438224 seconds.
```

I should add that my laptop has got no problems, using the same router.

---

### Post by jml on 2006-03-22
Its possible that the update reset some network configuration settings.  If you haven't already done so, go into the networking utility and see if your network card is still listed.  If it is, check on its properties to make sure everything is as it should be.  Then reactivate the card.  Deactivating it first if the system says its already active.  then reactivating it.  Rebooting the system afterwords may also help.  Sometimes significant upgrades to the system (like kernal upgrades,) can do funny things to configuration files.  Hope this helps.

Joe

---

### Post by mips on 2006-03-23
Try a static IP configuration and then try disabling IPv6

---

### Post by Ishamael on 2006-03-27
[QUOTE=jml]Its possible that the update reset some network configuration settings.  If you haven't already done so, go into the networking utility and see if your network card is still listed.  If it is, check on its properties to make sure everything is as it should be.  Then reactivate the card.  Deactivating it first if the system says its already active.  then reactivating it.  Rebooting the system afterwords may also help.  Sometimes significant upgrades to the system (like kernal upgrades,) can do funny things to configuration files.  Hope this helps.

Joe[/QUOTE]
The card deactivates itself upon activation.

[QUOTE=mips]Try a static IP configuration and then try disabling IPv6[/QUOTE]
Static IP works, thanks.



In "sudo dhclient eth0", the line:
```
DHCPREQUEST on eth0 to 255.255.255.255 port 67
```..means that it believes that my router is at 255.255.255.255, right?
Where does it get that number from?

---

### Post by n00buntu on 2006-03-27
Hello,

  I have exactly the same problem as Ishamael. Thanks for your reply, but I don't know how to use it:
1. Very sorry, but I hardly know GNU/linux, so I don't know how to do the things you said (like setting the IP to static and disabling IPv6).
2. I know from my ISP that my IP should be dynamic, so how can I change it to static in any case?

  If you could elaborate a bit, I'd really appreciate it!

---

### Post by mips on 2006-03-28
[QUOTE=Ishamael]The card deactivates itself upon activation.


Static IP works, thanks.



In "sudo dhclient eth0", the line:
```
DHCPREQUEST on eth0 to 255.255.255.255 port 67
```..means that it believes that my router is at 255.255.255.255, right?
Where does it get that number from?[/QUOTE]

255.255.255.255 is a Broadcast address, the DHCP request gets broadcasted to ALL clients on that network. Think about it, if your PC does not have an IP address or know what the router address is who is it going to send the dhcprequest to ??? Thus the broadcast to all clients, the one that is a dhcp server will respond.

Try disabling IPv6:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```

---

### Post by mips on 2006-03-28
[QUOTE=n00buntu]Hello,

  I have exactly the same problem as Ishamael. Thanks for your reply, but I don't know how to use it:
1. Very sorry, but I hardly know GNU/linux, so I don't know how to do the things you said (like setting the IP to static and disabling IPv6).
2. I know from my ISP that my IP should be dynamic, so how can I change it to static in any case?

  If you could elaborate a bit, I'd really appreciate it![/QUOTE]

To stop the IPv6 module from loading:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```

The WAN side of your connection will still be Dynamic as you have no control over that. You can however configure the LAN side between your PC and router for a static IP address. You will have to edit your /etc/network/interfaces file or you can do it via the GUI which differs between ubuntu & kubuntu.

The static config is just to determine whether the network actually works or not. You can then decide wheter you want to use DHCP or a static config.

You need to know your routers IP address, subnet mask and stuff like that in order to do a static config. If you don't and you have a dualboot windows install you can issue the "ipconfig /all" from a dos window and post the complete output here. From that I could tell you what to do. Alternatively look at post#38 here, [http://www.ubuntuforums.org/showthread.php?t=126764](http://www.ubuntuforums.org/showthread.php?t=126764) for an example, your values will not be the same though.

[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

---

