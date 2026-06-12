---
title: "Realtek rtl8029 doesn't work"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by KL-7 on 2009-10-07
Hi.
I have a problem, that prevent me from changing my WinXP on Ubuntu :confused:
The problem is that I can't connect to the Internet under Ubuntu.
My DHCP connection works perfect under Windows for many years, but I can't make it working under Ubuntu (7.*, 8.*, 9.04).
After booting from liveCD (of from installed Ubuntu) I have an eth0 connection via rtl8029 with my correct IP, but this connection seems not working anyway. 

Can you help me? What additional info  should I post?

As I know there are many problems with this ethernet card, but I haven't found any solutions.

---

### Post by hal10000 on 2009-10-07
Open a terminal window and post the output of the following commands:
```

lspci
lsmod | grep ne2k
ifconfig

```
You may also run the command [COLOR="Red"]lshw[/COLOR] (this is a lowercase L in the command name, not a one), but because it produces a very long output, you should search for your network card section and post only this relevant part.
We may then be able to go further.

---

### Post by KL-7 on 2009-10-07
```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
02:03.0 Communication controller: Intel Corporation 536EP Data Fax Modem

ubuntu@ubuntu:~$ lsmod | grep ne2k
ne2k_pci               16480  0 
8390                   16768  1 ne2k_pci

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr /*My mac-address*/
          inet addr: /*My IP*/  Bcast:10.21.255.255  Mask:255.255.0.0
          inet6 addr: [fe80::260:52ff:fe05:a4b4/64]("http://fe80::260:52ff:fe05:a4b4/64") Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10188 (10.1 KB)  TX bytes:5763 (5.7 KB)
          Interrupt:22 Base address:0xbc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1068 (1.0 KB)  TX bytes:1068 (1.0 KB)
```

part from lshw:
```
           *-network
                description: Ethernet interface
                product: RTL-8029(AS)
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 00
                serial: 00:60:52:05:a4:b4
                width: 32 bits
                clock: 33MHz
                capabilities: ethernet physical
                configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=10.21.4.180 latency=0 module=ne2k_pci multicast=yes

```

As I understand my card is working, but there are some problems with drivers (ne2k-pci) or smth like that... How can I work around this problem?

---

### Post by hal10000 on 2009-10-07
You have no problems with drivers, your card is working perfectly.
Though you don't get a connection.
I suppose you're in a network. How is that network configured, do you get an ip-address via dhcp or do you have a static ip-address?

Your problems are presumably caused by a nameserver-problem. If the network is configured via dhcp then this should usually not happen, because most dhcp-servers offer you the correct ip-address of your nameserver(s). If you use a static ip-address then you have to fill in the nameservers ip-address(es) manually.

To verify if you have a nameserver-problem you can try to [COLOR="Red"]ping[/COLOR] to an existing ip-address in your network, e.g.:
```
ping 10.24.X.X
```
where X.X means an address part in your network. You may also try an ip-aress in the internet, e.g.
```
ping 194.25.2.129
```
This is the ip-address of the german telekom dns-server (of course you may use any other existing ip-address you like).
If you **get an answe**r like this:
```

ping 194.25.2.129

PING 194.25.2.129 (194.25.2.129) 56(84) bytes of data.                         
64 bytes from 194.25.2.129: icmp_seq=1 ttl=57 time=22.1 ms                     
64 bytes from 194.25.2.129: icmp_seq=2 ttl=57 time=22.6 ms                     
64 bytes from 194.25.2.129: icmp_seq=3 ttl=57 time=21.4 ms                     
64 bytes from 194.25.2.129: icmp_seq=4 ttl=57 time=21.6 ms
64 bytes from 194.25.2.129: icmp_seq=5 ttl=57 time=22.8 ms
64 bytes from 194.25.2.129: icmp_seq=6 ttl=57 time=22.1 ms
64 bytes from 194.25.2.129: icmp_seq=7 ttl=57 time=21.7 ms

```
but you **don't** get a positive answer if you ping this way:
```

ping dns03.btx.dtag.de

```
then you have definitely a nameserver-problem. You can fix this by either asking your network-administrator to tell you the ip-address of your nameserver or y booting windows and looking into the tcp-settings of your ethernet card and notice the address of your nameservers; you then have to fill in the same settings in your ubuntu-network admin tool.

Some networks are configured to use a proxy-server for internet connection via your browser. You may ask your administrator for the correct settings or look under windows how your browser is configured in reference of your proxy-settings

If you want to get access to your windows servers in your network (domain, file servers, printservers etc.) you have to use the samba client in ubuntu and also ask you administrator or look in your windows settings to get tese info.

I hope this can help you to silve your problems.

Good luck.

---

### Post by KL-7 on 2009-10-07
Thank you very much for answer.

The most awful circumstance in this situation is that I  connect not to the LAN, but directly to my internet provider which has a dhcp server. So my IP and any other connection properties in Ubuntu are absolutely right (They're identical to those one from WinXP, where I have stabel connection via this rtl8029). 

That's why I dont know what to do. 

I tried to connect modem via USB port - it works and I can access Internet. 
Anyway I prefer to get my rtl8029 working in Ubuntu, but if I dont find solution I'll use rtl8029 under WinXP and USB under linux.

---

### Post by hal10000 on 2009-10-07
That's very strange.
But since you get an ip-address from you provider via dhcp it is evident that your card has no problems, because otherwise you would'nt get an address!!!!

So it's just a configuration hassle.

What happens if you do a ping with a known ip-address and a ping with a known name? That's definitely the best test to find out what's going on.

Also post the output of the command [COLOR="Red"]route[/COLOR]

---

### Post by maxpathan on 2010-06-14
Hi
I have followed this thread. I have the same problem, but no solution.

My onboard LAN failed so I inserted an old lan card. I did the above commands and the same responses. 

The card is being recognised, but I cant even ping my router!!

Any advise will be much appreciated. Ive been trying to fix this for days :-(


regards
Max

---

