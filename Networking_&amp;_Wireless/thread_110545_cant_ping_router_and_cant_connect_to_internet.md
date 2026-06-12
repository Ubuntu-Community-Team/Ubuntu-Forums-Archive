---
title: "cant ping router and cant connect to internet"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by D1G1T4L on 2005-12-31
i cant seem to ping my router and cant connect to internet
when i do ifconfig eth0
it shows eth0 info etc
but it doesnt show inet address that is assigned to the card

even though my router shows that it assigned an address to it!

when i try assising static ip, the internet still doesnt work

someone please help

---

### Post by drfalkor on 2005-12-31
try this:
sudo dhclient

---

### Post by ninotob on 2005-12-31
Forgive me if it's a too basic question, but how are you viewing your router information page -- are you using a second computer or looking at the lights on the front of your router?

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=ninotob]Forgive me if it's a too basic question, but how are you viewing your router information page -- are you using a second computer or looking at the lights on the front of your router?[/QUOTE]

second computer

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=drfalkor]try this:
sudo dhclient[/QUOTE]

i have already tried that, it cant discover a dhcp offer after trying several times

---

### Post by D1G1T4L on 2005-12-31
when i do sudo dhclient eth0, i think it tries searching and then says no dhcpoffers
no working leases in persisten database-sleeping

---

### Post by harisund on 2005-12-31
Are you using a wireless connection? Or is it a wired connection? 

Can you post the content of your ifconfig eth0 here?

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=harisund]Are you using a wireless connection? Or is it a wired connection? 

Can you post the content of your ifconfig eth0 here?[/QUOTE]

wired connection

ifconfig eth0
```

eth0  Link encap:Ethernet HWaddr 00:40:05:7c:01:EC
        UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
        RX packets:0 errors:0 dropped: 0 frame:0
        TX packets: 0 (all 0s too)
        collison 0    txqueuelen:1000
        Rbx bytes:0 (0.0 b)  TX bytes: 0   (0.0 b)
        Interrupt: 10  Base address: 0xdc00

```

its wierd, its not showing inet address
and when i ping my router it says connect: Network is unreachable

---

### Post by harisund on 2005-12-31
Are you sure your hardware is detected? Do you know what NIC you have? 

Anyway, I would give the following a try
sudo ifconfig eth0 down
sudo ifconfig eth0 up
dhclient eth0

You should be able to see the light (normally it is green.) glow on the network interface card in your computer. Also, make sure of the other obvious settings, such as a DHCP Server is enabled on your router, there is no problem with your MAC address being blocked or something and so on..

---

### Post by drfalkor on 2005-12-31
if you get a sleeping message when you do a: sudo dhclient eth0, the router is not connected up to the internett .

EDIT: It's like that for me !

---

### Post by harisund on 2005-12-31
even if the router is not connected to the network, shouldn't it still give out an ip address if it has a running DHCP server? The computers will still be connected, right? Just not to the internet. Or will that result in a sleeping error?

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=harisund]Are you sure your hardware is detected? Do you know what NIC you have? 

Anyway, I would give the following a try
sudo ifconfig eth0 down
sudo ifconfig eth0 up
dhclient eth0

You should be able to see the light (normally it is green.) glow on the network interface card in your computer. Also, make sure of the other obvious settings, such as a DHCP Server is enabled on your router, there is no problem with your MAC address being blocked or something and so on..[/QUOTE]

yes hardware is detected, i even ran some command that shows the name of my card. i tried other cards too, its same thing
i tried doing ifconfig eth0 down and up adn then dhclient eth0, it keeps giving me DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8, then it says same thign but interval 14, interval 8 again, interval 10, interal 11, interval 10

then it shows agaqin
NO DHCPOFFERS received
No working leases in persistent database - sleeping

and yes the green light is working on the card!
no mac address blocking or anything, i have a windows and another ubuntu box that work fine right now using the same router

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=drfalkor]if you get a sleeping message when you do a: sudo dhclient eth0, the router is not connected up to the internett .

EDIT: It's like that for me ![/QUOTE]

the router is connected to internet, how do u think i am posting right now?? lol i have 2 other computers connected to the router as well

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=harisund]even if the router is not connected to the network, shouldn't it still give out an ip address if it has a running DHCP server? The computers will still be connected, right? Just not to the internet. Or will that result in a sleeping error?[/QUOTE]

the router is connected to internet! i am connected right now through other computer

