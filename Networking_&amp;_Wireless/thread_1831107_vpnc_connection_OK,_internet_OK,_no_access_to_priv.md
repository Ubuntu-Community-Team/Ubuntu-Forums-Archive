---
title: "vpnc: connection OK, internet OK, no access to private network"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by lantilope on 2011-08-22
Hi all,

Here is my issue.
I need Cisco VPN to access my university's (Griffith) server and it works just fine on Windows. When it is connected I have to go onto any web page, and it will aromatically show a Griffith page where I have to enter credentials. After that it works like a charm and I have a full access to the network.
I installed vpnc (network-manager-vpnc) in Ubuntu 11.04, managed to get the Griffith profile file from my Windows directory, and imported it into vpnc. I can connect to vpnc by entering my password, but when I go onto a web page I am not redirected to the usual Griffith login page (although I am connected to internet). For the story I am in China and my uni in Australia, but when I connect to vpnc it still looks like I am in China...

Any idea what could be wrong?

Thanks a lot for your help,

Ben

---

### Post by lmarmisa on 2011-08-22
Not sure if I can help you.

First of all, this link could help you:

[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

Please, post the output of this command while you are connected to the VPN:

```

ifconfig

```

P.S. Welcome to the forums. :-D

---

### Post by lantilope on 2011-08-22
Thanks for your quick reply and your welcome Imarmisa.
I already dug into the link you suggested but I didn't seem to find anything that could help me...
Here is the output of ifconfig:

```
ben@ben-OptiPlex-330:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:2c:40:9e  
          inet addr:10.10.101.14  Bcast:10.10.103.255  Mask:255.255.252.0
          inet6 addr: fe80::21e:c9ff:fe2c:409e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:397662 errors:0 dropped:39 overruns:0 frame:0
          TX packets:211738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:488152243 (488.1 MB)  TX bytes:17671798 (17.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40461 (40.4 KB)  TX bytes:40461 (40.4 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:132.234.200.54  P-t-P:132.234.200.54  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Anything interesting in there?

Ben

---

### Post by lkjoel on 2011-08-23
Could you run the Network Info script (in my signature), and attach the generated file?

---

### Post by lmarmisa on 2011-08-23
The interface **tun0** belongs to VPNC. A public IP address is assigned to this interface. This is an "australian" public IP address (Brisbane located). I do not know if this address was negotiated with the VPN server or if it is assigned by the Griffith profile you imported. Anyway, the same IP address seems assigned to the other side of the point to point connection. This is odd.

You will need more information about how to configure your VPNC for connecting to your university.  Maybe the profile of Windows that you imported is valid for Ubuntu but this is not sure.

If you need to be connected with Ubuntu to your University and you are unable to solve the VPN connection problem, you could consider to use virtualization.

If your computer is powerful (dual core, 2 GB of memory), you could install [VirtualBox]("http://www.virtualbox.org/") on Windows and then create an Ubuntu virtual machine. That virtual machine will be an Ubuntu system running like any other program of Windows. And this Ubuntu machine will be able to access to your University using the VPN connection of Windows.

---

### Post by lantilope on 2011-08-23
> Could you run the Network Info script (in my signature), and attach the generated file?

Sorry lkjoel for some reason I can't access your link...

> If your computer is powerful (dual core, 2 GB of memory), you could install VirtualBox on Windows and then create an Ubuntu virtual machine. That virtual machine will be an Ubuntu system running like any other program of Windows. And this Ubuntu machine will be able to access to your University using the VPN connection of Windows.

Actually the computer I'm using now runs on Ubuntu (the Windows partition was compromised and as it is a company computer I couldn't just format the drive), and I am using VirtualBox to virtualize a Win XP... The other way around!
And when I connect to vpnc, although I still have internet I can't access websites blocked in China. I'm definitely not bridging with Australia... Weird!

Thanks,

Ben

---

### Post by lmarmisa on 2011-08-23
Have you read this?:

[https://intranet.secure.griffith.edu.au/computing/remote-access/accessing-resources/virtual-private-network/vpn-installation-guide-for-linux-ubuntu](https://intranet.secure.griffith.edu.au/computing/remote-access/accessing-resources/virtual-private-network/vpn-installation-guide-for-linux-ubuntu)

---

### Post by lantilope on 2011-08-23
Damn I feel stupid - didn't even think of googling Griffith VPN...

However that still isn't working!  Now I don't have access to internet anymore, the browser says "looking for xxx" but nothing happens. The ifconfig output looks the same. Do you think it would work if I input directly the link of the page I'm supposed to be redirected to? Unfortunately I can't try it now I don't have my laptop with me...

---

### Post by lmarmisa on 2011-08-23
Sorry. I do not understand this comment: "Do you think it would work if I input directly the link of the page I'm supposed to be redirected to?".

Could you post the results of these commands while you are connected to the VPN?:

```

ifconfig
cat /etc/resolv.conf
route -n
ping -c3 8.8.4.4
ping -c3 google.com
wget www.ubuntu.com

```

---

### Post by lantilope on 2011-08-23
I meant that when on Windows I connect to the VPN, my browser automatically redirects me to a Griffith page where I have to put in my credentials. I tried to access the address of this page directly without success. 
However I installed Cisco VPN on my virtual Windows and I was pleased to see that it worked just fine! But still it would be nice to get it to work on my Ubuntu.
Here are the outputs of the commands:

```
ben@ben-OptiPlex-330:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:2c:40:9e  
          inet addr:10.10.101.77  Bcast:10.10.103.255  Mask:255.255.252.0
          inet6 addr: fe80::21e:c9ff:fe2c:409e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35383 errors:0 dropped:4 overruns:0 frame:0
          TX packets:16302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26587472 (26.5 MB)  TX bytes:1873234 (1.8 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43217 (43.2 KB)  TX bytes:43217 (43.2 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:132.234.200.47  P-t-P:132.234.200.47  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:12093 (12.0 KB)

ben@ben-OptiPlex-330:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain vpn.griffith.edu.au
search vpn.griffith.edu.au
nameserver 132.234.241.1
nameserver 132.234.241.10
nameserver 10.10.10.10

ben@ben-OptiPlex-330:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
132.234.1.230   10.10.100.1     255.255.255.255 UGH   0      0        0 eth0
132.234.200.0   0.0.0.0         255.255.254.0   U     0      0        0 tun0
10.10.100.0     0.0.0.0         255.255.252.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0

ben@ben-OptiPlex-330:~$ ping -c3 8.8.4.4
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.

--- 8.8.4.4 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

ben@ben-OptiPlex-330:~$ ping -c3 google.com
ping: unknown host google.com

ben@ben-OptiPlex-330:~$ wget www.ubuntu.com
--2011-08-23 15:28:19--  http://www.ubuntu.com/
Resolving www.ubuntu.com...   
failed: Name or service not known.                  
wget: unable to resolve host address `www.ubuntu.com'
ben@ben-OptiPlex-330:~$ 
 
```

---

### Post by lmarmisa on 2011-08-23
No traffic. :(
 
I have a question. In the case of Windows, you type a web site in your browser and then you are redirected to a login page where you enter your credentials. Have you provide these credentials while you have followed the VPN install guide?. I see a group name, a group password and a user name, but no personal password.

I suppose that you followed step by step the installation instructions and you did not type any wrong parameter.

---

### Post by lkjoel on 2011-08-23
8.8.4.4 is not a good IP to ping. I got 33% packet loss, and I'm connected.
Try this instead:
```
ping -c3 ubuntu.com

```

---

### Post by lmarmisa on 2011-08-23
> **lkjoel said:**
> 8.8.4.4 is not a good IP to ping. I got 33% packet loss, and I'm connected.
Try this instead:
```
ping -c3 ubuntu.com

```

**8.8.4.4** is a public DNS server provided by Google. This is normally a very reliable server. No problem here:

```

....
64 bytes from 8.8.4.4: icmp_req=94 ttl=51 time=119 ms
64 bytes from 8.8.4.4: icmp_req=95 ttl=51 time=110 ms
64 bytes from 8.8.4.4: icmp_req=96 ttl=51 time=104 ms
64 bytes from 8.8.4.4: icmp_req=97 ttl=51 time=98.5 ms
64 bytes from 8.8.4.4: icmp_req=98 ttl=51 time=127 ms
64 bytes from 8.8.4.4: icmp_req=99 ttl=51 time=112 ms
64 bytes from 8.8.4.4: icmp_req=100 ttl=51 time=109 ms
64 bytes from 8.8.4.4: icmp_req=101 ttl=51 time=126 ms
64 bytes from 8.8.4.4: icmp_req=102 ttl=51 time=153 ms
64 bytes from 8.8.4.4: icmp_req=103 ttl=51 time=140 ms
64 bytes from 8.8.4.4: icmp_req=104 ttl=51 time=128 ms
^C
--- 8.8.4.4 ping statistics ---
[COLOR="Blue"]104 packets transmitted, 104 received, 0% packet loss, time 103149ms[/COLOR]
rtt min/avg/max/mdev = 81.423/109.348/155.874/18.991 ms
luis@UB1010ENG:~$ 


```

---

### Post by lkjoel on 2011-08-23
Why don't you just try:
```
ping -c3 google.com

```
So that it will always choose the best server.

---

### Post by lmarmisa on 2011-08-23
> **lkjoel said:**
> Why don't you just try:
```
ping -c3 google.com

```
So that it will always choose the best server.

I prefer to propose two different tests:

1) **ping -c3 8.8.4.4 **is oriented to check the IP communications. We are looking for the echo to ping of a server located in some point in the internet. This test does not require the DSN service.

2) **ping -c3 google.com** is oriented to check the DNS resolution.

Sometimes the problem is related to DNS. In that case the first command will work and the second one will fail.

---

### Post by lantilope on 2011-08-23
> Have you provide these credentials while you have followed the VPN install guide?. I see a group name, a group password and a user name, but no personal password.

Yes there is indeed a username, and the personal password is asked when connecting to vpnc. All the parameters should be good, I double checked with the Windows ones and it is all the same. It just would not go through to the Griffith login page.

> Why don't you just try:
```
ping -c3 google.com
```

I tried that without success... There is no traffic.

What do you think the issue might be? Do you think it is on the Australian side that something goes wrong?

Ben

---

### Post by lmarmisa on 2011-08-23
Maybe the remote access from Ubuntu to the Griffith university does not work properly, but this sounds a bit strange. According to your comments, the VPN connection protocol seems completed but you have no traffic.

I recommend this test. Create a new virtual machine and install Ubuntu on it (select the bridged mode for your network interface if you have a DHCP server on your LAN). Then start your VM and go to the [link VPN Installation Guide for Linux Ubuntu]("https://intranet.secure.griffith.edu.au/computing/remote-access/accessing-resources/virtual-private-network/vpn-installation-guide-for-linux-ubuntu") and follow the instructions again. Finally check if you are able to connect to the Griffith university from the new virtual machine.

---

### Post by lantilope on 2011-08-24
OK I installed a virtual Ubuntu and tried it again, I still could not access any web page. I tried with a bridged network and NAT but both lead to the same result. I guess I will have to work from my virtual XP when I will need the VPN!

---

### Post by lmarmisa on 2011-08-24
> **lantilope said:**
> OK I installed a virtual Ubuntu and tried it again, I still could not access any web page. I tried with a bridged network and NAT but both lead to the same result. I guess I will have to work from my virtual XP when I will need the VPN!

Contact the university and ask them if there is a problem with the VPN access from Ubuntu.

---

