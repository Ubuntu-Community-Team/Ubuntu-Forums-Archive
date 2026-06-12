---
title: "network seriously unstable"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by strattonbrazil on 2006-06-25
I've been have a problem with my internet connection.  I have both wifi and ethernet automatically detected, but after a while, it doesn't work.  I must either restart the connection, or simply wait random amounts of time (hours) for it to start working again.  I still get an IP address, just doesn't seem to do anything.  No ping, no nslookup, nothing.  But after awhile it magically starts working again.  

I've seen various threads with these same issues, but no one seems to have a good response to it.

---

### Post by wombat20 on 2006-06-25
That is very odd.  Could it be your router/modem?  Does it work with any other machine?  Does it work on any other distro/OS?

Sorry I can't be of more help.  :???:

---

### Post by strattonbrazil on 2006-06-25
Other machines in the house work all the time.  My laptop worked fine running Windows, Debian and SUSE.  I don't even know how to debug this problem because there aren't any physical errors.  I think it might be a kernel issue.

---

### Post by eswar on 2006-06-26
Even I have the same problem with my notebook.  But my problem is bit different, whenever I try sudo apt-get update or upgrade or even using synaptic for installing things, the network gets automatically disconnected for no reason.  Even SSH or SCPing is causing the network down.  So, each time, I had to refresh my network.  Or I have to use sudo ifdown ethX first and 
sudo ifup ethX again to get the network working properly.  So, i am not able to upgrade, ssh or even download files of few MBs.

 I never had this problem with Breezy.    I dont know how to fix this, and  i am new to linux.  Could anyone please help me out?!
Cheers,
|Eswar>

---

### Post by harpo_the_whale on 2006-06-27
Still running Ubuntu 5.10 but having the same problem myself...networked with my main Win XP machine. No firewall probs, and other machines on network work fine (not Ubuntu). Connection will be great then all of a sudden nothing. Can not ping websites. Total loss of connectivity on Ubuntu. Usually a refresh/reboot seems to work but this gets annoying after awhile.

Thanks,
Harpo

---

### Post by ahwei on 2006-07-12
I was using Breezer and the same problem too. I did not bother it as I seldom use it as my primary machine. I normally will reboot the system and it works again. 

Now am using new 6.06. Problem persists. And I found out that no need to reboot system can cure it, just simply unplug the RJ45 cable to your machine and reconnect it back. The connection will be resumed without the reboot of the system. 

It is still annoying... anyone knows what is wrong?

---

### Post by mips on 2006-07-12
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

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

### Post by harpo_the_whale on 2006-07-19
Thanks for the offer MIPS it's much appreciated. Below is the requested information. I'm running an IBM 300PL thru the integrated NIC thru a Windows Gateway. I'm hoping maybe this will tell you a little more. Any suggestions are greatly appreciated. See below. I have also turne power save features off for the NIC on the gateway machine (firewalled), other machines work fine on the network even a test Linspire machine. Gateway uses static ip: 192.168.0.1 and also Ubuntu: 192.168.0.2 and all others are dynamic (can't remember Linspire but I think it was static). I have found a way to prevent the connection from dropping in and out...open up a terminal and have a nonstop ping running to 192.168.0.1 (gateway machine). When the connection drops it's only lost between Ubuntu and gateway machine while other machines are reachable on the network. Vice versa holds true. Nothing out of ordinary in the firewall logs so I'm really not sure.

Harpo




-----------------------------------------------------------------------------
harpo@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:06:29:26:3E:2C
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:158 txqueuelen:1000
          RX bytes:3719267 (3.5 MiB)  TX bytes:572168 (558.7 KiB)

harpo@ubuntu:~$ lspci | grep Eth
0000:00:03.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 05)
harpo@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
harpo@ubuntu:~$ cat /etc/resolv.conf
search mshome.net
nameserver 192.168.0.1
domain mshome.net
nameserver 67.69.184.216
harpo@ubuntu:~$ cat /etc/network/interfaces
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
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1