---

### Post by D1G1T4L on 2005-12-31
someone please help, this is really frustrating :(

---

### Post by harisund on 2005-12-31
Hmm..looks like everything is all right indeed.. sorry then .. the last thing that comes to my mind is of course the Microsoft way, restart ! otherwise I am at a loss

---

### Post by drfalkor on 2005-12-31
[QUOTE=D1G1T4L]the router is connected to internet, how do u think i am posting right now?? lol i have 2 other computers connected to the router as well[/QUOTE]

lol, sorry - my bad. I'm a bit confused ! :D

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=harisund]Hmm..looks like everything is all right indeed.. sorry then .. the last thing that comes to my mind is of course the Microsoft way, restart ! otherwise I am at a loss[/QUOTE]

i restarted 100 time now =(

---

### Post by D1G1T4L on 2005-12-31
this dude has the same problem as me!!!1

[http://www.ubuntuforums.org/showthread.php?t=95489&page=2](http://www.ubuntuforums.org/showthread.php?t=95489&page=2)


but no one solved it either, where are ubuntu gurus at!??!

---

### Post by D1G1T4L on 2005-12-31
i also reinstalled like 10 times and tried 3 different network cards

and the funny thing is router sees the ip and hardware address of the ubuntu box, however i cant ping the router or anything from the box itself, and how come i dont see the inet address when i do ifconfig eth0

---

### Post by joe3eagles on 2005-12-31
You're not alone.  I have the same problem with almost exactly the same command outputs, although I'm on a wireless router.  I suppose somebody may eventually come up with other ideas to try.

---

### Post by drfalkor on 2005-12-31
sudo iptables --flush
(what about now?)
sudo dhclient
(now ?)

I dunno if the --flush thingy is a wise thing to do, I was just looking up in the iptables manual, haven't tryed it before.

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=joe3eagles]You're not alone.  I have the same problem with almost exactly the same command outputs, although I'm on a wireless router.  I suppose somebody may eventually come up with other ideas to try.[/QUOTE]


i am on wireless router too but its directly connected, my other windows xp computer is wirelessly connected

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=drfalkor]sudo iptables --flush
(what about now?)
sudo dhclient
(now ?)

I dunno if the --flush thingy is a wise thing to do, I was just looking up in the iptables manual, haven't tryed it before.[/QUOTE]

ok just tried that, nothing changed

---

### Post by joe3eagles on 2005-12-31
[QUOTE=D1G1T4L]i am on wireless router too but its directly connected, my other windows xp computer is wirelessly connected[/QUOTE]

If you're using a wireless router shouldn't you be using wlan0 instead of eth0 for the dhclient & ifconfig commands?

---

### Post by harisund on 2005-12-31
no no.. wlan0 is the default name for the wireless interface.. here the interface in question is the wired one, which by default is eth0..

---

### Post by harisund on 2005-12-31
Digital, one small question .. when you installed UBuntu on the machine did you have it connected? Did it get an IP address at that time?

---

### Post by zukakog on 2005-12-31
I've got the exact same problem.  Here's everything that I could come up with.

Keep in mind that I have 4 other computers connected to this router, and they can all access the network/internet just fine.

The machine in question works just fine when booted to Windows, so it's not a hardware/cable issue.

It should end up connected like this:

IP Address: 10.0.236-239.***
Net Mask:   255.255.252.0
Gateway:   10.0.236.1
DNS:         10.0.236.1

```
$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD flow-control, link ok
```

Note that there is no IP address.
```
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:6D:48:23
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

NIC type
```
$ lspci | grep Eth
0000:02:08.0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 83)
```

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

Pinging the gateway
```
$ ping 10.0.236.1
connect: Network is unreachable
```

```
$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:e0:b8:6d:48:23
Sending on   LPF/eth0/00:e0:b8:6d:48:23
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

```
$ cat /etc/network/interfaces
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
auto eth0
iface eth0 inet dhcp
```

I can't get my wireless up, but that's a different issue.
Under Configuration of network:1 it says that my driver is e100
```
$ sudo lshw -C network
  *-network:0 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@02:04.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:e0600000-e0600fff irq:10
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:6d:48:23
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=full firmware=N/A link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:e0603000-e0603fff ioport:4000-403f irq:11
```

e100 is loaded
```
$ lsmod
Module                  Size  Used by
...			...	...
e100                   32768  0
mii                     5248  1 e100
...			...	...
```

