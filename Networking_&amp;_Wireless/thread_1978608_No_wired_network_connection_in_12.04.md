---
title: "No wired network connection in 12.04"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by haaho on 2012-05-12
Hello,

I installed Ubuntu 12.04 using another computer for Internet
connection (shared with other computers). Everything is detected, 
but I have no connection until I restart  NetworkManager, with command 
```
sudo pkill -9 NetworkManager
```
After that it works as it should. Here some more information:

```
svee@svee-comp:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY
       vendor: Sundance Technology Inc / IC Plus Corp
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 31
       serial: b0:48:7a:84:f9:6b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sundance driverversion=1.2 duplex=full ip=10.42.43.10 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:e000(size=128) memory:ec111000-ec1111ff memory:40000000-4000ffff

```

```
svee@svee-comp:~$ dmesg | grep eth0
[    1.284888] eth0: IC Plus Corporation IP100A FAST Ethernet Adapter at 0001e000, b0:48:7a:84:f9:6b, IRQ 17.
[    1.285356] eth0: MII PHY found at address 0, status 0x7849 advertising 01e1.
[   17.316059] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.589896] eth0: Link up
[   20.590156] eth0: Link changed: 100Mbps, full duplex
[  280.528031] eth0: no IPv6 routers present
svee@svee-comp:~$ 
```

```
svee@svee-comp:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for svee: 
May 12 09:08:47 svee-comp NetworkManager[1672]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May 12 09:08:47 svee-comp NetworkManager[1672]: <info> (eth0): DHCPv4 state changed preinit -> bound
May 12 09:08:47 svee-comp NetworkManager[1672]: <info>   address 10.42.43.10
May 12 09:08:47 svee-comp NetworkManager[1672]: <info>   prefix 24 (255.255.255.0)
May 12 09:08:47 svee-comp NetworkManager[1672]: <info>   gateway 10.42.43.1
May 12 09:08:47 svee-comp NetworkManager[1672]: <info>   hostname 'svee-comp'
May 12 09:08:47 svee-comp NetworkManager[1672]: <info>   nameserver '10.42.43.1'
May 12 09:08:47 svee-comp NetworkManager[1672]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 12 09:08:47 svee-comp NetworkManager[1672]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May 12 09:08:48 svee-comp NetworkManager[1672]: <info> DNS: starting dnsmasq...
May 12 09:08:48 svee-comp NetworkManager[1672]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
May 12 09:08:49 svee-comp NetworkManager[1672]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 12 09:08:49 svee-comp NetworkManager[1672]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
May 12 09:08:49 svee-comp NetworkManager[1672]: <info> Activation (eth0) successful, device activated.
May 12 09:08:49 svee-comp NetworkManager[1672]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
May 12 09:08:49 svee-comp AptDaemon.NetMonitor: WARNING: Failed to determinate network state
May 12 09:09:08 svee-comp NetworkManager[1672]: <info> (eth0): IP6 addrconf timed out or failed.
May 12 09:09:08 svee-comp NetworkManager[1672]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 12 09:09:08 svee-comp NetworkManager[1672]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 12 09:09:08 svee-comp NetworkManager[1672]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```

---

### Post by probin51 on 2012-05-12
Seeing similar problems here too. When booting, the logon screen appears but it takes a while for Unity to come up.

The only thing I can find in dmesg is...

```

[    8.809080] kjournald starting.  Commit interval 5 seconds
[    8.809112] EXT3-fs (sda1): recovery complete
[    8.809395] EXT3-fs (sda1): mounted filesystem with ordered data mode
[COLOR="Red"][   33.457548] ADDRCONF(NETDEV_UP): eth0: link is not ready[/COLOR]
[   33.470719] udevd[523]: starting version 175

```

Sometimes when the desktop appears I have no networking. This never happened under 11.10, 11.04. So this is specific to 12.04.

If I find anything out this weekend I'lll post back.

---

### Post by haaho on 2012-05-12
Just to add that the same hardware works fine under Lucid, no problems at all.

---

### Post by guilag on 2012-05-12
Same thing here :-(

Each time I login, I have to do this command:
sudo ifdown eth0 && sudo dhclient eth0 && sudo ifup eth0

---

### Post by haaho on 2012-05-14
Played half a day with the network settings, trying to connect trough pppoe, no luck. Everything worked out of the box with 10.04. 
Tryed sound settings - no microphon, everything worked fine with 10.04.

Very hard for me to call the new Ubuntu "a progress" :-x




edit:  Removing NetworkManager and configuring trough pppoeconf solved the problem.

---

### Post by LarryJ2 on 2012-06-09
My "clean" install of Mythbuntu 12.04 will not connect through the wired interface eth0 in the same manner described in this thread.  "ifconfig" shows eth0 is present but never gets an ip assigned.

So I decided to fall back on my old "never fail"  wicd which I started using the last time ubuntu/linux messed up the wired connection. 

1. sudo apt-get install wicd

2. sudo apt-get remove --purge network-manager-gnome

3. sudo apt-get remove --purge network-manager

Then I used wicd's  gui to insert my static config data. 

Even that didn't help.  Still no eth0 connection.

If I plug in a wifi usb dongle,  wicd finds wlan0 and I can connect OK using wlan0  either with  static or dhcp.

I've been goodle-ing away on this for more than eight hours.  This same hardware worked fine in Mythbuntu 10.04.  I'm sorry I changed!:mad:

Larry

---

### Post by LarryJ2 on 2012-06-11
If you haven't removed network-manager,  try this:

sudo start network-manager

On another 12.04 installation on a different non mythbuntu PC,  this "magically" caused eth0 to connect, receive an ip, and a dns server.

Presently reinstalling Mythbuntu 12.04 (4th time)  Wish me luck!

---

