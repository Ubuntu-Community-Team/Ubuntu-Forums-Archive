---
title: "Internet - where are you?"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by Andrew Gibbons on 2006-01-13
Hi,

Having installed Ubuntu 5.10 (with dual boot into XP), I am unable to access the internet via a router. Local access to other pcs is fine. 'Pinging' the gateway address gives no response. This is also true of windows machines on the network which can access the net. Am confused!

Thanks for any help, Andrew

---

### Post by kosmic on 2006-01-13
What is the router IP ?
IS the router using DHCP ? or Static IP ?
in a terminal do the following :
 
sudo ifconfig
 
and post where the result

---

### Post by mips on 2006-01-13
What router do you have ?

Follow this guide and tell us where you get stuck:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)
Post the output of the steps here as you go along.

From windows copy and paste the output of the **ipconfig /all** command here.

---

### Post by Andrew Gibbons on 2006-01-18
Using DHCP
ifconfig gives :

eth0      Link encap:Ethernet  HWaddr 00:11:43:03:20:99
          inet addr:10.97.148.67  Bcast:10.97.148.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe03:2099/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1775 (1.7 KiB)  TX bytes:1878 (1.8 KiB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1724013 (1.6 MiB)  TX bytes:1724013 (1.6 MiB)

---

### Post by Andrew Gibbons on 2006-01-18
I'll try the 'follow' in a 'mo but first....

From windows
ipconfig /all gives :

Windows IP Configuration

        Host Name . . . . . . . . . . . . : a6
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : hants.gov.uk

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : hants.gov.uk
        Description . . . . . . . . . . . : Broadcom NetXtreme 57xx Gigabit Cont
roller
        Physical Address. . . . . . . . . : 00-11-43-03-20-99
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.97.148.67
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.97.148.40
        DHCP Server . . . . . . . . . . . : 172.26.1.30
        DNS Servers . . . . . . . . . . . : 172.16.1.41
                                            172.16.1.43
        Primary WINS Server . . . . . . . : 172.29.1.100
        Lease Obtained. . . . . . . . . . : 18 January 2006 11:39:07
        Lease Expires . . . . . . . . . . : 26 January 2006 11:39:07

---

### Post by mips on 2006-01-18
What brand/model router do you have ?
Who is the ISP ?

---

### Post by Andrew Gibbons on 2006-01-25
I think the router brand is : 3COM
the model is : Switch 3300-R209 (I guess!)

there's also 3C16985B Super Stack 3 written on the box....

I think the ISP is Hantsnet


[QUOTE=mips]What brand/model router do you have ?
Who is the ISP ?[/QUOTE]

---

### Post by mips on 2006-01-25
Can you ping:
1.  10.97.148.67
2.  10.97.148.40
3.  172.16.1.41
4.  213.166.17.43  ([www.hants.gov.uk](www.hants.gov.uk))
5.  198.133.219.25 ([www.cisco.com](www.cisco.com))
6.  [www.hants.gov.uk](www.hants.gov.uk)
7.  [www.cisco.com](www.cisco.com)

What output does traceroute 198.133.219.25 give you ? (You might have to run this from windows then the command is **tracert 198.133.219.25**)

Does your win web browser make use of a proxy server at all ?

Are you trying to connect from work ? Reason I ask is that you are plugged into a switch.****

---

### Post by Andrew Gibbons on 2006-01-25
from windows (will have to try Ubuntu later...) :

ping 10.97.148.67 ok
ping 10.97.148.40 fails
ping 172.16.1.41 ok
ping 213.166.17.443 ok
ping 198.133.219.25 fails
[www.hants.gov.uk](www.hants.gov.uk) ok
[www.cisco.com](www.cisco.com) fails

from windows, tracert 198.133.219.25 gives :

Tracing route to [www.cisco.com](www.cisco.com) [198.133.219.25]
over a maximum of 30 hops:

  1     1 ms     1 ms     1 ms  10.97.148.40
  2    15 ms    15 ms    15 ms  10.97.0.149
  3    22 ms    32 ms    20 ms  10.96.0.5
  4    21 ms    22 ms    21 ms  10.18.0.5
  5    22 ms    23 ms    23 ms  10.15.0.34
  6   215 ms   130 ms   116 ms  172.16.2.2
  7   549 ms    28 ms    28 ms  firewall3.hants.gov.uk [172.16.1.219]
  8     *        *        *     Request timed out.

win proxy server server used for LAN
yes to the work

thanks for your help!

---

### Post by mips on 2006-01-25
Have you configured your Ubuntu machine to use the proxy server ?

---

### Post by stream303 on 2006-01-25
> 
win proxy server server used for LAN
yes to the work

If you are running a firewall on the windows box, is it stopping your Ubuntu packets?

---

### Post by FLeiXiuS on 2006-01-25
By any chance have you checked your routing tables?  Please give us the output of the following command.  Most of the time there is no default gateway set.  This will result in a destination host unreachable message by ICMP when you go to ping a WAN // Internet address.

$ sudo route

Also, be sure to check to see if your name server is setup correctly in /etc/resolv.conf.  For example if your having problems pinging google.com with an error of "Unknown Host"  maybe this is why.

Find out your DNS servers and correctly set them up.  

Example:
search mydomainanme
nameserver xx.xx.xx.xx
nameserver xx.xx.xx.xx

Substitute the X's with the IP addresses of the name servers.  Note: There may be more then one!

---

### Post by Andrew Gibbons on 2006-01-27
My Ubuntu is configured to use a proxy (I think!)

---

### Post by Andrew Gibbons on 2006-01-27
My bad wording I suspect. The machine is dual-boot; when booted into Windows it is connected via a LAN to a proxy server. Obviously the same is true for the Ubuntu boot - the difference being that despite aparently setting the proxy configuration and the dns settings the same as for windows the Ubuntu won't connect to the internet!

---

### Post by Andrew Gibbons on 2006-01-27
output from sudo route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.97.148.0     *               255.255.255.0   U     0      0        0 eth0
default         10.97.148.40    0.0.0.0         UG    0      0        0 eth0


The DNS is setup the same as for the Windows configuration.

---

### Post by mips on 2006-01-28
Is authentication required for the proxy server ? I know that some proxy servers are setup/linked to the ms domain username&password.

Speak to your network admin and ask him what is required to get to the net.

---

### Post by Andrew Gibbons on 2006-01-30
The Windows machines have never required any authentication to be set up so I assume the same would be true for Ubuntu. The admin is as puzzled as I am!

---

### Post by mips on 2006-01-30
post your **/etc/network/interfaces** file here
post your **/etc/resolv.conf** file here
post the the output of **route -n** command here

---

### Post by Andrew Gibbons on 2006-01-30
from /etc/network/interfaces :
-----
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
iface eth0 inet dhcp

auto eth0

-----


from /etc/ersolv.conf :
----
search hants.gov.uk
nameserver 172.16.1.41
nameserver 172.16.1.43

----

output from route -n :

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.97.148.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.97.148.40    0.0.0.0         UG    0      0        0 eth0



thanks again!

---

### Post by mips on 2006-01-30
What happens when you:
ping 172.16.1.219
ping 213.166.17.48

Have you tried to statically configure your tcp/ip settings, not that it should make any difference ?

Your config looks fine and connectivity is there, just not to the internet which leads me to believe the problem might not be with your PC.

You might want to ask your network admin why the firewall reponds to outdside ping requests, not advisable unless you have a specific reason.

---

### Post by mips on 2006-01-30
Is your windows machine/browser configured to use a cache or proxy server at all ([http://cache.hants.gov.uk/](http://cache.hants.gov.uk/)) ???

Also disable IPv6 and see what happens.

In the firefox address/URL space type "about:config" , scroll down to **network.dns.disableIPV6 = false** ,double click this line to change it to **true**.
In the above do NOT type in any quotes.

The above will most probably help for Firefox but not your other applications. Test with Synaptic, GAIM and other stuff using the net and if they dont work try the following:

Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**alias net-pf-10 off #ipv6**

---

### Post by Andrew Gibbons on 2006-02-01
ping 172.16.1.219    responds
ping 213.166.17.48  responds

Have tried to statically configure the tcp/ip settings, not that it made any difference ! :-)


I agree about the firewall ping requests!

---

### Post by mips on 2006-02-01
[QUOTE=Andrew Gibbons]The Windows machines have never required any authentication to be set up so I assume the same would be true for Ubuntu. The admin is as puzzled as I am![/QUOTE]


Lets just say you fire up a windows machine get an IP address and do NOT log on to any windows domains/servers. 
Will you still be able to connect to the net ???

Can you ping any of the other PCs on your LAN from Linux ???

---

### Post by Andrew Gibbons on 2006-02-01
[QUOTE=mips]Lets just say you fire up a windows machine get an IP address and do NOT log on to any windows domains/servers. 
[/QUOTE]

Um, how?

[QUOTE=mips]Can you ping any of the other PCs on your LAN from Linux ???[/QUOTE]

Yes, the other (windows) PCs can be pinged, browsed etc.

---

### Post by mips on 2006-02-01
[QUOTE=Andrew Gibbons]Um, how?
Yes, the other (windows) PCs can be pinged, browsed etc.[/QUOTE]

Well, do you have to log on to the domain/server or can you not click the little dropdown menu and select Desktop only logon

I know a lot of places use the Domain Username/password to automatically give you access to a proxy/firewall. So even though you think you are not authenticating on any proxy/firewall you are actually without your knowledge as the process is transparent.

I honestly believe your config is good but something else is the matter.

---

### Post by Andrew Gibbons on 2006-02-01
[QUOTE=mips]Is your windows machine/browser configured to use a cache or proxy server at all ([http://cache.hants.gov.uk/](http://cache.hants.gov.uk/)) ???
[/QUOTE]

The windows machines have the lan settings set to use a proxy address for the http etc protocols

[QUOTE=mips]Also disable IPv6 and see what happens.
[/QUOTE]

alas, one of the first things I tried for Firefox - to no avail

---

### Post by mips on 2006-02-01
[QUOTE=Andrew Gibbons]The windows machines have the lan settings set to use a proxy address for the http etc protocols



alas, one of the first things I tried for Firefox - to no avail[/QUOTE]

Please configure youre ubuntu pc LAN settings to use the same proxy server and see what happens.

---

### Post by Andrew Gibbons on 2006-02-01
[QUOTE=mips]Please configure youre ubuntu pc LAN settings to use the same proxy server and see what happens.[/QUOTE]

I think I already have but I'll check....

---

### Post by Andrew Gibbons on 2006-02-01
[QUOTE=mips]Please configure youre ubuntu pc LAN settings to use the same proxy server and see what happens
[/QUOTE]

Um, thats another thing I tried at the beginning - without effect


[QUOTE=mips]Well, do you have to log on to the domain/server or can you not click the little dropdown menu and select Desktop only logon
[/QUOTE]

I'm only familiar with the situation here where several 'standalone' windows pcs each have a network card and are configured to talk to each other or connect to the internet. Don't know the menu you mention!


[QUOTE=mips]I know a lot of places use the Domain Username/password to automatically give you access to a proxy/firewall. So even though you think you are not authenticating on any proxy/firewall you are actually without your knowledge as the process is transparent.
[/QUOTE]

I sort of know what you mean but we have had to setup these pcs several times (thats the beauty of windows!) and neither I nor sys admin can remember ever having to setup such access. The only time we have seen (on these pcs) similar dialogues is for pc-pc connection (or for setting up Ubuntu!).

[QUOTE=mips]
I honestly believe your config is good but something else is the matter.[/QUOTE]

Thats what I usually thinkk about me! :-)

---

