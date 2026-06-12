---
title: "Broadcom problem, WTF??"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by keelay42 on 2009-10-23
I cannot get my onboard wireless card to act right. My external card died on me, and I need to rectify this.
this is where I'm at right now.....stuck

HALP


kyle@kyle-laptop:~$ sudo lshw -C network; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -C usb; uname -a; dmesg | grep ound; dmesg | grep b43; dmesg | grep iwl; iwconfig; sudo /etc/init.d/networking restart
[sudo] password for kyle: 
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 01
       serial: 00:03:25:0b:86:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.3 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:65:53:40
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:f0:6e:16:a8:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
00:00.0 Host bridge [0600]: ATI Technologies Inc AGP Bridge [IGP 320M] [1002:cab0] (rev 13)
00:01.0 PCI bridge [0604]: ATI Technologies Inc PCI Bridge [IGP 320M] [1002:700f] (rev 01)
00:07.0 ISA bridge [0601]: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+] [10b9:1533]
00:08.0 Multimedia audio controller [0401]: ALi Corporation M5451 PCI AC-Link Controller Audio Device [10b9:5451] (rev 02)
00:09.0 Modem [0703]: ALi Corporation M5457 AC'97 Modem Controller [10b9:5457]
00:0a.0 CardBus bridge [0607]: Texas Instruments PCI4410 PC card Cardbus Controller [104c:ac41] (rev 02)
00:0a.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4410 FireWire Controller [104c:8017] (rev 02)
00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
00:0d.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:0d.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:0d.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)
00:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
00:10.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c4)
00:11.0 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility U1 [1002:4336]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Linux kyle-laptop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux
[    0.552205] ACPI: No dock devices found.
[    0.560066] pnp: PnP ACPI: found 10 devices
[    1.352440] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    1.743646] isapnp: No Plug & Play device found
[    2.264190] hub 1-0:1.0: USB hub found
[    2.349907] hub 2-0:1.0: USB hub found
[    2.433902] hub 3-0:1.0: USB hub found
[    2.436860] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.446819] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.389024] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0c.0
[    3.616182] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0e.0
[   17.073749] yenta_cardbus 0000:00:0a.0: CardBus bridge found [161f:2029]
[   17.531422] b43legacy-phy0: Broadcom 4306 WLAN found
[   17.552151] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   17.552180] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[    3.371682] b43-pci-bridge 0000:00:0c.0: PCI INT A -> Link[LNK2] -> GSI 10 (level, low) -> IRQ 10
[   17.531422] b43legacy-phy0: Broadcom 4306 WLAN found
[   17.552151] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   17.552180] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   17.576122] b43legacy-phy0 debug: Radio initialized
[   35.019263] input: b43legacy-phy0 as /devices/virtual/input/input10
[   35.329201] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[   35.517786] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   35.572973] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   35.792062] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   35.856576] b43legacy-phy0 debug: Chip initialized
[   35.857066] b43legacy-phy0 debug: 30-bit DMA initialized
[   35.859656] Registered led device: b43legacy-phy0:tx
[   35.859683] Registered led device: b43legacy-phy0:rx
[   35.859708] Registered led device: b43legacy-phy0:radio
[   35.859749] b43legacy-phy0 debug: Wireless interface started
[   35.868393] b43legacy-phy0 debug: Adding Interface type 2
[  459.252102] b43legacy-phy0 debug: Removing Interface type 2
[  459.298414] b43legacy-phy0 debug: Wireless interface stopped
[  459.298657] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  459.298744] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  459.298828] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  459.304122] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  459.312570] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  459.320600] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  459.328107] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 128/128
[  459.416153] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  459.424039] b43legacy-phy0 debug: Radio initialized
[  459.424053] b43legacy-phy0 debug: Radio initialized
[  459.452098] input: b43legacy-phy0 as /devices/virtual/input/input11
[  459.828068] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  459.892578] b43legacy-phy0 debug: Chip initialized
[  459.893209] b43legacy-phy0 debug: 30-bit DMA initialized
[  459.897681] Registered led device: b43legacy-phy0:tx
[  459.897730] Registered led device: b43legacy-phy0:rx
[  459.897781] Registered led device: b43legacy-phy0:radio
[  459.897839] b43legacy-phy0 debug: Wireless interface started
[  459.945465] b43legacy-phy0 debug: Adding Interface type 1
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth0=eth0.

