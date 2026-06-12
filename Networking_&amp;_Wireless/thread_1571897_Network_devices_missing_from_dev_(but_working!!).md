---
title: "Network devices missing from /dev (but working!?!)"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by olesk on 2010-09-10
I have a server with two network cards installed, one with a bridge used for OpenVPN - the setup works perfectly. Now, however, I cannot find eth0, eth1 nor br0 in /dev on Lucid (2.6.32-25-generic #43-Ubuntu SMP) any longer, and some programs that need a device for input, like nethogs, can no longer run. Fascinatingly, [FONT=Fixedsys]tcpdump eth1[/FONT] work, but [FONT=Fixedsys][SIZE=1]nethogs /dev/eth1[/SIZE][/FONT] does not, as there is no /dev/eth1 device. Which "eth1" device file tcpdump uses I have no idea about.
 
```
 
# Loopback interface                                                                                                                        
auto lo br0 eth1
iface lo inet loopback
 
# Main interface - eth0 - reserved at DHCP server to 10.0.0.90 
iface br0 inet static
        address 10.0.0.90
        netmask 255.255.255.0
        gateway 10.0.0.1
        bridge_ports eth0
 
iface eth0 inet manual
        hwaddress ether 00:22:15:9f:1b:00
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down
 
# Secondary interface - eth1 - to be set up in promisc mode to listen to ALL  
# traffic on Switch1 
iface eth1 inet manual
        hwaddress ether 00:22:15:9f:30:6c
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down
 
```
 
The strange thing is that the network works flawlessly, and all the devices are described in /dev/.udev/db/net, but there are no network devices in /dev, so the question is: where on earth are my network device files? 
 
 
Am I missing something extremely basic here? :)

---

### Post by furball4 on 2010-10-10
Ditto here... so I don't know how to specify a network interface for slmon to use.

---

### Post by olesk on 2010-10-11
Several kernel updates updates later (and all manner of other upgrades for that matter), there remains no network devices under /dev or /dev/network (or anywhere else). I used to work on AIX a *long* time ago, where device files were not really required, but I simply do not understand how this works on Ubuntu (and haven't been able to google up anything). Are there really noone who can tell us why a) the network devices don't exist as files under /dev or /dev/network and b) why it still works for some programs (tcpdump), but not others (slmon/nethogs)?

---

### Post by olesk on 2010-10-14
I haven't been able to solve my problem, but it seems that there might be a link to having vmware server installed (which I did, but it is now removed). 
 
Apparently, vmware can mess up the file /etc/udev/rules.d/70-persistent-net.rules which contains entries for the network cards. Mine looks like this:
 
```
# This file maintains persistent names for network interfaces.                                                                              
# See udev(7) for syntax. 
# 
# Entries are automatically added by the 75-persistent-net-generator.rules 
# file; however you are also free to add your own entries. 
 
# PCI device 0x11ab:0x4364 (sky2)  
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:15:9f:1b:51", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0" 
 
# PCI device 0x11ab:0x4320 (skge) 
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:15:9f:30:6c", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1" 
```
 
For people with vmware installations, this had messed up their MAC addresses for the cards. This is however not the case for me. The MAC addresses are correct, so are the drivers (and the network works - it's just that there are no /dev/eth0 and /dev/eth1 files).
 
If I cannot find any solution to this, I'll try deleting the file and restart udev to recreate.
 
Did you have or currently have vmware server installed?
 
 
*** Edit:
 
**Seems I've been utterly confused. The answer to all this is that (like I was used to from AIX about a decade back), the network device nodes/files are no longer used in Linux and Ubuntu. As they cannot be addressed in any meaningful way as files (unlike hard disks for example), they have been removed from linux. **
 
**What this means in practice is that programs like for example nethogs (nifty program, give it a spin!) will not work with a device parameter with full path (/dev/eth0 for example). This is by design, as there is no such device file/node anymore. Simply specifying "eth0" without a path does though, and should work for all other programs as well, though some (very old) programs might complain. **
 
**I guess this mens I'm getting old, as I'm so used to working with device nodes that it never dawned on me that they had died a long time ago. I'm really curious as to when exactly this happened, but I presume it must be quite some time back...**

---

