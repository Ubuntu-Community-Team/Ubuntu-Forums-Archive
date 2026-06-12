---
title: "No wired connection even though everything is looking fine."
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by Herbert K. on 2009-02-17
Hi,

i installed ubuntu 8.10 on my FujitsuSiemens Amilo A 7600 Laptop. I have no problems with this connection on Windows XP and xubuntu 6.10 worked out of box. 
But now i got a weird wired connection problem. Everything seems to be working but nothing goes through.

(provider)---(splitter)---(dsl modem)---(router)---(2 wired and 2 wireless clients)


```
user@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:02:3f:b9:89:11  
          inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0 
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1 
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2083 (2.0 KB)  TX bytes:3481 (3.4 KB) 
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:4540 (4.5 KB)  TX bytes:4540 (4.5 KB) 

user@ubuntu:~$ ping 192.168.0.1 
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 
From 192.168.0.109 icmp_seq=2 Destination Host Unreachable 
From 192.168.0.109 icmp_seq=3 Destination Host Unreachable 
From 192.168.0.109 icmp_seq=4 Destination Host Unreachable 
From 192.168.0.109 icmp_seq=6 Destination Host Unreachable 
From 192.168.0.109 icmp_seq=7 Destination Host Unreachable 
From 192.168.0.109 icmp_seq=8 Destination Host Unreachable 
From 192.168.0.109 icmp_seq=10 Destination Host Unreachable 
From 192.168.0.109 icmp_seq=11 Destination Host Unreachable 
From 192.168.0.109 icmp_seq=12 Destination Host Unreachable 
^C 
--- 192.168.0.1 ping statistics --- 
13 packets transmitted, 0 received, +9 errors, 100% packet loss, time 12011ms 
, pipe 3 
user@ubuntu:~$ sudo gedit /etc/network/interfaces 
[sudo] password for user: 
user@ubuntu:~$ 


auto lo eth0
iface lo inet loopback

iface eth0 inet dhcp



user@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
00:0b.0 CardBus bridge: ENE Technology Inc CB1420 Cardbus Controller (rev 01)
00:0b.1 CardBus bridge: ENE Technology Inc CB1420 Cardbus Controller (rev 01)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
user@ubuntu:~$ 
```

What i tried yet:

-  edit /etc/network/interfaces  auto eth0 iface eth0 inet dhcp

didnt solve the problem

-  change the mtu rate to different settings 1492, 1454, 1460, 1452, 1500

this didnt help either and had no effect on the ifconfig mtu output, on the contrary the system completly froze up a few times when i tried to sudo /etc/init.d/networking restart


Any ideas?

---

### Post by whiskytroll on 2009-02-17
Hi Herbert!

Do you have NetworkManager installed? If you do it will try to manage your connections automagicaly, and usually it succeeds. However if there is lines in the "/etc/network/interfaces" other than the ones containing something whith "lo" the NetworkManager wont try anything since it allows you to do so manually instead. So you might try to change the "/etc/network/interfaces" to contain only:

auto lo eth0
iface lo inet loopback

then restart the network.

Hope this will help you, cause I don't know anything about manually configs... :)

---

### Post by Miguel on 2009-02-17
I might be having a similar problem. I did a BIOS update in Win XP about two hours ago, and now my ethernet card no longer works. It doesn't work in Ubuntu 8.10 and it doesn't work in openSUSE 11.1. Both are for x86_64. Ethernet, however, works perfectly fine in WinXP.

However, where I'm based right now, DHCP uses a non-default IP address, so it's not the typical 192.168.*.*. However, Network Manager insists in using 192.168.whatever. I've tried modprobing in and out e1000e (the module for my network card) and to no avail. Luckily, WiFi seems to be working fine, but I don't know for much longer. Anybody has an idea of what might be going wrong?

---

### Post by Herbert K. on 2009-02-17
Hi,

the network connection didn´t work after the installation. So i googled for solutions and tried some out.

