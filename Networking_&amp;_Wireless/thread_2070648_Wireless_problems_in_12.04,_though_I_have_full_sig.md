---
title: "Wireless problems in 12.04, though I have full signal"
date: 2012-10-13
forum: Networking &amp; Wireless
---

### Post by chemicalblue on 2012-10-13
Alright so I'm a bit new to ubuntu/linux in general, and ever since I switched from windows 7 I haven't had the greatest time with the internet. I'm connected with high signal strengths, but a lot of the pages I go to won't load. I'm also not able to download and install programs at the moment (says something about not being able to fetch something).

I've been reading forums all night, and the only thing I've found to help out was disabling IPv6. It made more sites work, but I'm still having a lot of problems. 

I have a Toshiba Satellite a505. I'm not sure at the moment exactly what a505 it is. My router is an XFINITY Wireless Gateway TG852G. I can't use a wired connection at the moment- no ethernet cable in the house right now.

I've used the network manager tool and it came up with this:

```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [HOME-51C2] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        70:1A:04:4E:83:3E

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *HOME-51C2:      Infra, 00:1D:D1:33:51:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    linksys:         Infra, 68:7F:74:EC:25:08, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    marty:           Infra, C8:3A:35:42:C9:50, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WPA2
    ATT5967:         Infra, 4C:60:DE:B1:2D:A0, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    HOME-B3B8:       Infra, 00:26:F3:54:B3:B8, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    2WIRE872:        Infra, 00:24:56:28:B7:01, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WEP
    HPD110a.8C57D6:  Ad-Hoc, 02:22:32:3E:7A:3D, Freq 2437 MHz, Rate 54 Mb/s, Strength 59
    HOME-4F22:       Infra, 00:1D:D0:1A:4F:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    Gonzalez Family: Infra, E0:91:F5:E4:80:F6, Freq 2417 MHz, Rate 54 Mb/s, Strength 94 WEP
    2WIRE859:        Infra, 3C:EA:4F:86:F8:D9, Freq 2412 MHz, Rate 54 Mb/s, Strength 97 WEP
    ATT4902:         Infra, 74:44:01:0C:B0:4A, Freq 2412 MHz, Rate 54 Mb/s, Strength 95 WPA2
    2WIRE612:        Infra, 98:2C:BE:5A:B5:C9, Freq 2412 MHz, Rate 54 Mb/s, Strength 99 WEP
    2WIRE963:        Infra, 00:23:51:5E:7E:D9, Freq 2412 MHz, Rate 54 Mb/s, Strength 99 WEP

  IPv4 Settings:
    Address:         10.0.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:26:6C:30:51:58

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```


I can only understand a bit of it. Help, please?

EDIT: More info.

lspci


```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
04:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
04:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
04:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
mikey@MechanicalHand:~$ 
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:26:6c:30:51:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:766310 (766.3 KB)  TX bytes:766310 (766.3 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:4e:83:3e  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe4e:833e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4404978 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2768441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1423190658 (1.4 GB)  TX bytes:1367267219 (1.3 GB)

```

And that's all I have.

---

### Post by kurt18947 on 2012-10-13
I'm not familiar with that chip set. It would be preferable to 'fix' the existing driver.  If you don't get a better reply in a reasonable time, you could try downloading and installing Realtek's driver.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I've used Realtek's drivers for an 8188Cus device and the install script worked fine.  Do be aware with this solution that a kernel upgrade will 'kill' the adapter.  The fix is easy - rerun the installer script.  But do keep the download where you can find it again.  You may or may not have to blacklist the current driver.  The current driver's name can be found by running "lsmod" in a terminal.

---

### Post by chemicalblue on 2012-10-13
> **kurt18947 said:**
> I'm not familiar with that chip set. It would be preferable to 'fix' the existing driver.  If you don't get a better reply in a reasonable time, you could try downloading and installing Realtek's driver.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I've used Realtek's drivers for an 8188Cus device and the install script worked fine.  Do be aware with this solution that a kernel upgrade will 'kill' the adapter.  The fix is easy - rerun the installer script.  But do keep the download where you can find it again.  You may or may not have to blacklist the current driver.  The current driver's name can be found by running "lsmod" in a terminal.


For some reason that site didn't work for me. Like I was able to get to it, but when I clicked on the mirror to get the driver it prompted me to enter a password I don't have.

---

### Post by ahallubuntu on 2012-10-13
Try again.  I have downloaded from their site many times and have even built drivers for your exact chipset from Realtek's site.  I tried again now.  No password asked.

Try downloading on another computer to a flash drive and copy the zip file over, if need be.

FYI, you may have to blacklist the existing 8191/8192 driver before installing the new one.

---

### Post by chemicalblue on 2012-10-13
> **ahallubuntu said:**
> Try again.  I have downloaded from their site many times and have even built drivers for your exact chipset from Realtek's site.  I tried again now.  No password asked.

Try downloading on another computer to a flash drive and copy the zip file over, if need be.