Any ideas?  I read through all 25 pages in this forum, and noticed quite a few people with the same issue.

Are you going to be our hero?

---

### Post by Sonique on 2005-12-31
Indeed, I too have a similar problem with my Sony Vaio C1VE, my router uses dhcp.

using zukakog's last post as a template, here is my outputs:

It should end up connected like this:
IP Address: 10.0.0.x
Net Mask: 255.255.255.0
Gateway: 10.0.0.2
DNS: 10.0.0.2

```

$ sudo mii-tool eth0
eth0: negotiated 100baseTx-HD, link ok

$ ifconfig eth0
eth0    	Link encap:Ethernet  HWaddr 00:00:86:3C:38:96
          	inet6 addr: fe80::200:86ff:fe3c:3896/64 Scope:Link
          	UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          	RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          	TX packets:55 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
          	RX bytes:7119 (6.9 KiB)  TX bytes:17478 (17.0 KiB)
          	Interrupt:9 Base address:0x4000 0000:01:00.0 

$ lspci | grep Eth
Ethernet controller: 3Com Corporation 3cCFE575BT Megahertz 10/100 LAN CardBus [Cyclone] (rev 01)

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

$ ping 10.0.0.2
connect: Network is unreachable

$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 7519
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:00:86:3c:38:96
Sending on   LPF/eth0/00:00:86:3c:38:96
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

```

---

### Post by Jeff12088 on 2005-12-31
Ubuntu gurus, get out here! Same exact problem here:
[http://ubuntuforums.org/showthread.php?t=110417](http://ubuntuforums.org/showthread.php?t=110417)

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=harisund]Digital, one small question .. when you installed UBuntu on the machine did you have it connected? Did it get an IP address at that time?[/QUOTE]
when i installed ubuntu it was trying to configure the network, it says "Network configuration has failed" your network is probably not using the dhcp protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly.

so it seems like ubuntu config cant detect my network, yet my router sees the ubuntu ethernet address and assigns a dynamic ip to it, how can this be

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=harisund]no no.. wlan0 is the default name for the wireless interface.. here the interface in question is the wired one, which by default is eth0..[/QUOTE]


yep

---

### Post by D1G1T4L on 2005-12-31
this is really frustrating, what can be the reason for inet addres not being shown/addressed

i dont get it

---

### Post by Lambert on 2005-12-31
Not to many ubuntu gurus, just users, many who have never seen a problem like this. But it's not that rare because there are a few of you with a similar situation.

If you would, I'll ask for some more output.

1st make sure the device is up
```
sudo ifconfig eth0 up
```

then run these commands and post output

```
sudo ethtool eth0
```

```
sudo mii-diag -Drv eth0
```



Something else to try. (this may not work for every driver as I'm attempting to turn on debugging for the driver. I know this works with the e100 driver)

find the driver your device is using

```
lsmod | grep mii
```

Now make sure the device is down

```
sudo ifconfig eth0 down
```

remove the driver

```
sudo modprobe -r e100
```(replace e100 with the driver being used by your nic)

now reinsert it with debugging turned on.

```
sudo modprobe e100 debugging=32
``` (=0 is no debuggin =32 reports the most verbose debugging messages you can use anything inbetween 1 and 32, the lower the number the less reported)

Now you need 2 terminals open. The first one run this command.

```
tail -f /var/log/messages
```

This command will continually scroll messages added to the log file messages. You may want to open a third terminal and run same command only with /var/log/syslog but I believe most debug messages will be in messages folder.

Now with debugging on bring up interface and dhclient. Look through the output of the other terminal for any errors or lines that look suspisicious. Anything from this output/file you feel necessary you can post here.

You can reverse this procedure to turn off debugging or on reboot driver will insert without debugging turned on.

---

### Post by mips on 2005-12-31
Can you people ping your loopback (lo0) interfaces ?

---

### Post by Jeff12088 on 2005-12-31
Cheers!
Mine worked magically after I restarted my gateway and replugged all the lines.
Of course I had to run
```
dhclient eth0
```
and I got a response...

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=mips]Can you people ping your loopback (lo0) interfaces ?[/QUOTE]


how do i do that? and wahts lo0 interface btw

---

### Post by D1G1T4L on 2005-12-31
btw my tail -f /var/log/mesages show

localhost kernel: Netdev WATCHDOG: eth0: transmit timed out
localhost kernel: eth0: link up, 100 Mpbs, full duplex, lpa 0x41E


