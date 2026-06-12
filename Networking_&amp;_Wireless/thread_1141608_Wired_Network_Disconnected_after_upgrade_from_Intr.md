---
title: "Wired Network Disconnected after upgrade from Intrepid to Jaunty"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by ydony on 2009-04-28
I'm using a DSL modem connected through an Ethernet port to connect to the internet.
It used to work smoothly with Gutsy, Hardy and Intrepid but it hasn't been set up correctly during the upgrade to Jaunty and the automatic installation of Network Manager (I didn't use NM with previous versions).


 Initially there were no connections defined in Network Manager and "Wired - Device not managed" appeared in gray when right-clicking on the NM-applet icon.
I tried to solve it by changing managed=false to managed=true in /etc/NetworkManager/nm-system-settings.conf

After this change Network Manager automatically detected eth1 and the DSL connection but it's still unable to connect; I always receive the message "Wired Network disconnected - you're now working offline" on a black background.


Please help.
If it's possible to use Jaunty without Network-Manager, please tell me how to proceed.


 Hereafter some further information:


 sudo lshw -C network
[INDENT]   *-network
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth1
       version: 12
       serial: 00:0c:6e:40:4c:04
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=half firmware=N/A latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:e1:6c:84:2d:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/INDENT] ifconfig
[INDENT] eth1      Link encap:Ethernet  HWaddr 00:0c:6e:40:4c:04
          inet6 addr: fe80::20c:6eff:fe40:4c04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:458 (458.0 B)  TX bytes:3848 (3.8 KB)
          Interrupt:22lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:67488 (67.4 KB)  TX bytes:67488 (67.4 KB)
[/INDENT] dmesg | grep eth
[INDENT] [    1.739081] Driver 'sd' needs updating - please use bus_type methods
[    1.739098] Driver 'sr' needs updating - please use bus_type methods
[    3.818844] skge eth0: addr 00:0c:6e:40:4c:04
[    9.771834] udev: renamed network interface eth0 to eth1
[   32.913429] skge eth1: enabling interface
[   32.917093] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   35.180253] skge eth1: Link is up at 10 Mbps, half duplex, flow control none
[   35.180454] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   45.480009] eth1: no IPv6 routers present[/INDENT]
 cat /etc/network/interfaces
[INDENT] auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider


