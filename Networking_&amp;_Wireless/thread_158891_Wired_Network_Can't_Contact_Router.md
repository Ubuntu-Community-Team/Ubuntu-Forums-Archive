---
title: "Wired Network Can't Contact Router"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by bennyk on 2006-04-11
Hi,
This will be very basic quesion, I hope.

I'm using 5.10 and a Linksys DD-WRT router, as my wired router.

The NIC is a National Semiconductors DP83815.

The NIC works perfectly under XP Pro with this router and DHCP setup.  Other machines on the network (Mac OS and Windows) can connect to the router and get DHCP from it.

my /etc/network/interfaces entry looks like:

auto eth0
iface eth0 inet dhcp

when I dhclient eth0, it displays

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval

and tries a bunch of times but gets no response.  When I look at the router's logs, it does not show any contact from the machine.

I have tried disabling ipv6 and it didn't seem to help.  I have tried the natsemi-diag tool and the card seems to be OK.  lspci is recognizing the card correctly.

This is quite frustrating, so I'm hoping there's something simple I'm missing, any ideas?

Thanks,
bk

---

### Post by spanishwasabi on 2006-04-12
Can you set an IP address yourself and ping the router?
Did you try other ports of the router with your machine?
Did you check it's not the cable? (Don't laugh, would not be the first time it happens... :-) )

G

---

### Post by bennyk on 2006-04-12
Can you set an IP address yourself and ping the router?
[B]
I can set the IP manually, and ifconfig confirms that it has been set, but I still cannot ping the router.
[/B]
Did you try other ports of the router with your machine?
[B]
I tried other ports with dhclient, 1-10, 60-70, but I really didn't have any idea which ports to try, I was just poking around.[/B]

Did you check it's not the cable? (Don't laugh, would not be the first time it happens... )
[B]
Believe me, I would not laugh, if the cable would fix the problem I'd be quite happy!  But alas, I have tried several others.[/B]

Is it possible that I am blocking all the traffic from my machine somehow?  This doesn't seem likely, since even during the install I could not connect to get DHCP.

Is it possible that the linux system is sending out information that is formatted differently than Win XP is does on the same machine, and that's why the router won't see it?

Thanks for your response.

---

### Post by spanishwasabi on 2006-04-12
Ok... if it's not the cable...

ping might be blocked somehow.

Try nmapping (nmap) other machines, like the XP machine and your router, and try to nmap the linux machine from the other machines.

Ensure you don't have any firewall enabled, nor on linux nor on windows (just for testing purposes, of course!)

When I was talking about  "other ports" i was meaning the physical plugs of your router. You usually have a few (4? 5?) and sometimes one is reserved for crossed cables, or simply not working. Does your windows machines still work when you plug the network cable on the port you have the linux macine now?

Alwaysdo your cheks both ways (Linux->router, router->linux, XP->Linux, Linux->XP) for ping, nmap or others.

Good luck,

G

---

### Post by bennyk on 2006-04-12
When I was talking about "other ports" i was meaning the physical plugs of your router.

**Yes, I have tried several different ports.  When I boot the linux machine into Win XP, it works fine with DHCP.  That's the puzzling part.**

I will install nmap and check into that.

---

### Post by bennyk on 2006-04-12
I scanned using nmap under Win XP, and found that the router has port 53 open as "domain" so I tried doing

dhclient eth0 -p 53 -s 10.0.1.129

however it still will not get any dhcp response.  This is quite frustrating, but there MUST be a way to make it work, no?

Thanks,
bk

---

### Post by bennyk on 2006-04-13
Bump for any last ditch advice before I pack in this whole linux idea.

---

### Post by mips on 2006-04-14
How did you disable IPv6 ???

1. Please disable IPv6 and reboot:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```
2. Please post output of **ifconfig eth1**
3. Please post output of **lspci | grep Eth**
4. Please post output of **route -n**
5. Please post output of **cat /etc/resolv.conf**
6. Please post output of **cat /etc/network/interfaces**
7. Please copy **entire** output of windows **ipconfig /all** command here

---

### Post by bennyk on 2006-04-16
Thanks mips, I'll post that here when I get a moment.

---

### Post by bennyk on 2006-04-16
1. Please disable IPv6 and reboot:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```

*OK*

2. Please post output of **ifconfig eth1**

```
eth0 Link encap:Ethernet HWaddr 00:A0:CC:A0:F2:6C
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
TX Packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:11
```

3. Please post output of **lspci | grep Eth**

```
0000:00:10.0 Ethernet controller: National Semiconducto Corporation DP83815 (MacPhyter) Ethernet Controller
```

4. Please post output of **route -n**

```
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
```

5. Please post output of **cat /etc/resolv.conf**
```
nameserver 137.165.4.2
nameserver 137.165.4.21
``` (I put these in manually)

6. Please post output of **cat /etc/network/interfaces**

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp
```

7. Please copy **entire** output of windows **ipconfig /all** command here

```

Windows IP Configuration
Host Name...: desktop
Primary DNS Suffix...:
Node Type...: Broadcast
IP Routing Enabled...: No
WINS Proxy Enabled...: No

Ethernet adapter Local Area Connection:
Connection-specific DNS Suffix...: nyc.rr.com
Description...: NETGEAR FA312 Fast Ethernet Adapter
Physical Address...: 00-A0-CC-A0-F2-6C
Dhcp Enabled...: Yes
Autoconfiguration Enabled...: Yes
IP Address...: 10.0.1.137
Subnet Mast...: 255.255.255.0
Default Gateway...: 10.0.1.1
DHCP Server...: 10.0.1.1
DNS Servers...: 10.0.1.1
Lease Obtained...: Sunday April 16, 2006 4:33:33 PM
Lease Expires...: Monday April 17, 2006 4:33:33 PM
```


Here is something interesting:

When I do **lsmod | grep mii**I get nothing.  But when I **ls /lib/modules/$(uname -r)/kernel/drivers/net/**, natsemi.ko shows up, and when I **sudo modprobe natsemi** it shows the driver as already loaded.

the output of **sudo mii-tool eth0** is ```
eth0: negotiated 100baseTx-FD flow-control, link ok
```

Thanks! :neutral: bk

---

### Post by OfficeLinebacker on 2006-04-17
have you tried powercycling the router?

---

### Post by bennyk on 2006-04-18
[QUOTE=OfficeLinebacker]have you tried powercycling the router?[/QUOTE]
yup.

---

### Post by mips on 2006-04-19
Try disabling APCI & APIC when the PC boots up.

Is the nic ISA, PCI etc ???
Is it onboard or a card ???

---

### Post by bennyk on 2006-04-19
[QUOTE=mips]Try disabling APCI & APIC when the PC boots up.

Is the nic ISA, PCI etc ???
Is it onboard or a card ???[/QUOTE]


MIPS THIS WORKED!!!!! =D> 

Awesome!  Now how do I get it to work with ACPI enabled? :rolleyes: 

thanks for your help,
bk

---

### Post by mips on 2006-04-21
You would add a line to the GRUB loader in order to do this.

File is /boot/grub/menu.lst

Some reference material for you:
[http://www.ubuntuforums.org/showthread.php?t=95157](http://www.ubuntuforums.org/showthread.php?t=95157)
[http://www.ubuntuforums.org/showthread.php?t=94989](http://www.ubuntuforums.org/showthread.php?t=94989)

---

