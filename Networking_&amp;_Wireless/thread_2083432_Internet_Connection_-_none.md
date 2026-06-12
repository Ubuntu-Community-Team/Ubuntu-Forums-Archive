---
title: "Internet Connection - none"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by JimS on 2012-11-12
I've been using Ubuntu since Breezy and have never experienced this problem.
I have a desktop PC which I built last year.
I'm connected to Internet by DSL modem/router.
3 other PCs are also connected and work fine.
I successfully ran #! (Crunchbang) for a while.
Also Puppy.
No connection problems with either.
Never installed M$ Windoz on this box.
No duel boot, just one distro installed at a time.

But when I install Xubuntu 12.04 there is no Internet connection.
I installed it twice, with #! inbetween.
Earlier Xubuntu worked fine in Virtual Box (in #!).

I ran the following two tools:

dmesg | grep eth
[    0.311293] i2c-core: driver [aat2870] using legacy suspend method
[    0.311294] i2c-core: driver [aat2870] using legacy resume method
[    2.228407] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc90000650000, 00:30:67:c7:a1:ce, XID 081000c0 IRQ 41
[    2.228409] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    7.862693] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.193545] r8169 0000:02:00.0: eth0: link down
[    8.193550] r8169 0000:02:00.0: eth0: link down
[    8.194910] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.943699] r8169 0000:02:00.0: eth0: link up
[    9.944074] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

and

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:67:c7:a1:ce  
          inet6 addr: fe80::230:67ff:fec7:a1ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:485216 (485.2 KB)  TX bytes:84844 (84.8 KB)
          Interrupt:41 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:759876 (759.8 KB)  TX bytes:759876 (759.8 KB)

When I run ifconfig with other distros installed
I get my IP address and they connect fine.
As you can see, no IP address here!

What do I need to do to get connected to the Internet.

Thanks in advance.

---

### Post by chuck_theobald on 2012-11-12
It would appear that dhcp is not working for you. Make sure that dhclient is installed, use:

aptitude search dhclient

to check the current installation status.

---

### Post by JimS on 2012-11-12
Thanks,

I tried your suggestion and got nothing,
but some very quick flashes of ????
and my prompt back.

Do I need something like
apt-get install dhclient
?

Rebooted - no change.

Go Ducks
class of 65

---

### Post by chuck_theobald on 2012-11-15
Sorry, my bad. dhclient is not the name of a package. To see the owner of the dhclient command, see the output of:

dpkg-query --search dhclient
< . . . bunch of other stuff . . . >
isc-dhcp-client: /sbin/dhclient

then use aptitude (or apt-get):

aptitude search isc-dhcp-client
i   isc-dhcp-client                                 - ISC DHCP client                                          
p   isc-dhcp-client:i386                            - ISC DHCP client                                          
p   isc-dhcp-client-dbg                             - ISC DHCP client (debugging symbols)                      
p   isc-dhcp-client-dbg:i386                        - ISC DHCP client (debugging symbols)   

The leading 'i' means the package has been installed.

UO class of '10 - 25 years late

---

### Post by itismike on 2012-12-11
Similar problems with Xubuntu 12.04 fresh install here. I think networking worked during the installation, but after rebooting eth0 doesn't respond:
```
# ifup eth0
error: "net.ipv6.conf.eth0.999.accept_ra" is an unknown key
failed to bring up eth0

# dmesg | grep eth

# lspci | grep Net
00:19.0 Ethernet Controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)

# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
...etc
```
Tried it on two separate machines and no network to speak of. Don't see any bugs filed under Xubuntu.

This is the first similar thread I've found. Did the original poster find a solution?

---

