---
title: "BCM4318 disconnecting on Xubuntu 12.10"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by johnnyleitrim on 2013-02-05
I've checked the sticky and a few other posts, but nothing I've tried helps my situation (but I don't know if previous stuff I've done has invalidated some of the other things I've tried!)

I have a Broadcom BCM4318 PCI card (see the details below) - I can see my wireless network, it does connect to the network momentarily but then disconnects and I see this in [FONT="Courier New"]dmesg[/FONT]:

```

[33535.728221] wlan0: authenticate with b0:b2:dc:a7:94:4c
[33535.740239] wlan0: send auth to b0:b2:dc:a7:94:4c (try 1/3)
[33535.741704] wlan0: authenticated
[33535.744038] wlan0: associate with b0:b2:dc:a7:94:4c (try 1/3)
[33535.746402] wlan0: RX AssocResp from b0:b2:dc:a7:94:4c (capab=0x431 status=0 aid=1)
[33535.746835] wlan0: associated
[33549.492038] ieee80211 phy0: wlan0: No probe response from AP b0:b2:dc:a7:94:4c after 500ms, disconnecting.
[33549.500397] cfg80211: All devices are disconnected, going to restore regulatory settings
[33549.500401] cfg80211: Restoring regulatory settings
[33549.500405] cfg80211: Calling CRDA to update world regulatory domain
[33549.505298] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[33549.505302] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

I'd certainly be grateful for any help to make this stable!

Below is the output of the following commands:

```

sudo lshw -C network
lspci
uname -r
iwconfig

```

```


  *-network DISABLED      
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:0f:fe:8b:94:15
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=1.3-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:fc000000-fc01ffff memory:fc025000-fc025fff ioport:1100(size=32)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:07:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:20 memory:fc100000-fc101fff
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:23:54:5c:dd:b7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.5.0-22-generic firmware=666.2 link=no multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       physical id: 2
       bus info: usb@1:4
       logical name: eth1
       serial: 4a:60:bc:69:13:ab
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth ip=172.20.10.3 link=yes multicast=yes
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: Matrox Electronics Systems Ltd. Millenium P650 PCIe (rev 02)
07:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)




3.5.0-22-generic




lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

---

### Post by johnnyleitrim on 2013-02-06
I reinstalled Xubuntu 12.10 and followed the steps on [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) to do an offline installation of the b43 driver (for BCM4318).

It is detecting my network card, I can see and join my network, but I am seeing a lot of packet loss.

On the b43 page above, in the known issues they say:

> BCM4318 chipset: AP mode does not work because of packet loss in high transmission rates. Hard to debug & fix.

I also see messages in my dmesg output like:

```
No probe response from AP xxx after 500ms, disconnecting.

```
... and ...

```
associating with AP with corrupt beacon.
```

Does anyone know why this might be happening?  Thanks!

---

### Post by tgalati4 on 2013-02-06
If this is a PCI card, where is the antenna?  How far from the wireless router?  Does it work if the PC is 10 feet (3 m) away from the router?

I'm not sure what AP mode is.  I assume it is Access Point mode which implies Ad Hoc network.  You want Infrastructure Network, not Ad Hoc.  Ad Hoc is used to carry the signal and hop from machine-to-machine.  Infrastructure is one wireless router and a bunch of PC's with wireless connecting to it.  How is your network set up?

---

### Post by johnnyleitrim on 2013-02-06
> **tgalati4 said:**
> If this is a PCI card, where is the antenna?  How far from the wireless router?  Does it work if the PC is 10 feet (3 m) away from the router?

I'm not sure what AP mode is.  I assume it is Access Point mode which implies Ad Hoc network.  You want Infrastructure Network, not Ad Hoc.  Ad Hoc is used to carry the signal and hop from machine-to-machine.  Infrastructure is one wireless router and a bunch of PC's with wireless connecting to it.  How is your network set up?

Thanks for the reply.  The antenna is screwed into the PCI card, so it's at the back of the machine.  The PC is within 3 metres of the router, and has direct line-of-sight (if that makes any difference).

I'm trying to connect to a router, so I would expect the mode is infrastructure.  I didn't set the mode on the card specifically, so I'm assuming it's using infrastructure mode?

---

### Post by wildmanne39 on 2013-02-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by johnnyleitrim on 2013-02-07
Thanks for the reply Wildman.  Attached is the output of the script.

---

### Post by wildmanne39 on 2013-02-07
Hi, your link quality is slow and signal strength, how far away are you from the router?

You should change your encryption in your router to just wpa2 if you have that option it will work much better then wpa/wpa2.

Please set your wireless settings to match the screenshots.
Thanks

---

### Post by johnnyleitrim on 2013-02-07
Thanks for the reply and tips Wildman.  I made the changes that you suggested.  It didn't help, but I went to check the antenna on my wireless card - and it looked like it was a bit frayed.  I removed the antenna, and since then I've had a stable (albeit slow) connection.

I'll get a new antenna for the card, attach it and see if that makes an improvement, and report back.

Thanks again for your help.

---

### Post by wildmanne39 on 2013-02-07
Hi, your welcome! That card usually works good once it is setup so the antenna may be your problem.

Also you can try changing the channel you may be getting interference,
Thanks

---

### Post by johnnyleitrim on 2013-02-13
Just a follow up to say that changing the antenna has done the trick.  I'm getting consistent speeds and no drops so far.  Thanks!

---

### Post by wildmanne39 on 2013-02-18
Hi, your welcome! Glad it is working.
Enjoy

---