---

### Post by duanedesign on 2009-10-23
Ubuntu 9.04 Jaunty Jackalope provides the b43 drivers, but due to copyright reasons not the proprietary firmware which is required to run your card.

If you have some other kind of internet access on your computer, you can download the firmware automatically by simply installing the b43-fwcutter package which does the download and setup for you. You will probably need to restart your computer before seeing the results. 

```
sudo apt-get install b43-fwcutter
```

If you dont have another means of internet access on your computer follow the [instructions here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").

---

### Post by keelay42 on 2009-10-28
already done that via wired connection. I went to my mothers, used her internet, and then it worked on her wireless. I got home, and I can connect to my router, but still no internet. I returned my router to default settings, hoping that would work, and it didnt. WTF??

---

### Post by Bucky Ball on 2009-10-28
So your wireless is working fine, you can connect to the router. All good. 

Open System->Admin->Network

Click the wireless option and then 'properties'. You need to match all details in there to the details of your router.

If your router is acting as a DHCP server (which it sounds like else you wouldn't be connecting with it) 'Configuration' needs to be set to 'Auto-Config (DHCP)'. You need the correct ESSID and security key (WEP or WPA). 'Enable Roaming' should be unticked.

Give that a go. You know you're connecting with your router how? Did you ping its IP or log into its configuration GUI? In your top toolbar do you have a network icon and is it looking 'connected'?

One last thing: Are you certain the ROUTER is online? The online light is there? May sound obvious but ... :)

---

### Post by t0mppa on 2009-10-28
If you're connected just fine to your router, then check your DNS & routing, they're the usual culprits on situations like this.

For DNS, try pinging 74.125.79.103 and [www.google.com](www.google.com). If only the former works, your DNS resolution isn't working properly, but you have a perfectly well working Internet connection. If neither one works, then you don't have a working connection to Internet and should check the routing.

For routing, run **netstat -r** and check that it has one (and only one) default route specified for your interface, where your router is acting as the gateway.

---

### Post by keelay42 on 2009-10-31
I have pinged both google and its i.p. already. sometimes it times out, sometimes it just takes a second. I know I have a working connection, I'm using it now from my other laptop. 
   I think I'm connected b/c the connection icon up top is showing connected with 3 bars of "signal strength". But other than that, I cannot even connect to the routers configuration page. I have my router configured the same way I have my router at my mothers, which worked fine, only difference is the one at my house (the one with the issue) is a WRT54G and the one at my mother is a Belkin something. 
  Also, when I had it working at my mothers, it was working using the external wireless adapter. Ubuntu sees my internal card, but its shaded, like its not turned on. 
   Its gettting to the point where I'm actually considering putting XP back on it. But I know its just something stupid, has to be

---

### Post by keelay42 on 2009-10-31
I take back that ping part. I cant successfully ping a dang thing. Not the ip to my router, not google, not google's ip, nothing. But it still says im connected...

---

### Post by t0mppa on 2009-10-31
Well, to make sure that the connection is made properly, you can run **cat /var/log/syslog | grep -e NetworkManager -e dhclient**. That should display all the details, especially if you're using DHCP.

As for why you cannot ping anything in case the connection is properly made, there's two things I can think of from the top off my head and those are incorrect routing and firewall blocking the traffic. For routing, troubleshooting begins from the same command I posted earlier (and seeing if it has any routes whatsoever for your wireless interface) and for firewall, **sudo iptables -L** should show all active rules.

---

