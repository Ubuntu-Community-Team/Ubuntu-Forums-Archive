---
title: "Strange problem with Ubuntu-Ubuntu LAN"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by Neopard on 2006-07-15
Ok, here is the "short" description of my problem: I have a PC running Ubuntu and a notebook running both Windows XP and Ubuntu, connected to LAN. When the notebook runs WinXP I have no problems, PCs ping each other and share internet connecion, but when the notebook runs Ubuntu nothing works, they don't ping and green lights on PC's NIC are turned off (while they're on when the notebook runs Windows). :confused: 

And now some useful (I hope so) technical info.
I experienced this issue first when I installed Ubuntu on the PC for the first time, then after I updated everything worked fine for a while, now after another update Ubuntu machines can't talk :(
I'm connected to Internet through a USB adsl Modem on PC (it took some time to work properly), and to the LAN through a ethernet card (eth0). Kernel version is 2.6.15-26-386.
On the notebook I've a ethernet card (eth0) connected to the LAN and a Wireless card (eth1, but I don't have wireless connection at home so it's useless so far). Kernel version is 2.6.15-26-386.
As I've said before, when the notebook runs Windows everything works as it should, green lights are on, both machines ping each other and share connection, but as i reboot the notebook with Ubuntu green lights turn off and my machines are isolated.
I tried to boot the notebook with Gentoo LiveCD 2006.0 but nothing happens. It looks like Ubuntu PC can connect only with WinXP machines :shock:
I get some hints only by the output from **sudo ifconfig** on the PC:
when the notebook runs Ubuntu I get:
```
eth0      Link encap:Ethernet  HWaddr 00:50:BA:AD:0C:93
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4915 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:400920 (391.5 KiB)  TX bytes:400920 (391.5 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:82.54.195.158  P-t-P:192.168.100.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:472239 (461.1 KiB)  TX bytes:175555 (171.4 KiB)

```
while when it runs Windows XP:
```
eth0      Link encap:Ethernet  HWaddr 00:50:BA:AD:0C:93
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fead:c93/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11452 (11.1 KiB)  TX bytes:468 (468.0 b)
          Interrupt:10 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:684684 (668.6 KiB)  TX bytes:684684 (668.6 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:82.54.195.158  P-t-P:192.168.100.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:660795 (645.3 KiB)  TX bytes:242882 (237.1 KiB)

```
The main difference I notice is that in the first case "RUNNING" does not appear in eth0, I think this should be quite important...
Any help will be appreciated!!

---

### Post by MrHorus on 2006-07-15
Since ifconfig is a Linux command, how did you get a Linux output when running Windows XP?

If you show the output of ipconfig /all from Windows XP and then the output from ifconfig it will be possible to see what is different.

The fact that you are not even getting link lights would indicate a hardware problem or that you are not using a crossover cable but if it works no problem in Windows XP then that evidently is not the case.

---

### Post by Neopard on 2006-07-15
The code I posted before was from the Ubuntu PC, the first when the connected notebook runs Ubuntu, the other when the connected notebook runs WinXP.
Here is the code from the notebook, whene it runs Ubuntu and connection doesn't work
```
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:D9:46:24
          inet addr:192.168.1.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fed9:4624/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:17928 (17.5 KiB)
          Interrupt:11 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12244 (11.9 KiB)  TX bytes:12244 (11.9 KiB)

```
and here is the output from ipconfig /all, from the notebook running windows XP (when everything works)
```
Configurazione IP di Windows



        Hostname . . . . . . . . . . . . . . : ValYs

        Suffisso DNS primario  . . . . . . .  :

        Tipo nodo . . . . . . . . . . . . . .  : Ibrido

        Routing IP abilitato . . . . . . . .  : Sì

        Proxy WINS abilitato . . . . . . . .  : No



Ethernet card local network connection (LAN):



        Suffisso DNS specifico per connessione:

        Description . . . . . . . . . . . . . : Realtek RTL8139/810x Family Fast

 Ethernet NIC

        Physical address. . . . . . . . . . . : 00-C0-9F-D9-46-24

        DHCP enabled. . . . . . . . . . . . : No

        IP address. . . . . . . . . . . . . : 192.168.1.2

        Subnet mask . . . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.1

        Server DNS . . . . . . . . . . . . .  : 62.211.69.150

                                            212.48.4.15



Ethernet card, wireless connection



        Support state . . . . . . . . . . . : Support disconnected

        Description . . . . . . . . . . . . . : Intel(R) PRO/Wireless 2200BG Net

work Connection

        Physical address. . . . . . . . . . . : 00-13-CE-7C-B5-EA
```
Maybe some word from this output is wrong since I've translated from Italian, but useful info should be easily readable

---

### Post by mips on 2006-07-15
Do a search for **8139** here as there are known issues with that chipset, also look at disabling IPv6.

---

