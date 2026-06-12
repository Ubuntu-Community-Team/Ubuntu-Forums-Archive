---
title: "Adding an Interface"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by BenFischer on 2009-01-04
I'm trying to establish an internet connection on a computer thats part of a router network, but I'm a little confused what ip address I should assign it.  Using ifconfig I think I should be able to activate my eth0 interface with the up option.  I looked on another computer in my house to find an ip address, and assigned the same one to the computer im working on.  In the shell it looked something like this "ifconfig eth0 192.168.1.xxx up". 
After doing this ping comes up with network unavailable. 
Do I need to be using a different ip address for this new computer? Some other details, the computer had a working internet connection before.. if that affects anything? I'm using a Intel Corp. 82562EZ 10/100 Ethernet Controller card, and a ethernet connection.  kernel version 2.6.22-24. Hardy Heron. and a 2wire router. Let me know if anything else would be useful.

Thanks, 
Ben

---

### Post by bsh on 2009-01-04
hahaha.
OF COURSE you MUST use a different ip address on the same subnet...
to make things permanent, you should add entries to your /etc/iftab to assign a device name to a given mac address. the file should look something liek this:
```
eth0 mac xx:xx:xx:xx:xx:xx arp 1
```
(you amy or may not have other interfaces here too)
xx.xx.xx.... is the mac address of the network interface.
you can get this with:
```
sudo lshw -class network
```
which outputs something like this:
```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: xx:xx:xx:xx:xx:xx
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.010.00-NAPI duplex=full ip=192.168.2.10 latency=0 link=yes module=r8168 multicast=yes port=twisted pair speed=1GB/s
```

copy the serial number into iftab.
this way eth0 will always be assigned to this interface on boot/network up.
then configure the ip address to either static or dynamic (dhcp, assigned by your router)
this is done with the */etc/network/interfaces* file.
an example of static ip:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
mtu 1500
```
where address is your static ip address. first three numbers should be the same as your router's ip address first three numbersa, the last one must be something unique. (within 0..254) there shouldn't be two or more same ip addresses on the same subnet! so make sure you are using an ip that is not used (and will not be used in the future either!) make sure the chosen ip is unique! make sure it is not within the router's dhcp pool, so it won't get assignewd to other dhcp devices in the future.
subnet mask should be 255.255.255.0
gateway should be your router's ip address.
mtu is the maximum transmission unit, which is 1500 by default. you can increase it if your hardware supports jumbo frames (but all hardware including the router and other network devices!!! otherwise it is not giving any improved performence, or even getting worse. so don't touch it if you are unsure) (you can omit mtu completely, it will default to 1500)
this is how you define a static ip to a given device.
dynamic ip (dhcp) is less troublesome in many cases:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```
make the above changes in iftab and interfaces, then either restart netowrking or reboot.

---

### Post by BenFischer on 2009-01-04
Lol thanks, I'm a nooob.  I was confusing the router IP with the personal IP for the computer.  Just one edit to your post for anyone else who finds this useful solution.  I think they phased out /etc/iftab and replaced it with /etc/udev/rules.d/70-persistent-net.rules. So the mac can go there if no iftab file exists.

Thanks,
Ben

---

