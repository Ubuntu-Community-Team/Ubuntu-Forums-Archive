---
title: "Strange wireless shenanigans"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by jeddycakes on 2010-10-28
Hello world,

I have a bit of an annoying problem regarding wireless connectivity on my Netbook.
The netbook in question is a [COLOR="Red"]Asus eee pc 1001ha[/COLOR] with a [COLOR="Red"]RaLink RT3090 Wireless 802.11n 1T/1R PCIe[/COLOR] wireless card onboard,

Basically, when I updated to 10.04 (from a previous icky Windows XP preloaded system from when I bought it) I found the wireless non-functional. OK, I said, lets check out the old forums. I eventually happened upon .deb called 'dkms' or something (I forget) which did the trick and made me feel very clever.

BUT THEN, WHOA!

After about 6 months it just suddenly stopped working. Dammit. It wouldn't even scan for new networks ffs. I thought I was going crazy...I tried reinstalling the deb to no real effect.
Now here's the mad part; It now actively scans and picks up all manner of wireless networks but crucially *will not connect.*

I mooched around on here and, thanks to some advice, tried installing wicd and using that to connect, still to no avail. It went through the normal 'connecting' routine, hung for a bit, then came back 'Bad Password', which is BS as I'm pretty sure I know my own bloody WEP key.

I am flummoxed. I'm hoping some genius will swoop down and flex at it or something and it'll then connect. Please help me, I'm getting it in the neck from the wife about 'not being able to go on Facebook in bed'

Outputs as follows :-

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

```

lsusb:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 13d3:5108 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

iwconfig:
```
wlan0     No such device

carly@carlys-netbook:~$ iwconfig
lo        no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=92/100  Signal level:-45 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:78:6c:ae  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:fe78:6cae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:844572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:640531 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:985692491 (985.6 MB)  TX bytes:68434012 (68.4 MB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8256 (8.2 KB)  TX bytes:8256 (8.2 KB)

ra0       Link encap:Ethernet  HWaddr 1c:4b:d6:2b:a8:fe  
          inet6 addr: fe80::1e4b:d6ff:fe2b:a8fe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:651381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103544559 (103.5 MB)  TX bytes:4035 (4.0 KB)
          Interrupt:17 

```

lsmod:
```
lsmod | grep "rt3090sta"
rt3090sta             818226  1 

```

dmesg:
```
dmesg | grep "rt3090sta"
[   12.542814] rt3090sta: module license 'unspecified' taints kernel.

```

Network Config:
```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ra0
       version: 00
       serial: 1c:4b:d6:2b:a8:fe
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.3 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: e0:cb:4e:78:6c:ae
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI duplex=full firmware=N/A ip=192.168.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

```

I'm running 10.04LTS (netbook with unity) with 2.6.32-25-generic i686
architecture.

Hope this massive glut of info doesn't make anybodys eyes melt.

Thanks in advance!!

---

### Post by utilitytrack on 2010-10-28
As follow from your outputs, there is no serious problems with your wireless card. So I can give advice turn off WEP/WPA security in your network and try to connect. If no success then we will search in some other things.

---

### Post by jeddycakes on 2010-10-28
> **utilitytrack said:**
> As follows from your outputs, there is no serious problems with your wireless card.

Apart from NOT CONNECTING.

---

### Post by utilitytrack on 2010-10-28
Without emotions. If you asked for help please to follow advices that you get.

---

### Post by Clove7 on 2010-10-28
You won't fix it...it's just some random update, it messed up a lot of people's wireless. After fighting with this bull crap for weeks, I had to downgrade to 9.10...I simply can't fix it. I've done EVERYTHING, to no avail. There seems to be absolutely no problems with the wireless card, it's enabled and it will connect (no matter where you are) at 100%...but it's not actually connected. It's a little different on 2 systems I got, but oh well...I'll probably be installing something new, a little more stable than ubuntu all because of this one problem :(.
 
Btw, I've tried it with a fresh, totally updated 10.04...wouldn't work, same crap. I tried it with a completely updated, fresh copy of 10.10...same exact problem. Then I downgraded and ran the partial upgrade on 9.10...worked. So, that's the only thing I can tell ya.

---

### Post by jeddycakes on 2010-10-29
> **Clove7 said:**
> You won't fix it...it's just some random update, it messed up a lot of people's wireless. After fighting with this bull crap for weeks, I had to downgrade to 9.10...I simply can't fix it. I've done EVERYTHING, to no avail. There seems to be absolutely no problems with the wireless card, it's enabled and it will connect (no matter where you are) at 100%...but it's not actually connected. It's a little different on 2 systems I got, but oh well...I'll probably be installing something new, a little more stable than ubuntu all because of this one problem :(.
 
Btw, I've tried it with a fresh, totally updated 10.04...wouldn't work, same crap. I tried it with a completely updated, fresh copy of 10.10...same exact problem. Then I downgraded and ran the partial upgrade on 9.10...worked. So, that's the only thing I can tell ya.

Dammit! I was kind of enjoying the unity interface. What I find really odd is that it worked before with a little trickery, and now doesn't at all. Seems like a step backward if you ask me.
I'll keep my fingers crossed for Natty lol

---