- i changed /etc/network/interfaces back to:

```
auto lo
iface lo inet looback
```

i needed to restart the system 3 times, because it stuck two times while booting

```
user@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:02:3f:b9:89:11  
          inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0 
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1 
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1963 (1.9 KB)  TX bytes:3413 (3.4 KB) 
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:91 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5100 (5.1 KB)  TX bytes:5100 (5.1 KB) 

user@ubuntu:~$ ping -c 4 192.168.0.1 
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 
From 192.168.0.109 icmp_seq=2 Destination Host Unreachable 
From 192.168.0.109 icmp_seq=3 Destination Host Unreachable 
From 192.168.0.109 icmp_seq=4 Destination Host Unreachable 
 
--- 192.168.0.1 ping statistics --- 
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms 
, pipe 3 
user@ubuntu:~$ 
```

as u can see no improvement

---

### Post by Herbert K. on 2009-02-18
Hi,

this Ibex anoys the crap out of me. I´m wasting way to much spare time on this. I made a little bit of progress but no break through yet.

- I looked up lsmod and noticed two drivers 8139too and 8139cp where loaded. I tried to blacklist 8193cp and rmmod 8139cp but the system still loaded it after reboot. So i removed 8139cp from kernel [http://ubuntuforums.org/showthread.php?t=169633](http://ubuntuforums.org/showthread.php?t=169633) . But this didn´t solve the problem.

- I disabled NetworkManager by unticking it in System/Preferences/Sessions and only configured ifupdown /etc/network/interfaces. This didn´t help either

- I tried out a knoppix 5.2 live dvd and everything worked fine: 
```
knoppix@Knoppix:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0b.0 CardBus bridge: ENE Technology Inc CB1420 Cardbus Controller (rev 01)
00:0b.1 CardBus bridge: ENE Technology Inc CB1420 Cardbus Controller (rev 01)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

knoppix@Knoppix:~$ lsmod
Module                  Size  Used by
ipv6                  279616  10
sworks_agp             13472  0
nvidia_agp             12316  0
efficeon_agp           12192  0
amd64_agp              16772  0
ali_agp                11136  0
af_packet              29960  0
dm_mod                 60440  0
trident                41044  0
gameport               19848  1 trident
ac97_codec             21132  1 trident
snd_ali5451            26892  1
snd_ac97_codec         97188  1 snd_ali5451
snd_ac97_bus            6528  1 snd_ac97_codec
snd_pcm_oss            45728  0
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                80004  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
parport_pc             43492  0
snd_timer              26500  1 snd_pcm
parport                40008  1 parport_pc
8250_pnp               13440  0
serio_raw              11012  0
snd                    55396  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              12512  2 trident,snd
8139too                31104  0
mii                     9728  1 8139too
shpchp                 41380  0
pci_hotplug            36424  1 shpchp
i2c_ali1535            11140  0
i2c_ali15x3            11908  0
i2c_core               25984  2 i2c_ali1535,i2c_ali15x3
8250_pci               24704  0
8250                   28164  2 8250_pnp,8250_pci
serial_core            25216  1 8250
snd_page_alloc         13960  1 snd_pcm
ati_agp                13068  1
agpgart                36044  6 sworks_agp,nvidia_agp,efficeon_agp,amd64_agp,ali_agp,ati_agp
tsdev                  11840  0
joydev                 13760  0
eth1394                23556  0
evdev                  14208  2
cpufreq_ondemand       12300  1
powernow_k7            11560  0
speedstep_lib           8836  0
freq_table              9088  2 cpufreq_ondemand,powernow_k7
processor              36200  1 powernow_k7
apm                    25564  2
aufs                   92504  1
cloop                  18496  2
sbp2                   28292  0
ohci1394               38960  0
ieee1394              300760  3 eth1394,sbp2,ohci1394
usb_storage            73408  0
usbhid                 56928  0
ff_memless              9992  1 usbhid
libusual               20624  1 usb_storage
ohci_hcd               24580  0
uhci_hcd               27788  0
ehci_hcd               35848  0
usbcore               135812  7 usb_storage,usbhid,libusual,ohci_hcd,uhci_hcd,ehci_hcd

knoppix@Knoppix:~$ lsmod | grep 8139
8139too                31104  0
mii                     9728  1 8139too

knoppix@Knoppix:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=255 time=2.70 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=255 time=0.539 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=255 time=0.546 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=255 time=0.538 ms

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 0.538/1.083/2.709/0.938 ms

knoppix@Knoppix:~$ ping heise.de
PING heise.de (193.99.144.80) 56(84) bytes of data.
64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=1 ttl=249 time=63.0 ms
64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=2 ttl=249 time=63.0 ms
64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=3 ttl=249 time=62.2 ms

--- heise.de ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 62.287/62.805/63.067/0.467 ms

knoppix@Knoppix:~$ ifconfig

eth1      Protokoll:Ethernet  Hardware Adresse 00:02:3F:B9:89:11
          inet Adresse:192.168.0.113  Bcast:192.168.0.255  Maske:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:4659 (4.5 KiB)  TX bytes:3182 (3.1 KiB)
          Interrupt:11 Basisadresse:0x4800

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

knoppix@Knoppix:~$     
```

- Then again i removed eth0 from /etc/network/interfaces and made a reboot.
```
user@ubuntu:~$ lsmod | grep 8139 
8139too                31616  0 
mii                    13440  1 8139too 
user@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:02:3f:b9:89:11  
          inet addr:192.168.0.113  Bcast:192.168.0.255  Mask:255.255.255.0 
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1 
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2449 (2.4 KB)  TX bytes:3413 (3.4 KB) 
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:4092 (4.0 KB)  TX bytes:4092 (4.0 KB) 

user@ubuntu:~$ ping -c 4 192.168.0.1 
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 
From 192.168.0.113 icmp_seq=2 Destination Host Unreachable 
From 192.168.0.113 icmp_seq=3 Destination Host Unreachable 
From 192.168.0.113 icmp_seq=4 Destination Host Unreachable 
cat l 
--- 192.168.0.1 ping statistics --- 
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms 
, pipe 3 
user@ubuntu:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 

user@ubuntu:~$ 

```

Since i disabled NetworkManager and ifupdown, which tool is still configuring, and probably messing up, my network at start up?

---

### Post by dmizer on 2009-02-18
Can you try pinging something outside of the LAN? Did you set a static IP, or are you using DHCP?

For example:
ping [www.google.com](www.google.com)
ping 209.85.171.100

---

### Post by Miguel on 2009-02-18
I know it won't help Herbert, but my issue was indeed a BIOS issue, and fixed it as soon as I downgraded it. I should also mention that as soon as I released the IP in WinXP (via ipconfig /release), it would no longer connect to a valid IP in winXP either, so it was an OS independent issue.

And back to topic: Herbert, does DHCP work in your card from an Ubuntu LiveCD?

---

### Post by Herbert K. on 2009-02-19
Hi,

i´m using dhcp but i tried static. /etc/network/interfaces looked like that:
```
auto lo
iface lo inet loopback

auto eth0
iface etho inet static
address 192.168.0.115
netmask 255.255.255.0
gateway 192.168.0.1
broadcast 192.168.0.255
```
And i also made the necessary changes in the router config. But that didn´t work. So i changed everything back to dhcp.

I couldn´t ping anything, didn´t matter if it was lan or wan.

- I don´t think it´s a network issue anymore:

If i use the Terminal Ctr+Alt+F1, instead of the GUI login, the network works. I can ping the router, [www.google.com](www.google.com) and i can get data through eth0. If i go back to the GUI with Ctr+Alt+F7 and log myself in, the network stops working instantly. I can go to Terminal F1 and get the network going again with sudo /etc/init.d/networking restart, but as soon as i go to the GUI the whole system crashes. Ctr+Alt+Backspace wont do anything nor Ctr+Alt+F1.

- I thought it might be acpi, so i edited /boot/grob/menu.lst and added acpi=off to the kernelline, then sudo update-grub and reboot. That didn´t help with the network and the mousepad and the keyboard wouldn´t work under GUI. So i changed everything back. 

- Now i´m stuck again and have no clue what the problem might be.

---

### Post by dmizer on 2009-02-19
Try disabling network manager with the following command:
```
sudo update-rc.d NetworkManager remove
```
Reboot.

Then edit your /etc/network/interfaces file so it looks like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```
Then try starting your network:
```
sudo dhclient eth0
```
See if that can get you online while in the GUI.

---

### Post by Herbert K. on 2009-02-20
Hi,

i did:
```

user@ubuntu:~$ sudo update-rc.d --help 
usage: update-rc.d [-n] [-f] <basename> remove 
       update-rc.d [-n] <basename> defaults [NN | SS KK] 
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] . 
		-n: not really 
		-f: force 
 
