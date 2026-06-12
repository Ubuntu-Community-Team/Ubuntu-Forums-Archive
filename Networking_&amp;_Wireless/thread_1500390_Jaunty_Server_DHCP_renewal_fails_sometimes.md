---
title: "Jaunty Server DHCP renewal fails sometimes"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by SabreWolfy on 2010-06-03
Ubuntu Jaunty Server connected via eth0 to a Billion residential ADSL router. I've locked the server MAC address to a specific IP in the router and set the DHCP renewal times to the longest possible times. For a certain number of days, the server will remain connected to the router, but then for some reason (the last time it was after about a month), the server loses it's connect and dumps into syslog the following:

```

Jun  2 17:10:15 defiant dhclient: DHCPREQUEST of 192.168.1.105 on eth0 to 192.168.1.254 port 67
Jun  2 17:11:26 defiant dhclient: last message repeated 5 times
Jun  2 17:12:32 defiant dhclient: last message repeated 5 times
Jun  2 17:13:33 defiant dhclient: last message repeated 5 times
Jun  2 17:14:37 defiant dhclient: last message repeated 4 times

```

repeatedly, followed sometimes by this:

```

Jun  2 22:15:40 defiant dhclient: No DHCPOFFERS received.
Jun  2 22:15:40 defiant dhclient: No working leases in persistent database - sleeping.

```

I've not made any changes to any of the standard network installation settings. I just plugged the ethernet cable into the machine when I installed it several months ago.

I've searched for threads around this, but none seemed to address the issue of a previously-working eth0 connection breaking.

Restarting the router sometimes results in the server coming back onto the network. However, sometimes not even this solves the problem. This means having to pull the power cord on the headless server.

I'm a little disappointed that a server installation cannot remain connected to the 'net via a router for months on end. Not much good as a server if I've gotta pull the plug on it every X days.


```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

```

/etc/resolv.conf points to the router.

```

$ route
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         home.gateway    0.0.0.0         UG    100    0        0 eth0

```

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:30:04:ef  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe30:4ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9048216 (9.0 MB)  TX bytes:37049917 (37.0 MB)
          Interrupt:26 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10907524 (10.9 MB)  TX bytes:10907524 (10.9 MB)

```

Ideas?

---

### Post by puppywhacker on 2010-06-03
A very big chance that it is your ADSL dhcpserver that is not stable, I would use a static addresses on your server as with local addresses you don't have a shortage. use something below 100 like 192.168.1.2 than you can still use dhcp from your ADSL router for other devices and not assign addresses double.

If you insist on troubleshooting use tcpdump or wireshark to capture the traffic, I think your router is just not responding consistently.

---

### Post by SabreWolfy on 2010-06-03
Thanks for the reply. I have the server set to use DHCP, but I have set the router to always give the same IP address to the server, so I guess that's a little redundant. I should just setup the SERVER to use the same IP by editing /etc/network/interfaces?

---

### Post by puppywhacker on 2010-06-03
yeah, that's what I mean, the server can have a static address so you are not plagued with requesting the same address, which may fail. ubuntu server doesn't have network-manager right? then the interface file is your best friend :)

```
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
```

just remember that you probably also want to set your DNS server in /etc/resolv.conf

---

### Post by SabreWolfy on 2010-06-10
Correction: My OP mentioned that this is a Jaunty server. It is in fact a Karmic server, recently upgraded to Lucid, and the problem was present under Karmic and is still present under Lucid.

**@puppywhacker:** Thanks for the suggestion -- I've been meaning to try it but have not got around to it yet. However, the server exhibited the problem again this morning. I think maybe I did not explain it properly or that there is more than one problem here. I'd appreciate your comments.

The server and a Karmic to Lucid desktop are both connected via ethernet to a residential ADSL router. The server is on 24/7. The desktop is suspended and resumed at various times. The problem only ever manifests on the server. At no point does the server disconnect from the router. I can always SSH into it from the desktop machine, so that means that the DHCP part is working? The server loses the ability to make outgoing connections. The desktop is able to make connections at that time, so the router is still connected. On the server /etc/resolv.conf points to the router. I'm not sure what to look for in syslog. A 'dig' lookup on the desktop works. The same lookup on the server reports that no servers could be reached.

During my testing, I entered 'ifdown eth0' on the headless server, while connected to it via SSH -- um, yes :) -- and had to manually force a restart. Strangely, after this the server STILL had no connection. After then restarting with a 'sudo reboot' the dig still failed.

After then restarting the **router**, the dig on the server worked, so clearly this is something to do with the router, as puppywhacker suggested. However, how come the dig worked on the desktop machine -- also connected to the same router -- but not from the server?

Should routers be power-cycled every few days? An arrangement where a server cannot make outgoing connections and can only be accessed from a LAN after X number of days is unworkable.

I've looked through settings on the router, but I can't find one which says *Only nuke Ubuntu servers connected via Ethernet.* :)

---

### Post by raim1312 on 2010-10-05
I am actually having the same problem. I have a Lucid Ubuntu server with a dhcp reserve configured and the router does not see the box as renewing its ip when the lease expires. As you described this doesn't happen all the time. Last month it didn't happen at all but its happened twice this week. I've tried forcing the router to refresh the reserved IP but that didn't fix the issue. I can ssh into the box using IP from in the network but DNS fails when its in this state. And yes sometimes a reboot does not fix it. But then other times dhclient -r fixes it.

Whats weirder is I have another Ubuntu 10.04 server on the same network that has been up and running days before this box was created that has never experienced the issue. Any recommendations would be greatly appreciated.

---