FYI, you may have to blacklist the existing 8191/8192 driver before installing the new one.

Yeah it's still doing the same thing. It tells me the frameload was interrupted, and then firefox opens (I'm using midori) and prompts me for the password. It specifically says "Enter password for WebUser on ftp://209.222.7.36"

As far as downloading on another computer, that will take maybe a day or so. There aren't any other computers in the house, but I can get a friend to do it for me.

Thanks for helping me, by the way. Sorry for the lack of know how.

EDIT: It's starting to load sites better, but a lot of the time midori isn't able to resolve the host name.

---

### Post by chemicalblue on 2012-10-13
Okay so I have the driver. But I'm not sure how to install. I know how to blacklist the other driver, but I can't find anything on installing the new one.

Again, sorry for the lack of know how.

---

### Post by ahallubuntu on 2012-10-13
Unzip the downloaded file.  Then open a terminal and navigate (cd) to the directory where it was all unzipped.

I think you have to make the installer executable:

sudo chmod 755 ./install.sh

Then, just type

sudo ./install.sh

You may need to add the  module name to the file /etc/modules so it gets loaded each time at boot.

---

### Post by chemicalblue on 2012-10-13
It says no such directory when I use sudo chmod 755 ./install.sh


There's a compat-install in one of the folders. Would that do anything or should I leave it alone?

---

### Post by ahallubuntu on 2012-10-13
Sorry - this driver is different from the one for my Realtek module.  I just downloaded and looked at it.

There is a "readme" file in the main directory, and it gives you these instructions for 12.04 that basically boil down to:

sudo make
sudo make install

(reboot the computer)

The "compat-install.sh" script is for older kernels.

---

### Post by chemicalblue on 2012-10-13
Okay, well now I believe it is installed. However, firefox is still having trouble finding sites. Midori is doing better, but I really want to use firefox. Here is the results of checks and stuff.

sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:30:51:58
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:5000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 70:1a:04:4e:83:3e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.2.0-32-generic-pae firmware=N/A ip=10.0.0.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
```

nm-tool


```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [HOME-51C2] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        70:1A:04:4E:83:3E

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    linksys:         Infra, 68:7F:74:EC:25:08, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    marty:           Infra, C8:3A:35:42:C9:50, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    belkin.ba4:      Infra, 94:44:52:FC:FB:A4, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    ATT5967:         Infra, 4C:60:DE:B1:2D:A0, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    2WIRE872:        Infra, 00:24:56:28:B7:01, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WEP
    HPD110a.8C57D6:  Ad-Hoc, 02:22:32:3E:7A:3D, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    *HOME-51C2:      Infra, 00:1D:D1:33:51:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    HOME-B3B8:       Infra, 00:26:F3:54:B3:B8, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    ATT4902:         Infra, 74:44:01:0C:B0:4A, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    Yazmin2010:      Infra, E0:91:F5:BA:BA:27, Freq 2417 MHz, Rate 54 Mb/s, Strength 14 WPA2
    HOME-4F22:       Infra, 00:1D:D0:1A:4F:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Gonzalez Family: Infra, E0:91:F5:E4:80:F6, Freq 2417 MHz, Rate 54 Mb/s, Strength 14 WEP
    2WIRE612:        Infra, 98:2C:BE:5A:B5:C9, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WEP

  IPv4 Settings:
    Address:         10.0.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:26:6C:30:51:58

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:26:6c:30:51:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51368 (51.3 KB)  TX bytes:51368 (51.3 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:4e:83:3e  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe4e:833e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5097612 (5.0 MB)  TX bytes:927887 (927.8 KB)
```

---

### Post by chemicalblue on 2012-10-13
Bump?

I really need help figuring this out. I would love to keep ubuntu, but not if I can't get on the internet.

Google isn't responding to pings anymore, and I have to struggle just to get one wep page to load.

---

### Post by steeldriver on 2012-10-13
It seems like your connection is basically up, and I don't see any dropped packets in your ifconfig - have you tried basic stuff like maybe changing your DNS servers to google's (8.8.8.8 / 8.8.4.4) instead of the (Comcast?) 75.75.75.75 and 75.75.75.76? 

Beyond that I would start checking for log messages related to wlan0 i.e.

```
dmesg | grep wlan0
```

---

### Post by chemicalblue on 2012-10-13
This is the result of dmesg | grep wlan0


```
[   20.182153] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.182633] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.881319] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 1)
[   22.882801] wlan0: authenticated
[   22.902753] wlan0: associate with 00:1d:d1:33:51:c0 (try 1)
[   22.913406] wlan0: RX AssocResp from 00:1d:d1:33:51:c0 (capab=0xc11 status=0 aid=1)
[   22.913409] wlan0: associated
[   22.925262] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.682434] wlan0: IPv6 duplicate address fe80::721a:4ff:fe4e:833e detected!
[ 4987.913383] wlan0: deauthenticating from 00:1d:d1:33:51:c0 by local choice (reason=3)
[ 4993.896196] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 1)
[ 4993.897780] wlan0: authenticated
[ 4993.900173] wlan0: associate with 00:1d:d1:33:51:c0 (try 1)
[ 4993.908902] wlan0: RX ReassocResp from 00:1d:d1:33:51:c0 (capab=0xc11 status=0 aid=1)
[ 4993.908906] wlan0: associated
[ 4999.155592] wlan0: deauthenticating from 00:1d:d1:33:51:c0 by local choice (reason=3)
[ 4999.959239] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 1)
[ 4999.960869] wlan0: authenticated
[ 4999.961164] wlan0: associate with 00:1d:d1:33:51:c0 (try 1)
[ 4999.970176] wlan0: RX ReassocResp from 00:1d:d1:33:51:c0 (capab=0xc11 status=0 aid=1)
[ 4999.970183] wlan0: associated
[ 5011.184026] wlan0: no IPv6 routers present
[ 5249.887474] wlan0: deauthenticating from 00:1d:d1:33:51:c0 by local choice (reason=3)
[ 5255.376092] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 1)
[ 5255.380282] wlan0: authenticated
[ 5255.380620] wlan0: associate with 00:1d:d1:33:51:c0 (try 1)
[ 5255.390416] wlan0: RX ReassocResp from 00:1d:d1:33:51:c0 (capab=0xc11 status=0 aid=1)
[ 5255.390423] wlan0: associated
[ 5266.616034] wlan0: no IPv6 routers present
[ 5289.667073] wlan0: deauthenticating from 00:1d:d1:33:51:c0 by local choice (reason=3)
[ 5307.882226] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 1)
[ 5307.888056] wlan0: authenticated
[ 5307.888453] wlan0: associate with 00:1d:d1:33:51:c0 (try 1)
[ 5307.899270] wlan0: RX ReassocResp from 00:1d:d1:33:51:c0 (capab=0xc11 status=0 aid=1)
[ 5307.899275] wlan0: associated
[ 5318.656130] wlan0: no IPv6 routers present
[ 5370.795884] wlan0: deauthenticating from 00:1d:d1:33:51:c0 by local choice (reason=3)
[ 5387.459797] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 1)
[ 5387.463538] wlan0: authenticated
[ 5387.463670] wlan0: associate with 00:1d:d1:33:51:c0 (try 1)
[ 5387.472505] wlan0: RX ReassocResp from 00:1d:d1:33:51:c0 (capab=0xc11 status=0 aid=1)
[ 5387.472509] wlan0: associated
[ 5398.528138] wlan0: no IPv6 routers present
[ 5839.712771] wlan0: deauthenticating from 00:1d:d1:33:51:c0 by local choice (reason=3)
[ 5848.982314] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 1)
[ 5848.984573] wlan0: authenticated
[ 5848.984777] wlan0: associate with 00:1d:d1:33:51:c0 (try 1)
[ 5848.996752] wlan0: RX ReassocResp from 00:1d:d1:33:51:c0 (capab=0xc11 status=0 aid=1)
[ 5848.996760] wlan0: associated
[ 5849.790346] wlan0: IPv6 duplicate address fe80::721a:4ff:fe4e:833e detected!
[ 7142.973845] wlan0: deauthenticating from 00:1d:d1:33:51:c0 by local choice (reason=3)
[ 7149.933666] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7150.956552] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 1)
[ 7151.156033] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 2)
[ 7151.158063] wlan0: authenticated
[ 7151.158380] wlan0: associate with 00:1d:d1:33:51:c0 (try 1)
[ 7151.167165] wlan0: RX ReassocResp from 00:1d:d1:33:51:c0 (capab=0xc11 status=0 aid=1)
[ 7151.167172] wlan0: associated
[ 7151.179330] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7161.304125] wlan0: no IPv6 routers present
[ 7252.573001] wlan0: deauthenticating from 00:1d:d1:33:51:c0 by local choice (reason=3)
[ 7253.442080] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 1)
[ 7253.444172] wlan0: deauthenticating from 00:1d:d1:33:51:c0 by local choice (reason=2)
[ 7253.456545] wlan0: authenticate with 00:1d:d1:33:51:c0 (try 1)
[ 7253.458025] wlan0: authenticated
[ 7253.458236] wlan0: associate with 00:1d:d1:33:51:c0 (try 1)
[ 7253.466943] wlan0: RX ReassocResp from 00:1d:d1:33:51:c0 (capab=0xc11 status=0 aid=1)
[ 7253.466950] wlan0: associated
```


And I tried changing to google's dns servers last night, and it didn't really do much. But I'll change to it again (I use automatic dhcp addresses only, right?) and see what it does. Thank you.

---

### Post by chemicalblue on 2012-10-13
Got it solved. I had to change NetworkManager.conf as so:

```
[ifupdown]
managed=true
```


Thanks again everyone for helping out.

---