user@ubuntu:~$ sudo update-rc.d -f NetworkManager remove 
 Removing any system startup links for /etc/init.d/NetworkManager ... 
   /etc/rc2.d/S28NetworkManager 
   /etc/rc3.d/S28NetworkManager 
   /etc/rc4.d/S28NetworkManager 
   /etc/rc5.d/S28NetworkManager 


```

edited /etc/network/interfaces and made a reboot, then: 

```

user@ubuntu:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth0/00:02:3f:b9:89:11 
Sending on   LPF/eth0/00:02:3f:b9:89:11 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 

user@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:02:3f:b9:89:11  
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1 
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:4050 (4.0 KB)  TX bytes:4791 (4.7 KB) 
          Interrupt:11 Base address:0x8c00 

eth0:avahi Link encap:Ethernet  HWaddr 00:02:3f:b9:89:11  
          inet addr:169.254.5.37  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1 
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:4184 (4.1 KB)  TX bytes:4184 (4.1 KB) 

user@ubuntu:~$ ping 192.168.0.1 
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 
From 169.254.5.37 icmp_seq=1 Destination Host Unreachable 
From 169.254.5.37 icmp_seq=2 Destination Host Unreachable 
From 169.254.5.37 icmp_seq=3 Destination Host Unreachable 
^C 
--- 192.168.0.1 ping statistics --- 
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4040ms 
, pipe 3 
user@ubuntu:~$ 
```

- The good thing is, the system doesn´t crash this way. Bad: it still won´t work.

---

### Post by dishbert on 2009-02-20
This may be a 64 VS 32 Bit version problem.  I upgraded my motherboard to ASUS M3N78-EN and AMD X2 6000+ last week.

I hope we can get to the bottom of this because I can't connect with a new install of 8.04 64 Bit, either live or from the HDD.  

I have a 8.04 32 Bit install that I used on the old motherboard on another partition, and it connects fine, although Firestarter now reports:  "Failed to start firewall device eth0 is not ready", which is odd because the system seems to be using eth1:

chris@PC-Linux:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:23:54:a4:c4:30  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fea4:c430/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8635 (8.4 KB)  TX bytes:7790 (7.6 KB)
          Interrupt:219 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15800 (15.4 KB)  TX bytes:15800 (15.4 KB

When I do this from the 64 Bit version I get:

chris@Ubuntu8:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:a4:c4:30  
          inet6 addr: fe80::223:54ff:fea4:c430/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5733 (5.5 KB)
          Interrupt:251 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:54:a4:c4:30  
          inet addr:169.254.6.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:251 Base address:0x8000 

Thanks to Herbert's tip I tried pinging from outside the GUI, and it works fine there.

---

### Post by dishbert on 2009-02-20
I installed 8.10 64 bit and it connects fine. 

I have no idea what was wrong with the 8.04 version, but I'm happy to at least have one 64 bit OS to play with on my new motherboard.

---

