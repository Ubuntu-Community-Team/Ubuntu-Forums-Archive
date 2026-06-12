---
title: "Ubuntu 12.04 (Kernel 3.2.0) Atheros AR242x / AR542x Wireless Not Working"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by macfreak84 on 2012-06-12
Hello World,

I just installed a fresh copy of Ubuntu 12.04 and my wireless Internet is not working. I want to share my Ethernet connection through my wireless card but after configuring the Ad-Hoc network in Network Manager the network is not visible on any remote computers or devices. I also cannot see any other local wireless networks in the Networking menu. Everything appears to work on the server but the new network is not visible.

When I run lspci the output is:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
03:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 (rev 61)

The output of lsmod | grep ath is:
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211

dmesg | grep ath shows:
[   18.549137] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.549153] ath5k 0000:02:00.0: setting latency timer to 64
[   18.549204] ath5k 0000:02:00.0: registered as 'phy0'
[   19.106015] ath: EEPROM regdomain: 0x65
[   19.106019] ath: EEPROM indicates we should expect a direct regpair map
[   19.106024] ath: Country alpha2 being used: 00
[   19.106027] ath: Regpair used: 0x65
[   19.120420] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa3, PHY: 0x61)
[   19.762314] type=1400 audit(1339536029.152:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=831 comm="apparmor_parser"

Is anyone else having problems with their atheros card, and if so can you please help me find a solution??

Thanks,
MacFreak

---

### Post by macfreak84 on 2012-06-13
Please help me! Anyone?

---

### Post by sk8 on 2012-06-13
he Mac, I'm having the same issues with the same card, I've got ti where i can maintain a wifi connection while i'm connected to a powersource, however, while operating on battery power wifi disconnects and will no longer see any networks available.

There are some powermanagement issues that need to be addressed. 

I recently posted another thread inregards to my issues. I've done a 3 different fresh installs with no luck. I will report back if i am able to figure anything out.

---

### Post by macfreak84 on 2012-06-13
My computer is a MacMini so I'm not sure if the power management issue applies to my configuration. Could very well be the culprit. The wireless card works flawlessly of course in Mac OS X.

I just tried switching to ndiswrapper for the wireless driver and now my wireless connection tries to connect, then drops out before the connection can be established. What's strange is that the entry returned from lspci -knn now reads:

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Apple Inc. AR5BXB6 802.11abg Wireless Mini PCIe Card [106b:0086]
    Kernel driver in use: ndiswrapper
    Kernel modules: ath5k

Why does it list the kernel module as ath5k? Is that normal?

dmesg | grep ndis yields:
[   20.957647] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   21.449188] ndiswrapper: driver netathw (,11/05/2010,9.2.0.104) loaded
[   21.449413] ndiswrapper 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.449805] ndiswrapper 0000:02:00.0: setting latency timer to 64
[   21.994694] ndiswrapper: using IRQ 17
[   22.014247] ndiswrapper (IoRegisterPlugPlayNotification:1128): not fully implemented (yet)
[   22.416854] usbcore: registered new interface driver ndiswrapper

Any further insight?
Thanks,
MacFreak

---

### Post by macfreak84 on 2012-06-17
bump

---

### Post by dedieko on 2012-06-27
> **sk8 said:**
> he Mac, I'm having the same issues with the same card, I've got ti where i can maintain a wifi connection while i'm connected to a powersource, however, while operating on battery power wifi disconnects and will no longer see any networks available.

There are some powermanagement issues that need to be addressed. 

I recently posted another thread inregards to my issues. I've done a 3 different fresh installs with no luck. I will report back if i am able to figure anything out.

+1

Im on Acer Aspire 1830 with :

```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

running Ubuntu 12.04.

Same problem. When running on battery, the card took longer to connect and take longer reply time when pinging chillispot gateway.

```
64 bytes from 192.168.182.1: icmp_req=7971 ttl=64 time=1.37 ms
64 bytes from 192.168.182.1: icmp_req=7972 ttl=64 time=1.36 ms
64 bytes from 192.168.182.1: icmp_req=7973 ttl=64 time=1.41 ms
64 bytes from 192.168.182.1: icmp_req=7974 ttl=64 time=1.28 ms
64 bytes from 192.168.182.1: icmp_req=7975 ttl=64 time=145 ms
64 bytes from 192.168.182.1: icmp_req=7976 ttl=64 time=167 ms
64 bytes from 192.168.182.1: icmp_req=7977 ttl=64 time=189 ms
64 bytes from 192.168.182.1: icmp_req=7978 ttl=64 time=212 ms

```
the first four is when plugged, the last four is when on battery.

the only thing that I saw at syslog is anacron line everytime I plug in / off:

```
Jun 27 16:25:22 dedieko-Aspire-1830 anacron[12249]: Anacron 2.3 started on 2012-06-27
Jun 27 16:25:22 dedieko-Aspire-1830 anacron[12249]: Normal exit (0 jobs run)
Jun 27 16:27:34 dedieko-Aspire-1830 anacron[12546]: Anacron 2.3 started on 2012-06-27
Jun 27 16:27:34 dedieko-Aspire-1830 anacron[12546]: Normal exit (0 jobs run)
```

---

### Post by wewa on 2012-06-27
I have been searching all night. I don't think there is a solution for Linux atheros wifi hardware support.

I have a compaq presario c762 and lspci says that I have atheros ar242x / ar542x wireless.

I also had problems getting it to work 2 years ago with Ubuntu.

So I was forced to go to XP from Vista, instead of Linux, and that was ok until it BSOD this week and no longer boots.

I was hoping Linux Mint 13 Maya would work but only with ethernet cable.

I guess I have to go back to XP. Atheros wifi is unsupported in Linux it seems.

---

### Post by macfreak84 on 2012-07-01
bump. I could have sworn this used to work. What is really confusing is that ndiswrapper doesn't seem to work either. When I install ndiswrapper with the correct driver, the internet tries to connect (shows the pulsing signal), then drops. then tries to connect... then drops. Never fully establishing the connection.

I am so frustrated.

---

### Post by grenness on 2012-11-17
Any solution to this?

I'm struggling with the wifi capabilities of a Toshiba Satellite P200D running Ubuntu 12.10.
The wifi card is "non-existing".

Christopher

---

### Post by grenness on 2012-11-17
> **grenness said:**
> I'm struggling with the wifi capabilities of a Toshiba Satellite P200D running Ubuntu 12.10.
The wifi card is "non-existing".

Never mind, I think I fixed it by adding

```
modprobe ath5k nohwcrypt=1

```
to

/etc/rc.local

:-)

Christopher

---

### Post by summakor on 2013-03-10
This bug relating to Atheros drivers seems relevant.
[URL="https://bugzilla.novell.com/show_bug.cgi?id=731576"]
https://bugzilla.novell.com/show_bug.cgi?id=731576[/URL]

The nohwcrypt option fixed it for me on a Toshiba Satellite A105-S2001 with ath5k driver.

---

