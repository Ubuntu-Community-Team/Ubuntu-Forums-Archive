---
title: "Configure VPN"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by diwas on 2009-05-04
Hello,


The network manager applet in the top panel shows an error. When I click it except "VPN Connections >" everything else is faded. Under *VPN Connections* I have two menus *Configure VPN* and *Disconnect VPN* and again, only *Configure VPN* is click able. And upon opening the Network Manager, nothing is click able in the right hand side. See screen shot.

Now, I have a single computer connected through NIC card to a ADSL router. Internet works great, but I don't know why am I getting this problem.

I am using Jaunty and the same problem persisted in Intrepid as well. I did a clean install of Jaunty, configured pppoe and then it was fine. But when I rebooted the system (without any change to the system) it showed me this error. Same thing happened with Intrepid.

The output of some common commands are as follows:
```

diwas@diwas-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)
01:02.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)

```

```

diwas@diwas-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:46:01:4e:e3  
          inet6 addr: fe80::218:46ff:fe01:4ee3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10324729 (10.3 MB)  TX bytes:816423 (816.4 KB)
          Interrupt:22 Memory:ff8ffc00-ff8ffcff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:120.89.101.148  P-t-P:120.89.97.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:7883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10147633 (10.1 MB)  TX bytes:643417 (643.4 KB)


```



Actually, this isn't a problem, but I think this might be the cause of a problem which has been annoying me since six months.


----
Diwas

---

### Post by diwas on 2009-05-04
I am sorry, I forgot to upload screen shot.

---

### Post by diwas on 2009-05-06
bump

---

### Post by diwas on 2009-05-09
bump

---

### Post by zozio32 on 2009-05-09
Sae stuff for me...
I just don't know how to get started with it.

---

### Post by Andrey Gazizov on 2009-05-09
I think. the Network Manager isn't good variant. Try to use Wicd (wicd.net) or, more better, configure your vpn with config-files. 

If you really want to use NM than you must install additional package "open vpn" for NW!

---

### Post by diwas on 2009-05-10
I dont get this though. I have a single computer, why would I even have to configure VPN? :S its strange or am I missing smthg?

---

### Post by zozio32 on 2009-05-11
I/ve installed open vpn, but the problem remain: I just don't have any option available in the VPN tab of the Network Connexion configuration tool.

And I have to say, I'll be totally clueless of what do to with the config files themselves

---

### Post by gombadi on 2009-05-11
> 
I/ve installed open vpn


When you say you have installed openvpn what packages did you install?

```

lroger@dave:~$ apt-cache search openvpn
openvpn - virtual private network daemon
openvpn-blacklist - list of blacklisted OpenVPN RSA shared keys
ebox-openvpn - eBox - OpenVPN server module
gadmin-openvpn-client - GTK+ configuration tool for openvpn (client)
gadmin-openvpn-server - GTK+ configuration tool for openvpn (server)
gadmin-tools - GTK+ server administration tools
kvpnc - vpn clients frontend for KDE
network-manager-openvpn - network management framework (OpenVPN plugin)
tunneldigger - Configures OpenVPN tunnel networks
tunneldigger-utils - Utilities for TunnelDigger-configured OpenVPN tunnels

```

---

### Post by zozio32 on 2009-06-11
sorry for not answering
I have been out for a while, not really checking this kind of stuff

when I' said that I have installed openvpn, it means that I ticked the openvpn box on the package manager, that's all.  I was hoping that the Networks Connection editor will all me to add one after that.

Anything else I should do?

---

### Post by dholbert on 2010-08-18
You also need to install this package:
```
network-manager-openvpn
```

(I imagine you probably already figured that out, but I'm just posting in case anyone else stumbles across this thread in search of help.)

---

