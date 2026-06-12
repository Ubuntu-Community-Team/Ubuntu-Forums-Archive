---
title: "Network connection works, internet doesn't"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by loneprairie on 2006-06-29
Hi all,

I've read through alotta threads but none seem to hit on this problem exactly. I set up 6.06 with no trouble, I can connect to my Win2k server, I can print over the network, but the internet does not work. The net works on all the Windows machines on the network also.  With the ubuntu box, I can ping other computers on the LAN but no address on the internet.

PC <-> Dell Powerconnect 2016 switch <-> Cisco 837 DSL router (the DHCP server)

I've tried the ifdown/up commands and the IPv6 toggle true in Firefox with no luck.

Any ideas?

Thanks,
e.

---

### Post by beerorkid on 2006-06-29
here is the orig thread which had some troubleshooting on it before they recomended a post here

[http://ubuntuforums.org/showthread.php?t=204902](http://ubuntuforums.org/showthread.php?t=204902)

---

### Post by ifican on 2006-06-29
You stated earlier that your machine pulled a dhcp address correct? If so can you ping your gateway, then past it i.e. any other IP on the internet. If that goes through then i see if you can ping via name, thereby showing you can resolve DNS. It may be something as simple as your machine is have trouble with your DNS passthrough by your router, just a hypothesis right now.

---

### Post by loneprairie on 2006-06-29
I can ping the gateway but nothing beyond that point.  I checked my /etc/resolv.conf after reading some more internet problem threads and it shows my two DNS addresses (which the box picked up on its own).  I cannot, however, ping those addresses.  Is it possible my Cisco 837 router is only saying "yes" to the Windows boxes and discriminating against the Ubuntu?

Thanks,
e.

---

### Post by beerorkid on 2006-06-29
K talked with the resident linux god here at work.

try entering this IP address into firefox

82.211.81.186    this is the IP addy of these forums.

if that works there is a problem with your box using your resolv.conf

It is possible that the router has been set up to not allow pings to come back or something

---

### Post by takakia on 2006-06-30
Hi beeorkid,

I had a similar problem and when I put the IP address of the ubuntu forums, it worked for me. But I am not able to go into the internet with domain names.  Any help for how to add resolv.conf would be great.

thank you.

---

### Post by beerorkid on 2006-06-30
hi takakia (me waving at screen)  he he

saw ya over on this thread: [http://ubuntuforums.org/showpost.php?p=1198082&postcount=6](http://ubuntuforums.org/showpost.php?p=1198082&postcount=6)

looks like a good idea, I just asked a local linux guru here at work and he suggested the IP address.  But from that post:
> if you're using a static ip address you should add your dns server(s) to /etc/resolv.conf

gksudo gedit /etc/resolv.conf

you can probably use your router as a dns proxy so add the following line:

nameserver 192.168.1.1

...and save sanges

if this doesn't work you can put your ISP's dns servers in your resolv.conf

---

### Post by Sud0 on 2006-06-30
I have the same problem with Dapper,

The Internet worked with the Live CD what I got directly from Canonical Ltd. (Ubuntu 6.06 LTS Dapper Drake) so then I installed Dapper, and the internet worked still but not for long, after I rebooted and logged into Windows a couple of times, Dapper ceased to connect to my internet, after I rebooted again GRUB wouldn't load it came up with Error Code 15, so that left me helpless without anything.

Once this happened, I pulled out my System Recovery Disk, thankfully windows was okay, I then deleted the partitions for Dapper and installed it again, but... the internet STILL won't work..i've tried configuring it via System -> Administration -> Network, enabling eth0 as the default gateway and enabling eth0 itself (it automatically enabled) but as soon as I press OK it goes back to setting the gateway to nothing.

I then opened up terminal, and typed in ifconfig, but i find something called a Loopback Device :/

eth0 works perfect, but I think lo is stopping it from working.

Any ideas?

- sud0

---

### Post by loneprairie on 2006-06-30
No dice on the ubuntu forums IP in Firefox.  I double checked and I can ping outside addresses from the Windows machines so the router allows it.  This is just weird.

Stumped,
e.

---

### Post by mips on 2006-06-30
What network card do you have, lspci -v will tell you ?

---

### Post by loneprairie on 2006-06-30
3com 3c905C-TX

---

### Post by mips on 2006-06-30
Do a search here for 3c905 and see if their are similair issues.

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

### Post by Sud0 on 2006-06-30
[QUOTE=mips]What network card do you have, lspci -v will tell you ?[/QUOTE]
Mips: I done a ipconfig /all on windows and got this through:

```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : ADVENT7086
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : lan

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : lan
        Description . . . . . . . . . . . : SiS 900-Based PCI Fast Ethernet Adap
ter
        Physical Address. . . . . . . . . : 00-16-EC-03-FE-5B
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 172.141.66.251
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . : 81.145.241.35
        DHCP Server . . . . . . . . . . . : 10.0.0.138
        DNS Servers . . . . . . . . . . . : 10.0.0.138
                                            205.188.146.145
        Lease Obtained. . . . . . . . . . : 30 June 2006 21:27:13
        Lease Expires . . . . . . . . . . : 01 July 2006 21:27:13
```

I couldn't honestly tell you what it says in Ubuntu because i can't write to my Media drive haha... but there you go.

---

### Post by mips on 2006-07-01
I would like to see the rest of the output from linux.

Looks like your router is in bridged mode but that should not be the issue.

---

### Post by takakia on 2006-07-05
ifconfig eth0
> Link encap:Ethernet  HWaddr 00:0A:E4:A1:6B:1B
          inet addr:147.8.76.240  Bcast:147.8.76.255  Mask:255.255.255.0
          inet6 addr: 2002:9308:80aa:4:20a:e4ff:fea1:6b1b/64 Scope:Global
          inet6 addr: fec0::4:20a:e4ff:fea1:6b1b/64 Scope:Site
          inet6 addr: 2001:ce0:2:111:20a:e4ff:fea1:6b1b/64 Scope:Global
          inet6 addr: fe80::20a:e4ff:fea1:6b1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11806 errors:1 dropped:0 overruns:0 frame:0
          TX packets:572 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3105265 (2.9 MiB)  TX bytes:48275 (47.1 KiB)
          Interrupt:10 Base address:0xa800


 lspci | grep Eth
> 0000:02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

route -n
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
147.8.76.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         147.8.76.200    0.0.0.0         UG    0      0        0 eth0



cat /etc/resolv.conf

> search hku.hk
nameserver 147.8.237.11
nameserver 147.8.231.201

sudo cat /etc/network/interfaces
> auto lo
iface lo inet loopback


iface eth0 inet static
address 147.8.76.240
netmask 255.255.255.0
gateway 147.8.76.200

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf



auto eth0

cat /etc/dhcp3/dhclient.conf

> # Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

Even I am having the same problem.  Here's the output of the above commands.  Any suggestions ?

---

### Post by mips on 2006-07-05
takakia,

Please hash out the 147.8.xxx.xxx addresses for security reasons.

Is the netmask, 255.255.255.0 correct ?

Try disabling IPv6.

Secondly do a search for "8139" in these forums as there are some known issues with that LAN chipset.

---

### Post by mips on 2006-07-05
[QUOTE=Sud0]
[code]
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 172.141.66.251
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . : 81.145.241.35
        DHCP Server . . . . . . . . . . . : 10.0.0.138
        DNS Servers . . . . . . . . . . . : 10.0.0.138
                                            205.188.146.145
[/QUOTE]

Your config looks a bit weird but it was obtained via dhcp so I dunno.

Can you ping 81.145.241.35 ? Also configure this address as your default gateway in Ubuntu.

Tried disabling IPv6 yet ?

---

