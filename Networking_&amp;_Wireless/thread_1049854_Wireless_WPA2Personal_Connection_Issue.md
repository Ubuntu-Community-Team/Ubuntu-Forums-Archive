---
title: "Wireless WPA2/Personal Connection Issue"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by k0d3k on 2009-01-25
I have a new install of Kubuntu 8.10.  I have followed numerous troubleshooting guides, installed the ndiswrapper, blacklisted as requested but still cannot connect to my wireless network.  My wireless router is a Linksys WRT160 running default Linksys Firmware.  The security is WPA2-Personal with an encryption method of TKIP or AES.  I can run "iwlist scan" and I see other wireless routers in my area but not mine.  I would estimate I am about 15-20 feet from my router.

The info requested to add from the how to guide is:
Dell Dimension 8400

lspci
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 002 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lspci -nn |grep 'Network Controller'
04:01.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod
Module                  Size  Used by
ndiswrapper           196380  0 

dmesg 
[   57.076375] wlan0: authenticated
[   57.076390] wlan0: associate with AP 00:17:9a:48:8c:a1
[   57.079708] wlan0: RX ReassocResp from 00:17:9a:48:8c:a1 (capab=0x421 status=0 aid=4)
[   57.079721] wlan0: associated
[   57.080311] wlan0: disassociating by local choice (reason=3)
[   71.216479] UDF-fs: Partition marked readonly; forcing readonly mount
[   71.245906] UDF-fs INFO UDF: Mounting volume '050307_1801', timestamp 2005/03/07 18:01 (1e20)
[  140.644124] ppdev0: registered pardevice
[  140.692034] ppdev0: unregistered pardevice
[  141.132569] ppdev0: registered pardevice
[  141.180161] ppdev0: unregistered pardevice
[  142.295162] ppdev0: registered pardevice
[  142.344326] ppdev0: unregistered pardevice
[  509.305427] usbcore: deregistering interface driver ndiswrapper
[  509.326721] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  509.336749] usbcore: registered new interface driver ndiswrapper
[  575.971566] wlan0: authenticate with AP 00:17:9a:48:8c:a1
[  577.850574] input: b43-phy0 as /devices/virtual/input/input8
[  578.024025] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  578.137740] Registered led device: b43-phy0::tx
[  578.139805] Registered led device: b43-phy0::rx
[  578.141732] Registered led device: b43-phy0::radio
[  578.164085] wlan0: authenticate with AP 00:17:9a:48:8c:a1
[  578.165222] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  578.165235] wlan0: authenticated
[  578.165241] wlan0: associate with AP 00:17:9a:48:8c:a1
[  578.168065] wlan0: RX AssocResp from 00:17:9a:48:8c:a1 (capab=0x421 status=0 aid=4)
[  578.168076] wlan0: associated
[  578.168393] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  588.472008] wlan0: no IPv6 routers present
[ 1096.476440] b43-pci-bridge 0000:04:01.0: PCI INT A disabled
[ 1096.614216] usbcore: deregistering interface driver ndiswrapper
[ 1107.895188] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 1107.953329] ndiswrapper: driver wmp54gs (Linksys,12/22/2004, 3.100.46.0) loaded
[ 1107.953708] ndiswrapper 0000:04:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1107.958425] ndiswrapper: using IRQ 17
[ 1108.394565] wlan0: ethernet device 00:12:17:65:81:c8 using NDIS driver: wmp54gs, version: 0x3642e00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[ 1108.395742] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1108.396762] usbcore: registered new interface driver ndiswrapper
[ 1112.420524] ADDRCONF(NETDEV_UP): wlan0: link is not ready

sudo lshw -C network
*-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:65:81:c8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wmp54gs driverversion=1.53+Linksys,12/22/2004, 3.100.4 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:51:4d:57:b3:45
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

lsb_release -d
Ubuntu 8.10

uname -mr
2.6.27-9-generic i686

Any suggestions you can give would be great.  I have the wireless network configured in my network configuration but cannot connect.  When I try to use "Windows Wireless Drivers", I specify the correct file but when I click "Configure Network" I receive an error message "Could not find a network configuration tool".

---

### Post by kevdog on 2009-01-25
Ive got a bcm4306 rev 03 chipset and I couldn't get it to work with WPA2 with ndiswrapper within Intrepid either (last successful connection was Feisty using this method).  I am now using the b43 module however without any problems and can vouch that this works well with WPA2

---

### Post by k0d3k on 2009-01-25
Thanks for the tip.  Can you confirm if I should be following this link for the info? 
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by k0d3k on 2009-01-25
Or I have another wireless card, if I remember correctly, the driver was "AirForce One".  The brand and model is Linksys WMP54GS v1.1.  Will that work with the ndiswrapper?

---

### Post by kevdog on 2009-01-25
Airforce One is a broadcom chipset as well.  If you can connect to the internet, ubuntu should automatically the b43 driver for you (and yes it is the driver in the link you mentioned).  You might have to install the firmwre manually however -- which is the actual binary code that directly interacts with the hardware otherwise known as the HAL layer.  I can't remember.  

See if you have at least part of the driver installed already.

modinfo b43

If that comes up with something then you are on the right track!

---

### Post by k0d3k on 2009-01-25
Would it be best to uninstall the ndiswrapper then?

---

### Post by Ayuthia on 2009-01-25
If you don't want to uninstall, you can just blacklist ndiswrapper and it won't be used:
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by k0d3k on 2009-01-25
Got it working, thank you both of you for the advice.  I am now replying wirelessly now instead of with the ugly cat5 running across my house :)

---

### Post by kevdog on 2009-01-25
You can blacklist ndiswrapper or simply remove it from the /etc/modules file since its an external kernel module and won't be specifically loaded on boot unless there are instructions too!

---

### Post by Weirdly on 2009-02-05
I have a similar problem. I'm trying to connect Kubuntu 8.10 to my router via WPA2 with CCMP (AES). I followed [this HOW-TO]("http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html") to get my Broadcom wireless working with ndiswrapper. I can access my neighbors unsecured connection now, but I can't connect to my own router.

I'm using knetworkmanager which apparently does a lot of things in its own way without using the normal configuration files, so nothing I've found seems to apply.  I have no /etc/wpa_supplicant.conf, for example, and I can't tell if I should have one with knetworkmanager.

Should I get rid of knetworkmanager and do things differently?  Should I configure wpa_supplicant and then knetworkmanager will succeed in managing the connection? If it makes a difference, I've only use a wired connection on this laptop to get the (large number of) updates for Kubuntu after installation, so if I lose the ability to automatically switch among available connections, it won't be a terrible loss. On the other hand, I do have an upstairs and a downstairs router (on different channels, of course), so automatically switching between them would be nice.

---