auto eth1
iface eth1 inet manual
[/INDENT]cat /etc/NetworkManager/nm-system-settings.conf
[INDENT] [main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
[/INDENT]Thanks

---

### Post by Iowan on 2009-04-28
I'm still a couple of versions behind, so dunno if Jaunty is using */etc/network/interfaces* file differently. >    The manual Method
       This method may be used to define interfaces for which no configuration
       is done by default. Such interfaces can be configured manually by means of up and down commands or /etc/network/if-*.d scripts.
 I'm used to seeing **dhcp** or **static** instead of **manual**.

---

### Post by bdoserror on 2009-04-29
I have a similar problem.  I had working, static IP network in 8.04.  Upgraded to 9.04 and now it shows up as disconnected, and the Wired connection list is empty and I can't add a new connection for eth1.  However, my network actually works.

```

_mtotman@joker:/usr$ sudo lshw -C network_
  *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 02
       serial: 00:22:15:67:60:78
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.3-0 ip=192.168.1.83 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:73:7b:18:7b:d5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

_mtotman@joker:/usr$ ifconfig_
eth1      Link encap:Ethernet  HWaddr 00:22:15:67:60:78  
          inet addr:192.168.1.83  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe67:6078/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:17813571 (17.8 MB)  TX bytes:4434059 (4.4 MB)
          Memory:f9fc0000-f9fe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:832 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2382670 (2.3 MB)  TX bytes:2382670 (2.3 MB)

_mtotman@joker:/usr$ dmesg | grep eth_
[    1.351117] Driver 'sd' needs updating - please use bus_type methods
[    1.351123] Driver 'sr' needs updating - please use bus_type methods
[    4.534731] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:22:15:67:60:78
[    4.534733] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    4.534765] 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: ffffff-0ff
[    9.608369] udev: renamed network interface eth0 to eth1
[   13.861229] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   15.304891] 0000:00:19.0: eth1: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   15.304894] 0000:00:19.0: eth1: 10/100 speed: disabling TSO
[   15.305497] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   26.168027] eth1: no IPv6 routers present
mtotman@joker:/usr$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
    address 192.168.1.83
    netmask 255.255.255.0
    gateway 192.168.1.50

_mtotman@joker:/usr$ cat /etc/NetworkManager/nm-system-settings.conf_
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

---

### Post by martinbures on 2009-04-29
Someone at work upgraded from 8.10 to 9.04 and they are having the same problem.  They are using a wired connection.  When he logs-in, the network manager icon shows two green spheres and the swirl is running like it wants to connect but just spins forever.

ifconfig yields an eth0 interface but there is no ip address assigned to it.

I tried bringing it down and back up again but nothing.

---

### Post by ydony on 2009-05-03
I tried to solve the problem by using either **dhcp** or **static** options but it didn't work.
I also have the NM applet icon showing the two green spheres until it stops and gives the message "Wired network disconnected"

Since I had no problems in previous versions and Network Manager was not installed, does anyone know if it's possible to also use Jaunty without Network Manager and how to do it (commands, configuration, ...) ?

---

### Post by ZeroError on 2009-05-03
You could try uninstalling network-manager through Synaptic or apt and using [WICD.]("http://wicd.sourceforge.net/")
I don't know if that will help, but you should give it a try.

But it should be possible to use Jaunty without Network Manager.
__

---

### Post by GabrielWolff on 2009-05-04
I got the same thing: eth0 is greyed out.
Funny thing is
1) It *did* work before, even after the upgrade
2) with the live CD it still works

Any suggestions?

---

### Post by SabreWolfy on 2009-05-04
I'm experiencing the same issues and it's very frustrating. I have three desktop machines at various locations which are permanently wire-connected to the 'net. Over a period of a few days, all three of them are dead on the 'net, which means that it is not even possible to restart them remotely. I need to get physical access to each one to do a hard reset. This has something to do with DHCP I think and is new in Jaunty. I certainly did not experience this with Gutsy, Hardy or Intrepid. I'm not a networking expert, so I stand corrected on this, but I think it has something to do with renewing the IP address on the LAN:

```

May  4 03:37:40 XXX NetworkManager: <info>  DHCP: device eth0 state changed renew -> expire 
May  4 03:37:40 XXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  4 03:37:40 XXX NetworkManager: <info>  DHCP: device eth0 state changed expire -> preinit 
May  4 03:37:45 XXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May  4 03:37:50 XXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May  4 03:38:00 XXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May  4 03:38:11 XXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May  4 03:38:22 XXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May  4 03:38:32 XXX dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May  4 03:38:41 XXX dhclient: No DHCPOFFERS received.
May  4 03:38:41 XXX dhclient: No working leases in persistent database - sleeping.
May  4 03:38:41 XXX NetworkManager: <info>  DHCP: device eth0 state changed preinit -> fail 
May  4 03:38:41 XXX NetworkManager: <info>  (eth0): device state change: 8 -> 9 
May  4 03:38:41 XXX NetworkManager: <info>  Marking connection 'Auto eth0' invalid. 
May  4 03:38:41 XXX NetworkManager: <info>  Activation (eth0) failed. 
May  4 03:38:41 XXX NetworkManager: <info>  (eth0): device state change: 9 -> 3 
May  4 03:38:41 XXX NetworkManager: <info>  (eth0): deactivating device (reason: 0). 

```

And from then on it's dead. Grrr!

Maybe [this]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/123650") bug (scroll to the bottom)? Workaround posted, but I haven't tested it yet. Also [this]("https://bugs.launchpad.net/ubuntu/+bug/359984") one.

Most likely, though, that [this]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368709") is the one.

(See also [this]("http://ubuntuforums.org/showthread.php?t=1144510") thread dealing with wireless disconnecting.)

---

### Post by connor4312 on 2009-05-04
Me having same problem too :-P

---

### Post by morgengenuss on 2009-05-04
please try creating a new user on your machine and then try to connect to your network again.
(i had the same issue, i'm still trying to figure out what changed from intrepid to jaunty that causes the bug.)


edit: it turned out it was sufficient to delete the keyring, something didn't go too well with the dist-upgrade there... (rm ~/.gnome2/keyrings/*)

---

### Post by painterh on 2009-05-08
Hi; I seem to have a similar issue with wired networking.  I have upgraded my main machine to 9.04, but I did it over a period of a couple of weeks.  What I mean is, I have been running intrepid x64 since beta, and recently added jaunty repos to my sources.list file.  Over the last couple of weeks I had been getting a large number of updates every day with no problem.  Then two days ago the update manager said there was a distribution upgrade available so I said yes, and installed all updates (except for lilo, I prefer grub).  All was well until I shut down that night and started up the next morning.  Bam, no wired network, what so ever.  Not only did I not have wired network on my desktop, but all the other computers on my home network lost networking as long as my ethernet cable was connected to the router.  I have to keep it disconnected till I sort this out.  Does anybody know what they changed in the final release of Jaunty that screwed so many people's networking?  I am happy to provide any info I can regarding my network config if anyone can help.  Thanks in advance.

---

### Post by claus on 2009-05-09
I'm basically having the same issue w/ Jaunty, the only difference being that my wired connection (auth0) only works *sometimes*. When I boot up my PC, sometimes it's there, sometimes it isn't. (And if it isn't, I haven't found out what to do about it except rebooting. Then the connection is there alright, at least most of the time. Otherwise I have to reboot again, until I have a connection.) Did anyone experience this very behaviour as well? (I upgraded online from Intrepid, which went flawlessly. Under Intrepid, I never experienced this kind of behaviour.)

TIA,

Claus

---

### Post by painterh on 2009-05-10
I got up this morning and typed ifconfig into a terminal, copied and pasted the MAC address of my network card into the network manger dialog box for setting up a new wired network, and I now have connection.  I don't know what changed, because I tried this several times yesterday with no success.  Anyway, my issue seems to have righted itself.  I hope others have a similar outcome.  Thanks

---

### Post by zapree on 2009-05-10
Ive got a similar problem, at first it diddnt work at all.  It was gray, but i went into manual config and just added the eth0 into my network (the same one i had before) then rebooted and now it works.  The only thing is that it will disconnect randomly.  I can just go and click on the disconnect icon and enable auto eth0 again, but i have no idea why it just randomly decided to disconnect and then un enable auto connect.

---

### Post by ravenax on 2009-05-11
i'm having the same problemm... the connection just exists for 10mins n then whaaaammmm!!!!:confused:

---

### Post by ravenax on 2009-05-11
hey i think something kinda worked out for me...:KS

i read this article on WICD network manager(cuz i read somewhere only WICD will work on jaunty:confused: err...?) - [http://www.yousaytoo.com/bearisusanto/wicd-network-manager/28907]("http://www.yousaytoo.com/bearisusanto/wicd-network-manager/28907")

there it was written
> TROUBLESHOOTING

If Wicd **fails to connect** after you install it, **make sure that the only entry in your /etc/network/interfaces file i**s

    [I]auto lo
    iface lo inet loopback[/I] 

so i edited the /etc/network/interfaces file as above n ran WICD, it DIDN'T work for me(after restart also), cuz my network got disconnected a million times after doing this.

then to connect to my n/w anyway i ran 

> sudo pon dsl-provider

to my suprise it DIDN'T GET DISCONNECTED! 

been stable for the past 2hrs anyway!! :)

PS: I dunno what actually happened!!!:confused:

---

### Post by ravenax on 2009-05-11
ok it doesn't work that way... sorry!!! ](*,) it's getting disconnected like mad now!!

---

### Post by Lechatelier on 2009-05-12
I have two computers connected to the same router. One runs ubuntu 8.04 and the other 9.04 I keep both systems up to date, i.e. install all recommended updates. Yesterday both computers worked fine. Today the 8.04 still has a normal connection while the 9.04 fails to connect to internet The network manager (0.7.0.100) reports "device not managed" for the ethernet card.
Hardware is ok since I could make a brief connection to internet.
Regards

---

### Post by Lechatelier on 2009-05-12
I have just made another test. 

I booted the computer from the 9.04 live cd and could connect to internet without any problem. This shows IMHO that the problem could be with some of the updates. Hope this my help.
Regards.

---

### Post by SabreWolfy on 2009-05-15
> **Lechatelier said:**
> I have just made another test. 

I booted the computer from the 9.04 live cd and could connect to internet without any problem. This shows IMHO that the problem could be with some of the updates. Hope this my help.
Regards.

I've had a desktop machine running for a few hours off the Jaunty Live CD spontaneously disconnect from wired ethernet.

---

### Post by ydony on 2009-05-16
It seems I eventually solved my issue :p by:

1. Uninstalling Network-Manager (using Synaptic Package Manager)
2. Installing Wicd (.deb package downloaded using Windows :cry:)
3. Using the "sudo pon dsl-provider" command

But:

1. I have to use the "sudo pon dsl-provider" command each time I startup my computer :neutral:; how should I do to make this plugin load automatically at startup ?

2. I'm pretty sure Wicd is actually useless because it always indicates "Not connected" in its stauts bar :confused:

kr

---

### Post by H.K.Murmu on 2009-05-16
1:-system----adminstration------user and groups

2:-In user setting select user-----properties---check the box "connect to internet using modem" and "connect to wireless and ethernet networks" then close

3:- open network manager applet from panel under DSL ---ADD---Edit DSL connection-----in tab DSL provide internet userid and password and under tab IPv4 setting select "automatic pppoe" and then close(perhaps require restart system, not sure)

4:-In panel left click network manager applet and click the radio button

5-now you are connected to internet through Network manager Applet

if you are upgraded through internet and still there is problem the install fresh jaunty ( dont upgrade) 

Best of luck

---

### Post by ydony on 2009-05-16
I found the solution: I had to use the "sudo pppoeconf" command.


 Pending questions:
1. Why hasn't it been set up correctly while upgrading to Jaunty ?
2. Why is it documented for previous versions only (up to Intrepid)?

---

### Post by Lechatelier on 2009-05-16
My problem appears to have healed itself. I hope it does not reappears in the future.
Regards

---

### Post by s1500 on 2009-05-18
Yesterday, just trying to fix my printer, I too ran into this dreaded problem(ie no networking happens). I got it so far as to have it fail on dhclient, where it just wouldn't grab an IP address. Looks like I got my addresses wrong. But how the heck did NetworkManager in its buggy state(buttons dont respond, etc) get included in the updates?

---

### Post by SabreWolfy on 2009-05-29
I tried [this]("http://ubuntuforums.org/showpost.php?p=7353186&postcount=4") and I'm waiting to see if it fixed the problem.

---

### Post by SabreWolfy on 2009-05-30
More discussion of DHCP and Jaunty, etc. in [this]("http://ubuntuforums.org/showthread.php?p=7346682#post7346682") thread.

---