auto eth0
harpo@ubuntu:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
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
harpo@ubuntu:~$ ipconfig /all
bash: ipconfig: command not found
harpo@ubuntu:~$ ifconfig /all
/all: error fetching interface information: Device not found
harpo@ubuntu:~$ ifconfig /?
/?: error fetching interface information: Device not found
harpo@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:29:26:3E:2C
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:158 txqueuelen:1000
          RX bytes:3740591 (3.5 MiB)  TX bytes:612688 (598.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:205376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17866880 (17.0 MiB)  TX bytes:17866880 (17.0 MiB)

harpo@ubuntu:~$ ifconfig /all
/all: error fetching interface information: Device not found
harpo@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:29:26:3E:2C
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:158 txqueuelen:1000
          RX bytes:3743477 (3.5 MiB)  TX bytes:615623 (601.1 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:205576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17881750 (17.0 MiB)  TX bytes:17881750 (17.0 MiB)

harpo@ubuntu:~$

---

### Post by harpo_the_whale on 2006-07-19
P.S. IPv6 has been disabled. Done alot of looking around already and thought I should try that.

Harpo

---

### Post by mips on 2006-07-19
Everything looks ok. What happens if you connect the ubuntu box directly to the router ?

I will think a bit more about this and get back to you.

Btw. My windows machine has this problem but not Ubuntu.

---

### Post by harpo_the_whale on 2006-07-20
My Windows machine 192.168.0.1 is functioning more as a server than anything...you know storage & net connection. From Canada myself and I live right next door to the middle of nowhere (lol) so I'm only lucky enough to have dialup on that machine. The connection is not bad as far as dialup goes (42.6,44,45.3,46 bops... 28.8 to 33.6 on a real bad day). I should probably upgrade to the latest version 6 but I'm not in a real rush to download it as you may have guessed. I've requested Ubuntu send me another CD. It's slightly annoying but as long as I keep that terminal open with ping going I'm fine...with absolutely no problems at all. Same problem whether the internet is connected or disconnected so it has to be a general networking problem of some sorts. At work today (Win2k & 28.8 bops all the time) so I'll have to try it tonight when I get home. I'm sure there has to be a solution. Thanks for the help tho MIPS.

You have a Windows box with intermitant internet connection problem? How is your network setup? Multi machines thru a router? 

Harpo

---

### Post by mips on 2006-07-24
To be really honest with you I dunno what the problem is. My only advice is to persavere.

---

### Post by eswar on 2006-07-25
Hi Mips,
   Here is the list of things you asked for!  I marked the IPs and gateways with X's.  I use a static IP from my office.  Even I have tried IPv6 disabling tactics, but it did not work out and it works in the same way, as it is!  So I restored and enabled IPV6.

The internet connection has no problems, as no one has this problem in my office, moreover, other ubuntu workstations, which has Breezy Badger 5.10 works quite well, (even my linux box had no problems with network, until I upgraded to 6.06LTS).

Hope these infos give you some ideas!
Thanks in advance!
------------------------------------------------

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:84:13: D5
          inet addr: xxx.xxx.xxx.xxx(Static IP)  Bcast: ***.***.***.***  Mask: xxx.xxx.xxx.xxx
          inet6 addr: fe80::20f:b0ff:fe84:13d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:742012 (724.6 KiB)  TX bytes:70548 (68.8 KiB)
          Interrupt:169

------------------
 lspci |grep Eth
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Ethernet Controller (rev 10)
-------------------
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.0   0.0.0.0         xxx.xxx.xxx.xxx U     0      0        0 eth0
0.0.0.0         xxx.xxx.xxx.xxx  0.0.0.0         UG    0      0        0 eth0
------------------------
/etc/resolv.conf
search hrz.uni-dortmund.de
nameserver 129.217.129.42

-------------------------
/etc/network/interfaces


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# The primary network interface

iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx

iface dsl-provider inet ppp
provider dsl-provider

auto eth0
-----------------------------
/etc/dhcp3/dhclient.conf

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
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
-----------------------------------
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:84:13: D5
          inet addr: xxx.xxx.xxx.xxx  Bcast: xxx.xxx.xxx.xxx  Mask: xxx.xxx.xxx.xxx
          inet6 addr: fe80::20f:b0ff:fe84:13d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:95727 (93.4 KiB)  TX bytes:37332 (36.4 KiB)
          Interrupt:169

eth1      Link encap:Ethernet  HWaddr 00:12:F0:63:CB:42
          inet6 addr: fe80::212:f0ff:fe63:cb42/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:998 (998.0 b)  TX bytes:510 (510.0 b)
          Interrupt:58 Base address:0xe000 Memory:b4006000-b4006fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:250908 (245.0 KiB)  TX bytes:250908 (245.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
---------------------------------------------------------

---

### Post by mips on 2006-07-25
Are the addresses you xxx out public addresses or private ones. I can understand if they are public but if they are private it's kinda pointless and almost just as good as not posting the info.

I'll have a look and see if I can pick up anything.

---

### Post by mips on 2006-07-25
For now do a search here for **88E8036** and see if any of the issues apply to your pc.****

---

### Post by harpo_the_whale on 2006-07-26
Well I thank you for all of your efforts anyhow MIPS...it truely is appreciated. I'm sure I'll figure out the answer sooner or later but untill then at least it's very workable. Just received the new Ubuntu cd's in the mail last night so I think I'm going to have a crack at that and see if it doesn't solve this problem. Till next time.

Harpo

---

### Post by mips on 2006-07-27
Let us know how it goes, good luck.

---

### Post by asfaltboy on 2006-07-27
Thanks mips, you solved my problem of disconnections by disabling IPV6 :)
I wonder if there is some kind of way to detect if a moder/router uses it...

---

### Post by mips on 2006-07-27
> **asfaltboy said:**
> Thanks mips, you solved my problem of disconnections by disabling IPV6 :)
I wonder if there is some kind of way to detect if a moder/router uses it...

No probs. A lot if not the majority of home devices do not support ipv6.

---

### Post by eswar on 2006-07-28
> **mips said:**
> Are the addresses you xxx out public addresses or private ones. I can understand if they are public but if they are private it's kinda pointless and almost just as good as not posting the info.

I'll have a look and see if I can pick up anything.

It is the public one!  Even I thought it would not be of great help!  But with the same settings, it was working fine for me, until, I installed the Dapper Drake 6.06LTS!  

But, I should thank you anyway!  

Please let me know if you got some ideas!

---

### Post by mips on 2006-07-28
> **eswar said:**
> It is the public one!  Even I thought it would not be of great help!  But with the same settings, it was working fine for me, until, I installed the Dapper Drake 6.06LTS!  

But, I should thank you anyway!  

Please let me know if you got some ideas!

Did you do an upgrade or fresh install ?

---

### Post by eswar on 2006-08-01
I did upgrade, directly from Breezy 5.10 to Dapper 6.06LTS, by running update manager!  

Yesterday, I tried working with the live cd of Dapper Drake 6.06LTS!  Even with the live CD, I had problems.  I did download few files, after certain time, the network got hung, and I had to 
do 'ifdown' and 'ifup' to reconnect the net, just like what I do with my system, after installing 6.06LTS!! 

I tried running with DHCP as well as Static IP, in live CD session, but the results were the same!

When I was using Fedora Core 4, I had network problems..  but that was worser than the present case, finally, i came to know that that was kernel problems, as it was discussed by some people who have laptop of my model (Toshiba Satellite A80-154, with Marvell Yukon ethernet card)! Anyway, their tricks didnt work out with  my laptop.. so, i switched to ubuntu!!   

I do not get much details about ubuntu 6.06 and Marvell Yukon problems, so far!  :( 
 
I hope I will get some good info soon!!

---

### Post by mips on 2006-08-01
I will keep my eyes open.

---

### Post by eswar on 2006-08-07
> **mips said:**
> I will keep my eyes open.

Thanks Mips!   I just wanted to try with other linux distros.  So, I tried booting with gentoo linux (2006.1) live cd and with Xubuntu live CD too. But, I have the same problem.. The network works for sometime, all the sudden, it stops! 


Even I have installed 'rocks', which i found in the synaptic, in my dapper drake! but the problem persists!

 Is it anything to do with the newest kernel or something?  I do not know much about how to work out!  But, I want to play with this problem, without crashing my box!  Could you help me?!

Thanks in advance, 
|Eswar>

---

### Post by eswar on 2006-08-24
<sigh>hmmmm.. finally degraded to Breezy Badger 5.10!

---

### Post by MihaiM on 2006-12-24
I have this weird problem also. After using WiFi through Network Manager and Ethernet through DHCP on a router when I try setting the IPs manually the networks blocks by itself after some time, even if network activity is present.

I have uninstalled Network Manager and restarted the computer and didn't have the problem again, but just until now. Guess it's a problem with Network Manager which overrides the IP addresses.

---

