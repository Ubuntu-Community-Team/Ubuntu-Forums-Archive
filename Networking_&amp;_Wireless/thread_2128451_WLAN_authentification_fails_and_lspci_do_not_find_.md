---
title: "WLAN authentification fails and lspci do not find device"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by anno1982 on 2013-03-23
Dear all, 

yesterday I have installed lubuntu on my Toshiba Satellite 2410-404 next to an Windows XP, where the WLAN card is working. 
I have used exactly the same settings to connect with my router as done in my Netbook (ubuntu) and in my Smartphone (Android). 
The Network-Manager is showing some wireless networks from my sourrounding, but if I try to connect to my (hidden) WLAN per 
WPA2 I get the information: Passwords or keys are needed. 

Strange is that an lspci can not find my card: 
sudo lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation NV17 [GeForce4 420 Go] (rev a3)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

But: 
iwconfig
irda0     no wireless extensions.
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11b  ESSID:"CundA42.9qGh550"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:105
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

And moreover: 
sudo lshw -C network
  *-network               
       Beschreibung: Ethernet interface
       Produkt: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       Hersteller: Intel Corporation
       Physische ID: 8
       Bus-Informationen: pci@0000:02:08.0
       Logischer Name: eth0
       Version: 42
       Seriennummer: xxxx
       Größe: 100Mbit/s
       Kapazität: 100Mbit/s
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.0.21 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       Ressourcen: irq:11 memory:fceff000-fcefffff ioport:df40(Größe=64)
  *-network
       Beschreibung: Kabellose Verbindung
       Physische ID: 2
       Logischer Name: eth1
       Seriennummer: xxxx
       Fähigkeiten: ethernet physical wireless
       Konfiguration: broadcast=yes driver=orinoco_cs driverversion=3.5.0-26-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

The Seriennummer (or hardware address) is entered correctly in the configuration of the router, which usually checks for this address (I have switched it off now). 
I am using DHCP and the router is activated for bgn 2.4 GHz. I have checked the password at least ten times and I really have no idea what could went wrong. 

Thanks for any hint, Andreas

---

### Post by chili555 on 2013-03-23
> Beschreibung: Kabellose Verbindung
Physische ID: 2
Logischer Name: eth1
Seriennummer: xxxx
Fähigkeiten: ethernet physical wireless
Konfiguration: broadcast=yes driver=orinoco_cs driverversion=3.5.0-26-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11bThere, pretty clearly, is your wireless device. However, not all of these older cards are capable of WPA2. Is yours?```
sudo iwlist eth1 auth
```Ideally, you will see:> Authentication capabilities :
		WPA
		[COLOR="#FF0000"]WPA2[/COLOR]
		CIPHER-TKIP
		CIPHER-CCMP


---

