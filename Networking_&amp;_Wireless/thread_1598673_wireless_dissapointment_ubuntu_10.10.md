---
title: "wireless dissapointment ubuntu 10.10"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by ensenadaubuntulover on 2010-10-16
loved Ubuntu for years but i feel disappointed lately with version 10.10
I saw it coming since version 10.04 when I installed and system don't recognize (or remember?) my password and could not run it at all so went back to 9.10 and al ok.

I waited until version 10.10 but I don't seem to find a way to connect wireless (asks for wep password and don't get to connect) and I don't have the faintest idea on where to start

my laptop is Fujitsu and card is Orinoco (worked like a charm out of the box on past versions)

now it does find wireless networks but ask for password and that's all

(all other netbooks wireless cameras work fine) just the Ubuntu 10.10 is what i find the fail

---

### Post by TBABill on 2010-10-16
Don't give up! You are not alone. I had the identical problem on a totally different machine. It's widespread and lots have this problem in 10.10. I reverted back to 10.04 till this is resolved. I have yet to find a fix.

You can't connect at all in 10.04? Or did I misunderstand your sentence about 9.10 and 10.04?

---

### Post by jamelt on 2010-10-18
I also find it impossible to get my wireless working in Ubuntu 10.10. Nothing is working.  I have a Dell E1505 with the Broadcom BCM 4321 Wireless Adapter.

```
jamel@eminate:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 01)
jamel@eminate:~$ 

```

```

jamel@eminate:~$ sudo rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```



```
jamel@eminate:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7d:1b:21:e8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:efcfc000-efcfffff memory:e0000000-e00fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:10:18:11:22:0e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.106 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff
```

```

jamel@eminate:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.
```


```
jamel@eminate:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

eth0      Interface doesn't support scanning.


```

```
jamel@eminate:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:18:11:22:0e  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:45ff:16ad:0:210:18ff:fe11:220e/64 Scope:Global
          inet6 addr: fe80::210:18ff:fe11:220e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21789728 (21.7 MB)  TX bytes:2938970 (2.9 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:7d:1b:21:e8  
          inet6 addr: fe80::219:7dff:fe1b:21e8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:21 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


```

---

### Post by electrik on 2010-10-22
hello, im a newbie and just thought Id mention how i got my wireless to work on all three m/c's Desktop, laptop and notebook. I found an old thread ages ago that told me to remove in network connections  edit connections all wired connections, and then in wireless security use unfortunately only the WEP 40/128 option and an appropriate key...(upto that point Id always used the far securer wpa/wpa2 option but couldnt get it to work). Had no problems ever since.  Hope this helps

Luv Ubuntu by the way, 

Electrik
[CENTER][COLOR=#000000]

[/COLOR]
[COLOR=#000000]
[/COLOR][/CENTER]
[LEFT][COLOR=#CCCCCC][FONT=Trebuchet MS][/FONT][/COLOR][/LEFT]
[CENTER][COLOR=#000000]AfrikaansAlbanianArabicBelarusianBulgarianCatalanChineseCroatianCzechDanishDetect languageDutchEnglishEstonianFilipinoFinnishFrenchGalicianGermanGreekHaitian Creole ALPHAHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianVietnameseWelshYiddish[COLOR=lightgrey]**&#8644;**[/COLOR]AfrikaansAlbanianArabicBelarusianBulgarianCatalanChineseCroatianCzechDanishDutchEnglishEstonianFilipinoFinnishFrenchGalicianGermanGreekHaitian Creole ALPHAHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianVietnameseWelshYiddish[LEFT]Detect language » English[/LEFT]


[/COLOR][/CENTER]

---

### Post by rhersel on 2010-10-22
@ jamelt

I had the same problem on my DELL Studio 15 with a Broadcom 4312 WLAN. What finally helped was replacing the standard NetworkManager with WICD as alternative. Here is how to install WICD and deinstall NM:

sudo apt-get install wicd
sudo apt-get remove --purge network-manager network-manager-gnome

---

### Post by DrR2 on 2010-10-23
Hello

Wonderful

Spent days trying to get wl working for Broadcom 4312

THANK YOU

DrR

---

### Post by stead21 on 2010-10-23
I have a Lenovo G560 laptop (Core i5) and I'm still having network drops, but I'm dual booting with Windows 7, so no biggie. I won't be going back to 10.04 because the power management on my laptop was horrible, but 10.10 has really good power management so I'm going to hold off. I also thought about doing all of my updates via wired connection, in which I saw from a couple different post could solve the wireless issue.

---

### Post by jordanthompson on 2010-11-02
> **stead21 said:**
> in which I saw from a couple different post could solve the wireless issue.

Would you please post them here?  I have yet to find one that actually fixes this problem.
thanks;)

---

### Post by countwalkerj on 2010-11-15
I just wanted to post this message for those who may be thinking about trying Ubuntu and aren't sure if they want to because they need to use a wireless adapter...

I downloaded and installed 10.10 last week on a Dell GX620 desktop at home. I installed the 64-bit version of Maverick and then restarted the desktop with my Belkin G Wireless USB adapter plugged in and voila! It worked right away. All I had to do was select my network and enter my WPA key. Big relief.

Just wanted to offer a positive experience since usually we only read about how "everyone" is having problems getting wireless networking to work in Linux. This isn't to take anything away from those experiencing problems. I've had my share of driver issues in the past, but in this instance I would say go ahead and try. It just might work!

---

### Post by HobbitTR on 2010-12-19
> **countwalkerj said:**
> I just wanted to post this message for those who may be thinking about trying Ubuntu and aren't sure if they want to because they need to use a wireless adapter...Just wanted to offer a positive experience

I agree with countwalker, in our house we have 4 laptops and NONE of them have ever had wireless problems immediately after an install and upon restart.:D  I always connect a wire during an install and upon restart, then I look for and have always found our ADSL modem on wireless. We have a Dell 1520, a VAIO VPCEB2M1E_W, a VAIO VGN_TX4XTP_B, and a NEC VERSA FP520. The NEC did not have onboard wireless but Ubuntu recognized the wireless PCMCIA card immediately.

So, go for it, Ubuntu is a good risk and a good fit for most users, especially for those who do like to "tinker" a bit. Good luck.

---

