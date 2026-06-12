---
title: "Odd IP Issue"
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by pkbarber on 2006-05-02
Hey,
So heres the deal.  I followed the "Wired Ethernet Troubleshooting Process" and found that when I get to the "route -n" command there is an interesting issue.  My router is configured at 192.168.0.1.  The response to route -n is 192.168.0.0.  I can ping the router on that machine and can access the routers admin page but it cant see anything outside of my network.  The "Destination" in that command should read my routers IP correct?  Ideas/solutions/threads are greatly appreciated.
PKB

---

### Post by gunderwood on 2006-05-02
Try just run command route sans the -n flag.

you should have a default route set to your router. 

I also suspect your issue may be more related to DNS, ensure that your nameservers have been set in you /etc/resolv.conf.

---

### Post by pkbarber on 2006-05-02
When I run route the destination reads 192.168.0.0 and the gateway 192.168.0.99... not the router.  And I dont know what to do with this string /etc/resolv.conf.  I ve found the folder but I dont know where to go from there.

---

### Post by gunderwood on 2006-05-02
[QUOTE=pkbarber]When I run route the destination reads 192.168.0.0 and the gateway 192.168.0.99... not the router.[/QUOTE]

Your routing table is definately messed up. a typical routing table looks like this. Where the router ius located at 192.168.1.1.

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

Basically what it tells us that any traffic to the local network 192.168.1.* is put on the local link. Any other traffic is sent to the router to be put out on the internet.

you're going to need to set up your routing table. Check the man pages for usage of the route command.

```

man route

```

[QUOTE=pkbarber]And I dont know what to do with this string /etc/resolv.conf.  I ve found the folder but I dont know where to go from there.[/QUOTE]

There is a resolvconf directory, this contains scripts used by a program called resolvconf which is supposed to automatically set up your nameservers. What I was actually refering to was a file called resolv.conf

```

cat /etc/resolv.conf 

```

Will show you the contents of the file. Ensure that your nameservers are listed in that file (you'll be able to find them on your routers admin interface) and once again the manpages are your friend here too. But until your routing issue is fixed it's a moot point because you can't reach anywhere out of the local network.

Hope this helps a little.

Greg

---

### Post by pkbarber on 2006-05-02
When I try to edit the route table (which im prob not doing correctly but what the heck ill give it a shot) it says: SIOCADDRT: Operation Not Permitted.  Thoughts?  Does this mean the command Im trying isnt a valid one?

---

### Post by Jason_25 on 2006-05-02
Sounds like your not using sudo.  It's a system-wide administration command so you have to be root.

---

### Post by mips on 2006-05-02
sudo route add default gw 192.168.0.1 dev eth0

---

### Post by pkbarber on 2006-05-02
That last sudo command went through.  The wrong ip is still there.  In "cat /etc/resolv.conf" it still says "nameserver 192.168.0.99"  However, now when I do a route -n the other gateway is there and the one i just put in (after a restart) is gone.  What is the correct command to completly release/flush/del all of the current ips?  THX

---

### Post by pkbarber on 2006-05-02
I failed to mention that it also fails two steps in the start up process: configuring network interface and connecting to the time server.  It never connected to the server but it did successfully configure the hardware. ERRR... Just restarted again and it got online, the right ips were in as well.  After another reboot its back to the wrong ips.

---

### Post by mips on 2006-05-02
Open your routers web interface and look at ALL the settings. Something here is very fishy.

You only have the one router on the network ? Tell us a bit more about your setup in detail.

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please copy **entire** output of windows **ipconfig /all** command here
7. Who is your ISP and provide a web link.

---

### Post by gunderwood on 2006-05-02
It sounds like there is something wrong with how the network is being configured. Configuration for any network interfaces is accomplished in the file ```
/etc/network/interfaces
``` 
There are manpage entries that explain the syntax of the network interfaces file. Your other option is to use the new network manager applet to automagically configure your wireless. I suspect if the interface is being setup through DHCP that there is something wrong with the router, or if it is being configured statically some important parameters are missing. 

Have you tried the Network Manager? It may be an  easy fix to your issue.

Greg :)

---

### Post by pkbarber on 2006-05-02
Mips - Can you think of a way to get all of this data to my windows box?  Thats a lot of typing.  I set up an SSH server and tried using Putty but it wont work.  Im looking for a usb thumb drive now...  Perhaps I configured the SSH server incorrectly but I wouldnt be surpirsed if the IP issue had something to do with it.  

Greg - It says command not found.  I tried "/etc/network/interfaces" and got a permission error so I ran "sudo /etc/network/interfaces" and got "command not found" which makes no since.

PKB

---

### Post by Jason_25 on 2006-05-02
Actually that makes perfect sense.  sudo doesn't know what to do with the name of a file.  You have to name an editor to open the file. Like nano.
```

sudo nano /etc/network/interfaces

```

---

### Post by gunderwood on 2006-05-02
[QUOTE=pkbarber]
Greg - It says command not found.  I tried "/etc/network/interfaces" and got a permission error so I ran "sudo /etc/network/interfaces" and got "command not found" which makes no since.

PKB[/QUOTE]


