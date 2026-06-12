---
title: "Ubuntu 10.04 wired connection problem"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by dark.gixxer on 2010-10-17
Hi all !

I installed ubuntu 10.04 a while ago (didn't use it since, which is why i'm coming to you only now).
Yesterday i discovered i had no internat connection (i think it never worked).
My configuration is :
- dual boot (ubuntu/windows xp)
- network device realtek 8168/8111 Giga

i did some trys since yesterday with no result. I have a wired connection, perfectly working within windows. But nothing in ubuntu.

I got rid of the avahi entry in following ifconfig with no result. eth0 still not connects.

I tried to configure /etc/network/interfaces. Today it's like that :
```
auto lo
iface lo inet loopback

auto eth0
iface etho inet dhcp
```[I](I wrote this from my memory, please forgive any mistake)
[/I]
I tried also to remove lo, and left only the eth0 entry, with no result.


Here is the result of some commands :
```
**lspci -nn**
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:5c:c3:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:4d:5c:c3:18  
          inet addr:169.254.6.77  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:29 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```When trying to disable/reenable eth0 with ifup/ifdown or ifconfig eth0 down and ifconfig eth0 up, something like this shows up

```
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```I'm really out of ideas. Would appreciate your adives and opinions.

Thx !

---

### Post by Lazaruss on 2010-10-17
dont delete lo, it's your loopback interface needed for localhost...

it appears that you possibly have DHCP not working, so you dont get an ip address when you connect...

What are you connecting to? router?

---

### Post by dark.gixxer on 2010-10-17
Thanx for your reply, and for informations about "lo".

I'm in france, connection to Free ISP thru an ADSL box, configured thru a web interface. The router function of the box is activated, and DHCP is also activated.

About dhcp, i searched this morning for it and found dhcpclient, but no dhcpd or dhcp3-server.

Also forgot to say that the **route **command shows nothing but its header.

---

### Post by dineshs on 2010-10-17
> 05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
try these links
[http://ubuntuforums.org/showthread.php?t=1480328&page=2](http://ubuntuforums.org/showthread.php?t=1480328&page=2)
[http://wiki.hetzner.de/index.php/Installation_of_r8168_network_driver](http://wiki.hetzner.de/index.php/Installation_of_r8168_network_driver)
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)> I wrote this from my memory, please forgive any mistakeThere is one
> auto lo
iface lo inet loopback

auto eth0
iface [COLOR="Red"]etho [/COLOR]inet dhcpit should be eth0 not etho:)
Note:If you are using 10.04 use network manager to configure manual IP.Your /etc/network/interfaces should only contain```
auto lo
iface lo inet loopback

```
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)

---

### Post by dark.gixxer on 2010-10-17
Thanks !
The mistake was actually a typo :)

I'll try to download the realtek driver, but already followed a method for this (not updating driver though) with no luck.

About the static ips, i' rather have my adress through dhcp.

Thanks for the links ! I try this now :D

---

### Post by dark.gixxer on 2010-10-17
Thanks a lot ! It worked ! I'm writing from ubuntu ! :D

I saw some threads here and there about this driver problem and followed a procedure that did not help, but this link you gave me fixed everything.

The **golden** link : [http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

But now, with the driver i downloaded it's even simpler, no need to follow all the steps.
I only did the first (rmmod r8169) but it was not necessary. The driver comes with a script autorun.sh that does everything :
- unloads previous driver;
- build driver
- install and binds driver.

Just after the autorun.sh run, i rebooted my computer then entered the test command and saw the awaited line :D

```
gixxer@zeus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:5c:c3:18  
**          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0**
          inet6 addr: fe80::21a:4dff:fe5c:c318/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2364 (2.3 KB)  TX bytes:4637 (4.6 KB)
          Interrupt:29 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
```

Thanks dinesh and Lazaruss for your help, i a ppreciate very much !

---

### Post by dineshs on 2010-10-17
Glad it is working.Thanks to nausicaavow

---

### Post by dark.gixxer on 2010-10-18
Yes i went to his thread to thank him too :)
It bumped the thread too, which is not a bad idea, as it may help a few more people i think.

---

