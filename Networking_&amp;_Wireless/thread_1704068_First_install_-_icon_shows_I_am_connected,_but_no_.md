---
title: "First install - icon shows I am connected, but no Internet access on laptop"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by gurudev1000 on 2011-03-10
Hi,
I believe many might have had this problem but countless searching on Google and this forum has yielded no results.

My friend has been having a lot of problems with Windows. I offered to install Ubuntu for him since it might juice out better performance from him hardware and less headaches of defragment and malwares.

I installed Ubuntu through the pendrive since his DVD drive isn't reading anything. After that, I open 'edit network' something from the network icon and since the 'auto eth0' connection doesn't work for my cable internet (which needs username and password when using Windows and connects me via a LAN cable to some device the operator has kept in the locality) I added a new connection under the 'dsl' tab and put in my username, password and service name.

This method worked when I tried Ubuntu on my desktop. But it's NOT working on the laptop. The icon shows it's connected but NOTHING loads. The updates don't work either. I read something about MTU but I am clueless what I am supposed to do with it. I have tried live boots of 9.10 and 11.04 alpha3 and all give the same problem. I have a golden chance of getting someone to Ubuntu but this is screwed up.

Please help me.

---

### Post by prshah on 2011-03-10
> **gurudev1000 said:**
> cable internet (which needs username and password when using Windows and connects me via a LAN cable to some device the operator has kept in the locality) I added a new connection under the 'dsl' tab and put in my username, password and service name.

If you are using Cable Internet, it is unlikely that the DSL settings will work. Depending on your provider, Auto eth0 should give you a network connection, and any attempt to browse should open the logon page (of your ISP).

I don't think your problem has anything to do with MTU yet; you should first check the following: Open a terminal, and give the commands as follows; please post back output for trouble shooting.

Are you physically connected to the network?```
sudo mii-tool eth0
``` 
Can you obtain an IP address and DNS information?```
sudo dhclient eth0
```
Are you connected to the Internet?```
ping -c 3 209.85.231.104
 # IP address is Google's
```
Is address translation working?```
ping -c 3 www.google.com
```
Are your DNS servers correct```
cat /etc/resolv.conf
```

Please post back output for more troubleshooting. Once again, I don't think entering username/password in the DSL tab will be of any help (that's for when the ADSL router is setup in the bridged mode only).

---

### Post by gurudev1000 on 2011-03-10
> **prshah said:**
> If you are using Cable Internet, it is unlikely that t.....k output for more troubleshooting. Once again, I don't think entering username/password in the DSL tab will be of any help (that's for when the ADSL router is setup in the bridged mode only).

THE OUTPUT:

lawrence@LawHCL:~$ sudo mii-tool eth0
[sudo] password for lawrence: 
eth0: negotiated 100baseTx-FD flow-control, link ok
lawrence@LawHCL:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:14:0b:44:47:6c
Sending on   LPF/eth0/00:14:0b:44:47:6c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
lawrence@LawHCL:~$ ping -c 3 209.85.231.104
PING 209.85.231.104 (209.85.231.104) 56(84) bytes of data.
From 169.254.5.47 icmp_seq=1 Destination Host Unreachable
From 169.254.5.47 icmp_seq=2 Destination Host Unreachable
From 169.254.5.47 icmp_seq=3 Destination Host Unreachable

--- 209.85.231.104 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms
pipe 3
lawrence@LawHCL:~$ cat /etc/resolv.conf
lawrence@LawHCL:~$ sudo cat /etc/resolv.conf

----------------

All these commands were typed while my network icon showed 'no network connection' since I followed your advice and only allowed the deafult 'auto eth0' under 'wired' tab.

---

### Post by prshah on 2011-03-10
> **gurudev1000 said:**
> 
lawrence@LawHCL:~$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD flow-control, link ok
lawrence@LawHCL:~$ sudo dhclient eth0
<..>
No working leases in persistent database - sleeping.

All these commands were typed while my network icon showed 'no network connection' since I followed your advice and only allowed the deafult 'auto eth0' under 'wired' tab.

The first command indicates that as far as a physical connection goes, everything is fine. The second command's failure shows that it is not able to obtain an IP address automatically, possibly indicating that you need to set the IP address and related details manually.

Has your cable Internet provider given you (/your friend) any specific IP address / subnet mask / DNS settings? What does the LAN cable plug into? Do you see a brand name / model number? Who is your ISP?

---

### Post by gurudev1000 on 2011-03-10
> **prshah said:**
> The first command indicates that as far as a physical connection goes, everything is fine. The second command's failure shows that it is not able to obtain an IP address automatically, possibly indicating that you need to set the IP address and related details manually.

Has your cable Internet provider given you (/your friend) any specific IP address / subnet mask / DNS settings? What does the LAN cable plug into? Do you see a brand name / model number? Who is your ISP?

Thanks for you replies :)
As I said before, the LAN cable doesn't end into any modem the cable has set in my house... it goes out of the house into what I IMAGINE might be a local thing they have set up. The cable guy gave me my username and password (both are the same) and the service name which is 'hnsbalaji'. On Windows this is all the information I need to have a working internet connection.

I use Windows 7. Is there any way I can get the required information from there and put into Ubuntu? I don't want to ask the cable guys themselves since they couldn't help at all last time with Linux.

---

### Post by prshah on 2011-03-11
> **gurudev1000 said:**
> On Windows this is all the information I need to have a working internet connection.

I use Windows 7. Is there any way I can get the required information from there and put into Ubuntu? 

How did you setup the connection on Windows 7? Exact steps, please, if possible.

Yes, you can pull the information off Windows 7. Note that the first step is to get the valid network information (IP address, subnet mask, DNS, etc). So boot into Windows, connect to your Internet, open a command prompt, and give the command```
ipconfig /all
``` Please post the output here. Please sanitize output by changing public IP addresses, if any.

---

### Post by gurudev1000 on 2011-03-11
> **prshah said:**
> How di...any.
Thanks again. I did the best I could to 'sanitise' the results though I have no idea what the method is :)

In Windows 7, I open 'internet options' and under 'connections' tab I 'add' a new connection. It usually doesn't set it up perfectly and give me the option to 'cancel' or 'set it up anyway'. I chose the latter. THEN in the network icon on the taskbar I open the connection newly made and add the username, password and service name... that's all

-------------------
Windows IP Configuration

   Host Name . . . . . . . . . . . . : Black-Beauty
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

PPP adapter InternetCable:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : InternetCable
   Physical Address. . . . . . . . . :
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : *NUMBERS HERE*(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.255
   Default Gateway . . . . . . . . . : 0.0.0.0
   DNS Servers . . . . . . . . . . . : 172.20.60.1
                                       123.108.224.6
   NetBIOS over Tcpip. . . . . . . . : Disabled

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 00-30-67-4E-CE-43
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : *NUMBERS AND ALPHABETS HERE*(Preferred)
   Autoconfiguration IPv4 Address. . : *NUMBERS HERE*(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : 234893415
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-15-04-9F-9B-00-30-67-4E-CE-43

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.{F8C2CB9F-06B5-4C12-9B55-9474A285A956}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{0C66CEDF-8148-4F44-9B8A-458898E134C1}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

---

