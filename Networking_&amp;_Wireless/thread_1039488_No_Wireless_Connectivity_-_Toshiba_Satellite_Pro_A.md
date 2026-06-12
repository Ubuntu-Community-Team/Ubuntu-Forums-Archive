---
title: "No Wireless Connectivity - Toshiba Satellite Pro A30/Agere MPCI3A"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by JonnnyH on 2009-01-14
Folks
A newbie to Linux and have just got 8.10 up and running on my Toshiba Satellite Pro A30. Though fixed connectivity is fine, I have no wireless card/networks shown. The physical wireless 'switch' is on, and I have tried toggling the hotkey to no avail - I believe the OS is not seeing the Agere MPCI3A card that is installed. lspci gives:

jon@jon-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
jon@jon-laptop:~$ 

Fixed connectivity is working fine. Ifconfig gives:

eth0      Link encap:Ethernet  HWaddr 00:02:3f:94:af:08  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fe94:af08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1682 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1932300 (1.9 MB)  TX bytes:199555 (199.5 KB)
          Interrupt:21 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

But no wireless card is shown. Results for iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Result for sudo lshow -C network is:

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:94:af:08
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.3 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:a0:1c:7d:7e:ce
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I have looked through the troubleshooting documentation to no avail - any help greatly appreciated
Thanks!

---

### Post by davidmohammed on 2009-03-06
I've got the same model - and yes I spent ages trying to figure out wireless/no wireless on this.  Wireless on a A30 is an optional extra - in my case, it wasn't physically installed even though there was a toggle switch!

Try ebay to either buy the wireless loop and card for the laptop or just by a pcmcia card.  The latter works fine with me.

---

### Post by ottabaub on 2009-09-15
JohnnyH, I have the impression davidmohammed didn't completely read your message. I also have a Satellite A30 but not the Pro version. My laptop doesn't have the internal wireless card. I've been using a D-Link DWL-G650 which I was able to get working with madwifi in 8.04. However, after a software update it stopped working and I wasn't able to get it to work again even by backing up to an older kernel. I can see my wireless router but no amount of fiddling with the settings will allow me to connect. So finally I decided to upgrade to 9.04. The D-Link card has two little green LEDs on it that light up when the OS is booting. With 9.04 they don't light up at all and I haven't been able to figure out why. The wireless card is undetected by the system. I'm wondering if the PCMCIA port driver is not working or not activating the port. I tried installing 8.10, like you. That doesn't work for me either. And nobody seems to have a solution. I'm wondering if I shouldn't try Fedora.

---