it's a text file you need to edit to tell the system how to setup your network cards.

```

cat /etc/network/interfaces

```

to view it, my bad.

Greg

---

### Post by pkbarber on 2006-05-03
Here is that file /etc/network/interfaces:

```

This file describes the network interfaces available on your system 
and how to activate them.  For more information, see interfaces(5).

The loopback network interface
auto lo
iface lo inet loopback

This is a list of hotpluggable network interfaces.
They will be activeated automatically by the hotpulg subsytem.
mapping hotplug
            script grep
            map eth1

iface eth1 inet dchp

iface ehto inet dchp

auto eth0

auto eth1

```

Whats with that eth0 and eth1?  I had a wifi card plugged in when i first built the box but took it out long ago.

---

### Post by gunderwood on 2006-05-03
[QUOTE=pkbarber]Here is that file /etc/network/interfaces:

...

Whats with that eth0 and eth1?  I had a wifi card plugged in when i first built the box but took it out long ago.[/QUOTE]

It looks like it still is configured for 2 interfaces, both of which use DHCP.
I assume from your comment you only have 1 network card in the box.

Can you run the following command and post the result please.

```

ifconfig -a | grep Ethernet

```

This will give a shortened print out of your interfaces.

```

lspci | grep Ethernet

```

will tell you what network cards have been detected in your PC.

If you've figured out a way to get all the files that mips asked fopr that'd be great. But otherwise get whatever output you can.

there was a line

> 
iface ehto inet dchp


Should be

```

iface eth0 inet dhcp

```

but I suppose it's probably a typo if you're typing in the output ...

Greg

---

### Post by pkbarber on 2006-05-03
ITs a typo, my bad. 
```

etho     Link encap:Ethernet  HWaddr 00:02:E3:0C:23:7A
eth1     Link encap:Ethernet  HWaddr 00:E0:4C:A7:3D:8A

``` 

Can I remove the wifi card's software, the second, from the system?  Delete its profile?  Or perhaps delete both and let the system detect the NIC?

---

### Post by pkbarber on 2006-05-03
lspci | grep Ethernet

```

0000:00:08.0 Ethernet controller: National Semicnductor Corportaion DP83815 (MacPhyter) Ethernet Controller
0000:00:12.0 Ethernet controller: VIA Technologies, INC. VT6102 [Rhine-II] (rev 74)

```

---

### Post by gunderwood on 2006-05-03
You have 2 network cards installed in the machine, more than likely the via one is the built in LAN. Pick one then comment out one of the lines

```

auto eth1   # or eth0 whichever you aren't using

``` 

then run the command

```

sudo /etc/init.d/networking restart

```

to restart the network. It should resolve an IP and set the gateway automatically.

Greg

---

### Post by pkbarber on 2006-05-03
Sorry newb... comment out?

---

### Post by pkbarber on 2006-05-03
And ive got the case open there isnt a built in NIC.

---

### Post by pkbarber on 2006-05-03
After restart the gateway is still wrong.  Granted, I didnt comment out the other line.

---

### Post by gunderwood on 2006-05-03
Put a # in front of the line. This in effect makes the line a comment and is ignored.

---

### Post by pkbarber on 2006-05-03
```

# auto eth1

```

correct or no?

---

### Post by gunderwood on 2006-05-03
yes

---

### Post by pkbarber on 2006-05-03
After the commenting out that line and restarting the network it works.  With 1 reboot: success.  2: FAILURE.  WHAT THE HECK ](*,) 
It had the correct GW the first time now it back to being wrong.

---

### Post by pkbarber on 2006-05-03
Its up for now...
1. Please post output of ifconfig eth0 (Depends on your interface number)
```
eth0      Link encap:Ethernet  HWaddr 00:02:E3:0C:23:7A
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:e3ff:fe0c:237a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:967822 (945.1 KiB)  TX bytes:164452 (160.5 KiB)
          Interrupt:16 Base address:0xa000

```
2. Please post output of lspci | grep Eth
```
0000:00:08.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)

```
3. Please post output of route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 et
```
4. Please post output of cat /etc/resolv.conf
```
pkb@LinuxBox:~$ cat /etc/resolv.conf
nameserver 192.168.0.1

```
5. Please post output of cat /etc/network/interfaces
```
pkb@LinuxBox:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

iface eth1 inet dhcp

iface eth0 inet dhcp

auto eth0



```
6. Please copy entire output of windows ipconfig /all command here
7. Who is your ISP and provide a web link.
Comcast [http://comcast.com/](http://comcast.com/)

---

### Post by gunderwood on 2006-05-03
Everything looks good now except your nameserver. Unless your router is also a DNS server. 

To find out if the issue is DNS try to ping [www.yahoo.com](www.yahoo.com), this will probably fail. Then try and ping 66.94.230.50 (yahoo's IP), this should work. If this is the case you will need to input your own nameservers. These can be found on your routers admin interface as either DNS or Nameservers. Or if you call your internet provider they can probably provide you the addresses of there DNS servers.

---

### Post by pkbarber on 2006-05-03
Thank everyone who helped.  It works fine now.  I really appreciate it!
PKB

---

