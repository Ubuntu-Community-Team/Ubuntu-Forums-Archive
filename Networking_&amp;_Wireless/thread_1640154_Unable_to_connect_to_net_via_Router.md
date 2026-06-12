---
title: "Unable to connect to net via Router"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by rajnikhil on 2010-12-07
Hi, I have an adsl broadband connection which I used to connect to internet via the router. The router is a Belkin F5D7230-4 Version-3000. When I originally installed ubuntu on my desktop the connection worked fine but then I configured the pppoe connection using the command 'sudo pppoeconf' to connect to the internet directly via the modem and after I did this I wasn't able to connect to the internet via the router anymore. I tried accessing the config page of the router at 192.168.2.1 in the ubuntu but that doesn't work too however the same works fine when I try to access it using my windows laptop and in that it shows the router to be working absolutely fine.

Could anyone please help me out here. Please let me know if you need anymore details (also please provide the steps/commands to get the info you need)

Thanks in advance!

---

### Post by dineshs on 2010-12-08
Pl try
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
After following step-I and II you can either use pon dsl-provider command to connect or try another method given in step-III
If you have problems please post the results of```
ifconfig -a
```and ```
ping 4.2.2.1 -c3
```after connecting

---

### Post by rajnikhil on 2010-12-08
Hi Dinesh, Thanks for the help however the connection still works only when the desktop is directly connected to the modem but when I connect the modem to the router and the desktop to the router then again the internet doesn't work. I tried connecting by creating a 'wired connection' from the NM but it doesn't show up when I click on the icon in the panel in order to use this connection. I did run the commands that you gave me after connecting the system to the router and here are the results:

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:94:83:5c  
          inet6 addr: fe80::21a:4dff:fe94:835c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:664250 (664.2 KB)  TX bytes:113775 (113.7 KB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1379135 (1.3 MB)  TX bytes:1379135 (1.3 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ping 4.2.2.1 -c3
connect: Network is unreachable

Please help me out. Thanks again.

---

### Post by dineshs on 2010-12-08
> I tried connecting by creating a 'wired connection' from the NM but it doesn't show up when I click on the icon in the panel in order to use this connection
1)Did you tick [COLOR="Blue"]Available to all users[/COLOR] while creating new connection?
> when I connect the modem to the router and the desktop to the router then again the internet doesn't work2)Does this setup work fine on windows?
3)Did you try pon dsl-provider or step-III in the given link to connect?
4)How do you connect to internet in Windows? Do you use a pppoe dialler or is the connection always ON?
5)What is the model name of your modem?

---

### Post by rajnikhil on 2010-12-08
> **dineshs said:**
> 1)Did you tick [COLOR="Blue"]Available to all 
users[/COLOR] while creating new connection?
I did not check available to all users when created the 'wired connection' however I did that when I created the DSL connection and that works fine.

2)Does this setup work fine on windows?
I am able to connect to internet with my windows laptop connected to the router by cable (not just wireless)
3)Did you try pon dsl-provider or step-III in the given link to connect?
Yeah I executed step III as you mentioned and I am able to connect only through modem (like I was able to when I was using pppoeconf).
4)How do you connect to internet in Windows? Do you use a pppoe dialler or is the connection always ON?
I have windows only on my laptop so i connect to it wirelessly through the router and during this time I cannot access the internet on my desktop.
5)What is the model name of your modem?
The modem is provided by BSNL, the model number is UT-300R2U

Also, when I'm creating wired network (not DSL) using NM it asks for MAC address. Now when I go to the router's setup using my windows laptop I can three mac addresses there i.e. wlan, lan and wan. Which of these am I supposed to provide in NM?

Again thanks for helping me out.

---

### Post by rajnikhil on 2010-12-08
Please find above my reply in-line.

---

### Post by dineshs on 2010-12-08
> Now when I go to the router's setup using my windows laptop I can three mac addresses there i.e. wlan, lan and wan. Which of these am I supposed to provide in NM?It is the MAC of your ethernet card
[COLOR="Blue"]00:1a:4d:94:83:5c[/COLOR] (see the result of ifconfig command)
I am not an expert in setting up a router.But I think the following setup will work and you can use both machines at a time
Step-I Make your modem(UT300) Bridged 
> Open browser  Firefox-Type 192.168.1.1 in Address bar. Click GO-Enter both Username and Password as[COLOR="Blue"] admin[/COLOR]-Click OK
Click advanced setup-Click edit at the right end of the line having 0/35 as VPI/VCI value-Click Next-select Bridging and click next, next.. save then save/reboot
wait till reboot complete (3 minutes)
Step-II Make your router PPPoE (See manual)
Step-III Connect modem ethernet to router WAN
Connect PCs to router and see if you are getting internet

---

### Post by rajnikhil on 2010-12-09
Hi Dinesh,

Just checked out the pages of modem and the router and all the values that you mentioned were already the ones that you mentioned.

I've attached the screenshots of both the pages. Please check them out and let me know if there is something I missed out.

Thanks

---

### Post by dineshs on 2010-12-09
The settings look OK.
Let us try rhis
Right-click on the NM icon(on top right of the panel) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection listed and click edit(If you dont see a wired connection,add one)
select ipv4 
method-manual 
address 192.168.2.250
mask 255.255.255.0 
gateway 192.168.2.1 [COLOR="Red"]then hit enter [/COLOR]
DNS 4.2.2.1 
click apply
run```
sudo service network-manager restart
```
And see if pages are loading

---

### Post by rajnikhil on 2010-12-09
Hurrrrrrrrrrrrrrrrraaaaaaaaaaaaaaaaaaayyyyyyyyyyyyyyyyyyyyyyyyyy. It works. I can now connect to the internet by both methods. Thanks a lot Dinesh, it was an I was looking to resolve for over an year now. You are a saviour, thanks a lot once again.:p:p:p:p:p:p:p:p

---

### Post by rajnikhil on 2010-12-09
Just one last doubt. I can't access any of the setup pages i.e. modem (192.168.1.1) and router (192.168.2.1) in ubuntu but only through my laptop which has windows. Any idea why it could be so?

---

### Post by dineshs on 2010-12-09
what are the results of ```
ping 192.168.1.1 -c3
```and```
ping 192.168.2.1 -c3
```?

---

### Post by rajnikhil on 2010-12-09
Hi Dinesh,

Following are the results of the queries you mentioned:
ping 192.168.1.1 -c3
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

ping 192.168.2.1 -c3
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.625 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.552 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=0.530 ms

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.530/0.569/0.625/0.040 ms

As you can see I'm now able to access the setup page of router however the setup page of the modem still remains out of reach in Ubuntu.

---

### Post by drdos2006 on 2010-12-09
I copied this from a previous posting for future use. It may be of some help to you......

You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

You be also having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns
Change IPv6disabled to true
Restart Firefox.

regards

---