so whats the reason for ifconfig not to show inet address under eth0 

??

---

### Post by zukakog on 2005-12-31
[QUOTE=mips]Can you people ping your loopback (lo0) interfaces ?[/QUOTE]

Actually I can't ping 127.0.0.1

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=zukakog]Actually I can't ping 127.0.0.1[/QUOTE]

i can ping 127.0.0.1

---

### Post by D1G1T4L on 2006-01-01
so anyone can help me or what? i dont know what to do

---

### Post by Lambert on 2006-01-01
[quote=D1G1T4L]btw my tail -f /var/log/mesages show

localhost kernel: Netdev WATCHDOG: eth0: transmit timed out
localhost kernel: eth0: link up, 100 Mpbs, full duplex, lpa 0x41E


so whats the reason for ifconfig not to show inet address under eth0 

??[/quote]

I was expecting more output then this. You didn't run all the commands, but with what you gave this is what I suggest.

open up this file

```
sudo gedit /boot/grub/menu.lst
```

Find the kernel section that you use. If you don't know type uname -r in terminal and it will tell you what kernel you're running.

You'll see this line but with your kernel version

```
kernel          /boot/vmlinuz-2.6.15-10-386 root=/dev/hda1 ro quiet splash

```

add to the end of the line    [I]acpi=off

[/I]save the file. This will turn off acpi power management but I found information saying that no internet connection and the netdev watchdog line is caused by acpi and solved when turned off.

Now reboot and test your connection.

Some of the posts had mixed ways of solving so if this doesn't solve it then try these.


1. open the file again, remove acpi=off and replace it with noapci, save and reboot.

2. if 1 doesn't work then open the file again and add both those statements to line *noapci acpi=off. save and reboot.*

---

### Post by rubenjavier on 2006-01-02
I have the same problem from a different point of view, my internet provider gave me a router with 8 static IP address that I can use, I have used all of them at the same time with windows machines (I assigned each machine a different IP address from the list my provider gave me and set the same gateway in all the machines) and everything worked fine. Then I used one of the static address with a Ubuntu machine and the rest with windows machines, again everything went well. Then I tried two ubuntu machines with static IP address and the rest for the windows machines, but only one machine connect to the internet, each time I reset the router the ubuntu machines conects at random, some times is one and sometimes is the other... but never both. I even tried turning off all the others windows machines and leaving just the two ubuntu machines with differents static IP address, but just one connects every time????
Why is this happening????
is there a way to send a command to the router to connect to it like when you ask a network connection to repair under windows?, maybe is something like that, both machines try do a request at the same time and only one connects before it reaches some kind of timeout, this is strange because the machines are using static IPs and not DHCP, and all the other windows machines with static IPs work just fine
Thanks in advance

---

### Post by D1G1T4L on 2006-01-02
[QUOTE=Lambert]I was expecting more output then this. You didn't run all the commands, but with what you gave this is what I suggest.

open up this file

```
sudo gedit /boot/grub/menu.lst
```

Find the kernel section that you use. If you don't know type uname -r in terminal and it will tell you what kernel you're running.

You'll see this line but with your kernel version

```
kernel          /boot/vmlinuz-2.6.15-10-386 root=/dev/hda1 ro quiet splash

```


thx i'll try t
add to the end of the line    [I]acpi=off

[/I]save the file. This will turn off acpi power management but I found information saying that no internet connection and the netdev watchdog line is caused by acpi and solved when turned off.

Now reboot and test your connection.

Some of the posts had mixed ways of solving so if this doesn't solve it then try these.


1. open the file again, remove acpi=off and replace it with noapci, save and reboot.

2. if 1 doesn't work then open the file again and add both those statements to line *noapci acpi=off. save and reboot.*[/QUOTe]


thanks i'll try that soon

---

### Post by D1G1T4L on 2006-01-02
[QUOTE=Lambert]I was expecting more output then this. You didn't run all the commands, but with what you gave this is what I suggest.

open up this file

```
sudo gedit /boot/grub/menu.lst
```

Find the kernel section that you use. If you don't know type uname -r in terminal and it will tell you what kernel you're running.

You'll see this line but with your kernel version

```
kernel          /boot/vmlinuz-2.6.15-10-386 root=/dev/hda1 ro quiet splash

```

add to the end of the line    [I]acpi=off

