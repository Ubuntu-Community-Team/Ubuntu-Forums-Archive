---
title: "No internet"
date: 2006-02-06
forum: Networking &amp; Wireless
---

### Post by olddave on 2006-02-06
I have posted in the other forums [http://www.ubuntuforums.org/showthread.php?t=125403](http://www.ubuntuforums.org/showthread.php?t=125403)
with my problems as i said in there all was working well last week but not now i have even reinstalled ubuntu twice and still no inernet will not ping or do anything can anyone help.
olddave

---

### Post by encompass on 2006-02-06
I have not looked at your previous thread... nor do I have the time....
BUT... have your tried rebooting your router and making sure those settings are correct?  That fixed my problem.

---

### Post by olddave on 2006-02-06
Yes i rebooted the modem when i got home tonight then tried to get on the internet still nothing.
olddave

---

### Post by mips on 2006-02-06
olddave,

The following info please:

1. Logical network layout, PC-->Router-->Modem etc
2. Connection type, USB, Ethernet etc.
2. Brand & Model of every single network device in #1 above (not PC)
3. Output of Windows ipconfig /all
4. Output of Ubuntu ifconfig -a
5. Output of Ubuntu route -n 
6. Contents of /etc/network/interfaces file
7. Content of /etc/resolv.conf file
8. ISP and weblink to their site.

---

### Post by olddave on 2006-02-07
1.  Network Card - 
     Router / Modem - Belkin voip 802.11g F1PI241EGau

2. Connection type is Ethernet, direct to Router/Modem, Modem direct to ADSL

3. ipconfig - 
Windows IP Configuration

4.  ifconfig -a output

eth0  link encap:ethernet HWaddr <<MAC ADDRESS>>
        inet6 addr: fe80::206:5bff:fe7c:5ffl/64 Scope:Link
        UP BRAODCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 b) TX bytes:7626 (7.4 KiB)
        Interrupt:18 Base address:0xdc80

lo      link encap:local loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:4498 errors:0 dropped:0 overruns:0 frame:0
        TX packets:4498 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:405331 (395.8 KiB) TX bytes:405331 (395.8 KiB)

sit0   link encap:IPv6-in-IPv4
        NOARP MTU:1480 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

5. Route -n returns an empty table listing.

6. contents of /etc/network/interfaces:
   auto lo
   iface lo inet loopback
   mapping hotplug
   script grep
   map eth0
  
   iface dsl-provider inet ppp
   provider dsl-provider

   iface eth0 inet dhcp

   auto eth0

7.  /etc/resolv.conf  is blank

8. We use iinet which have a news server of freenews.iinet.net.au - I am not sure what you mean by a "weblink" but their website is iinet.net.au.

---

### Post by olddave on 2006-02-07
3. Windows IP  config

Ethernet adapter local area connection:
connection-specific DNS Suffix .:
IP Addresss...........................: 10.1.1.2
Subnet Mask..........................: 255.255.255.0
Default Gateway.....................: 10.1.1.1


Also the PC ethernet card is:  Network adapters: 3Com 3C920 Integrated Fast Ethernet Conroller (3C905C-TX Compatible)

Windows is fine for connection to the internet - with all default settings (including the DNS server).

---

### Post by mips on 2006-02-07
First lets see if we can get any connectivity via a static address seeing dhcp is not working.

**sudo gedit /etc/network/interfaces**

remove the line that says:
```
iface eth0 inet dhcp
```

and add this instead:
```
iface eth0 inet static
	address 10.1.1.2
	netmask 255.255.255.0
	network 10.1.1.0
	broadcast 10.1.1.255
	gateway 10.1.1.1
```



Lets also update your DNS details
[B]
sudo gedit /etc/resolv.conf[/B]

add these lines:
```
nameserver 203.59.24.3
nameserver 203.14.169.3
```
I assume the above DNS IP's are the same as reported by the windows ipconfig /all command ???


Can you ping 10.1.1.1 ?
Can you ping 203.59.24.3 ?
What does **route -n** display now ?

---