[/I]save the file. This will turn off acpi power management but I found information saying that no internet connection and the netdev watchdog line is caused by acpi and solved when turned off.

Now reboot and test your connection.

Some of the posts had mixed ways of solving so if this doesn't solve it then try these.


1. open the file again, remove acpi=off and replace it with noapci, save and reboot.

2. if 1 doesn't work then open the file again and add both those statements to line *noapci acpi=off. save and reboot.*[/QUOTE]


uname -r shows
2.6.12-9-386

what does acpi power management actually do? can u explain?

I TURNED IT OFF AND IT WORKED! THANK YOU VERY MUCH! omg

can u please explain what the hell it is and why does it mess around with my ethernet card and how come it doesnt happen to many others? thank you a lot! omg i am so happy

---

### Post by Lambert on 2006-01-02
First I'm glad to see your problem was solved. I learned something myself.

What is acpi? advanced configuration and power interface.

What does that mean?

ACPI specifies how a computer's basic input/output system, operating system, and peripheral devices communicate with each other about power usage.

It's a standard so the entire computer is on the same page to power consumption can be configured and controlled if that helps you understand it. The nic is an in/out device so there was just a conflict with acpi and the nic. 

Not knowing much about the nic there was probably a conflict in the driver and how it exchanges/interfaces with acpi. 

How does this affect things? It's possible your pc will consume more power as it's not being controlled by the os. Could be a problem on a laptop where longer battery life is desired. On a desktop, just consumes more power.

Why doesn't happen to others? Depends on the device and possible the age of it. Whether drivers were updated when the acpi standard replaced apm. (which is an older standard for power management)

Note my explanation may be flawed so anybody correct me where I'm wrong.

---

### Post by zukakog on 2006-01-10
[QUOTE=Lambert]
How does this affect things? It's possible your pc will consume more power as it's not being controlled by the os. Could be a problem on a laptop where longer battery life is desired. On a desktop, just consumes more power.

Why doesn't happen to others? Depends on the device and possible the age of it. Whether drivers were updated when the acpi standard replaced apm. (which is an older standard for power management).[/QUOTE]

:KS Bless you! :KS 

Turning off ACPI worked for me too.  The only problem is that for the majority of tasks, my laptop was running at around 700Mhz.  Now it is always running at 1.8Ghz.  My battery life sucks.

I'm updating my system now, and I noticed an update to ACPI.  I'm going to enable ACPI again and see if it will continue to work.  I'll keep you posted.

---

### Post by heftigrat on 2006-01-10
[QUOTE=rubenjavier]I have the same problem from a different point of view, my internet provider gave me a router with 8 static IP address that I can use...
...this is strange because the machines are using static IPs and not DHCP, and all the other windows machines with static IPs work just fine
Thanks in advance[/QUOTE]

Try posting a new thread, this sounds like a completely different issue than what the original poster is referring to.


(Very interesting thread though, VERY informative!  :D )

---

### Post by ashgromnies on 2006-01-11
I get the same message, however disabling ACPI did not seem to do anything... :(

---

### Post by dieselpower on 2006-01-15
I have the same problem. I have tried everything I can find including all 3 ways to turn of acpi. It seem like it is a bios problem to me. I have 6 computers connected to one router, set up with ubuntu server, dhcp3, shorewall, samba, and apache2 with php4. Only two computers can connect, a compaq armada 7400, and a desktop with a AMD Duron and some kind of TS-AKT4/A mobo. The others run ubuntu(2) Gentoo(1) and winblows Xtra Pokey pro SP2. I have switched NICs around and still only the same machines can connect. I have run the Gentoo live cd on all of them, the 2 machines boot up and I can ping google.com first thing without any setup, *with any of the nics.* On the others, eth0 is not set up automagicaly. And after I set it up, with either DHCP or staticaly, no matter what I do, I cannot even ping my router, No IP is set on eth0 and nothing works. *This is ALL with the same Gentoo cd*. I will try to change the bois settings and see if that helps. But I am at a loss as to what to do. Someone please jump in and keep me from having to be the allmighty saving ubuntu guru! If you need any of my logs or config files just let me know, I'll post. Just someone please help!

Lawrence

---

### Post by dieselpower on 2006-01-15
It's all working now! I hope all of your other problems are as simple as mine! I have two 5 port network hubs and one had quit working properly. Sometimes you gotta go all the way 'round the world to see what's behind you!

Lawrence

---

