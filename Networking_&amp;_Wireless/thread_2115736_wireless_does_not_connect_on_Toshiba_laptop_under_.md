---
title: "wireless does not connect on Toshiba laptop under 12.04"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by Rhody on 2013-02-13
Hi Gang,
I have an older Toshiba laptop - a Satellite Pro 6100 - that I've just converted to Ubuntu 12.04 LTS.  Everything seems to work just find except the wireless 802.11 connection.

My wired connection is working just fine.
I enable wireless in the network connections menu and I see a list of the local wireless networks.  So far, so good.

I select my network, and it pauses for a while and then asks for my WEP key (which I enter) and it pauses for another 60 seconds and asks for my key again.  This authentication dialog appears every minute or so endlessly.  The connection is never finalized.

I turned off network security, and after a reboot, it no longer asks for authentication.  But it still does not connect.

I've installed wicd and launched wicd-client.  When I attempt to connect to the wireless network from there, it says "obtaining ip address" for about 5 minutes before failing.

I've run as many diagnostic commands as I know of (sorry for being so long-winded, but I've been at this for almost 5 days now and I'm at my wits end)  - 

sudo lshw -C network:
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:00:39:40:95:e7
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.107 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:fceff000-fcefffff ioport:df40(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:6f:79:09
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=3.2.0-37-generic-pae firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

sudo iwlist scanning
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:25:9C:54:3B:A0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:off
                    ESSID:"Paradise"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001834aadb9
                    Extra: Last beacon: 208ms ago
                    IE: Unknown: 00085061726164697365
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD740050F204104A0001101044000102103B000103104700100000000000001000000000259C543BA01021000C4C696E6B73797320496E632E10230007575254353447321024000776312E352E303110420001301054000800060050F20400011011000757525435344732100800020084103C000101

eth0      Interface doesn't support scanning.

cat /etc/network/interfaces
auto lo
iface lo inet loopback

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV17 [GeForce4 420 Go] [10de:0175] (rev a3)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)
02:0a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)
02:0b.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 32)
02:0b.1 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 32)
02:0d.0 System peripheral [0880]: Toshiba America Info Systems SD TypA Controller [1179:0805] (rev 03)

sudo lshw -short
H/W path           Device      Class          Description
=========================================================
                               system         Portable PC
/0                             bus            Portable PC
/0/0                           memory         128KiB BIOS
/0/4                           processor      Mobile Intel(R) Pentium(R) 4 - M C
/0/4/12                        memory         8KiB L1 cache
/0/4/13                        memory         512KiB L2 cache
/0/81                          memory         512MiB System Memory
/0/81/0                        memory         256MiB SODIMM SDRAM Synchronous
/0/81/1                        memory         256MiB SODIMM SDRAM Synchronous
/0/100                         bridge         82845 845 [Brookdale] Chipset Host
/0/100/1                       bridge         82845 845 [Brookdale] Chipset AGP 
/0/100/1/0                     display        NV17 [GeForce4 420 Go]
/0/100/1d                      bus            82801CA/CAM USB Controller #1
/0/100/1d.1                    bus            82801CA/CAM USB Controller #2
/0/100/1d.2                    bus            82801CA/CAM USB Controller #3
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1e/8        eth0        network        82801CAM (ICH3) PRO/100 VE (LOM) E
/0/100/1e/a                    bridge         PCI1410 PC card Cardbus Controller
/0/100/1e/b                    bridge         ToPIC100 PCI to Cardbus Bridge wit
/0/100/1e/b.1                  bridge         ToPIC100 PCI to Cardbus Bridge wit
/0/100/1e/d                    generic        SD TypA Controller
/0/100/1f                      bridge         82801CAM ISA Bridge (LPC)
/0/100/1f.1        scsi0       storage        82801CAM IDE U100 Controller
/0/100/1f.1/0      /dev/sda    disk           60GB TOSHIBA MK6021GA
/0/100/1f.1/0/1    /dev/sda1   volume         55GiB EXT4 volume
/0/100/1f.1/0/2    /dev/sda2   volume         509MiB Extended partition
/0/100/1f.1/0/2/5  /dev/sda5   volume         509MiB Linux swap / Solaris partit
/0/100/1f.1/1      /dev/cdrom  disk           DW-28E
/0/100/1f.5                    multimedia     82801CA/CAM AC'97 Audio Controller
/0/100/1f.6                    communication  82801CA/CAM AC'97 Modem Controller
/1                             power          R86F2R
/2                 eth1        network        Wireless interface

dmesg | egrep 'acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt6|rt7|usb|witch|wl'
[    0.000000] APIC: switched to apic NOOP
[    0.008758] SMP alternatives: switching to UP code
[    0.065509] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.068846] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.068852] HEST: Table not found.
[    0.077586] i2c-core: driver [aat2870] using legacy suspend method
[    0.077590] i2c-core: driver [aat2870] using legacy resume method
[    0.077993] usbcore: registered new interface driver usbfs
[    0.078025] usbcore: registered new interface driver hub
[    0.078078] usbcore: registered new device driver usb
[    0.078806] Switching to clocksource pit
[    0.098389] pnp: PnP ACPI: found 12 devices
[    0.136865] Switching to clocksource acpi_pm
[    0.139688] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.233577] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.233616] ACPI: Lid Switch [LID]
[    0.240662] ERST: Table is not found!
[    0.468600] hub 1-0:1.0: USB hub found
[    0.469405] hub 2-0:1.0: USB hub found
[    0.469942] hub 3-0:1.0: USB hub found
[    0.470159] usbcore: registered new interface driver libusual
[    0.819776] isapnp: No Plug & Play device found
[    0.880161] usb 1-1: new low-speed USB device number 2 using uhci_hcd
[    1.229692] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.671387] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input3
[    1.680434] generic-usb 0003:045E:0039.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1/input0
[    1.680478] usbcore: registered new interface driver usbhid
[    1.680482] usbhid: USB HID core driver
[    1.768429] e100 0000:02:08.0: eth0: addr 0xfceff000, irq 11, MAC addr 00:00:39:40:95:e7
[   25.882568] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.044897] lp: driver loaded but no devices found
[   27.175142] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   27.320596] found SMC SuperIO Chip (devid=0x5a rev=00 base=0x002e): LPC47N227
[   27.431911] yenta_cardbus 0000:02:0a.0: CardBus bridge found [12a3:ab01]
[   27.694300] yenta_cardbus 0000:02:0b.0: CardBus bridge found [1179:0001]
[   27.850744] yenta_cardbus 0000:02:0b.1: CardBus bridge found [1179:0001]
[   27.911115] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   27.911251] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   27.965683] [drm] nouveau 0000:01:00.0: BMP BIOS found
[   27.965699] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 2.0
[   29.425343] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.426524] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.428206] e100 0000:02:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[   29.428699] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.839795] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   30.955556] orinoco_cs 0.0: Hardware identity 0005:0004:0005:0000
[   30.955680] orinoco_cs 0.0: Station identity  001f:0001:0008:000a
[   30.955686] orinoco_cs 0.0: Firmware determined as Lucent/Agere 8.10
[   31.783181] Console: switching to colour frame buffer device 175x65
[   31.991467] orinoco_cs 0.0: Hardware identity 0005:0004:0005:0000
[   31.991603] orinoco_cs 0.0: Station identity  001f:0002:0009:0030
[   31.991609] orinoco_cs 0.0: Firmware determined as Lucent/Agere 9.48
[   31.991613] orinoco_cs 0.0: Ad-hoc demo mode supported
[   31.991617] orinoco_cs 0.0: IEEE standard IBSS ad-hoc mode supported
[   31.991621] orinoco_cs 0.0: WEP supported, 104-bit key
[   31.991625] orinoco_cs 0.0: WPA-PSK supported
[   32.421467] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   32.422449] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   33.496250] eth1: Lucent/Agere firmware doesn't support manual roaming
[   38.788226] eth1: Lucent/Agere firmware doesn't support manual roaming
[   39.696061] eth0: no IPv6 routers present
[   44.136221] eth1: Lucent/Agere firmware doesn't support manual roaming
[   49.380166] eth1: Lucent/Agere firmware doesn't support manual roaming
[   54.688261] eth1: Lucent/Agere firmware doesn't support manual roaming
[   59.964227] eth1: Lucent/Agere firmware doesn't support manual roaming
[   65.208222] eth1: Lucent/Agere firmware doesn't support manual roaming
[   70.496189] eth1: Lucent/Agere firmware doesn't support manual roaming
[   75.673721] eth1: Lucent/Agere firmware doesn't support manual roaming
[   80.860348] eth1: Lucent/Agere firmware doesn't support manual roaming
[   86.076337] eth1: Lucent/Agere firmware doesn't support manual roaming
[   91.298156] eth1: Lucent/Agere firmware doesn't support manual roaming
[   96.307938] eth1: Lucent/Agere firmware doesn't support manual roaming
[  101.551462] eth1: Lucent/Agere firmware doesn't support manual roaming
[  106.849511] eth1: Lucent/Agere firmware doesn't support manual roaming
[  112.062556] eth1: Lucent/Agere firmware doesn't support manual roaming
[  117.328235] eth1: Lucent/Agere firmware doesn't support manual roaming
[  122.639491] eth1: Lucent/Agere firmware doesn't support manual roaming
[  127.935719] eth1: Lucent/Agere firmware doesn't support manual roaming
[  133.208248] eth1: Lucent/Agere firmware doesn't support manual roaming
[  138.551451] eth1: Lucent/Agere firmware doesn't support manual roaming
[  143.760267] eth1: Lucent/Agere firmware doesn't support manual roaming
[  148.971058] eth1: Lucent/Agere firmware doesn't support manual roaming
[  154.444209] eth1: Lucent/Agere firmware doesn't support manual roaming
[  159.372230] eth1: Lucent/Agere firmware doesn't support manual roaming
[  164.664244] eth1: Lucent/Agere firmware doesn't support manual roaming
[  169.876251] eth1: Lucent/Agere firmware doesn't support manual roaming
[  175.116255] eth1: Lucent/Agere firmware doesn't support manual roaming
[  180.328949] eth1: Lucent/Agere firmware doesn't support manual roaming
[  185.652217] eth1: Lucent/Agere firmware doesn't support manual roaming
[  190.896249] eth1: Lucent/Agere firmware doesn't support manual roaming
[  196.123430] eth1: Lucent/Agere firmware doesn't support manual roaming
[  201.345598] eth1: Lucent/Agere firmware doesn't support manual roaming
[  206.569501] eth1: Lucent/Agere firmware doesn't support manual roaming
[  211.780226] eth1: Lucent/Agere firmware doesn't support manual roaming
[  217.016233] eth1: Lucent/Agere firmware doesn't support manual roaming
[  222.348471] eth1: Lucent/Agere firmware doesn't support manual roaming
[  227.564264] eth1: Lucent/Agere firmware doesn't support manual roaming
[  232.838999] eth1: Lucent/Agere firmware doesn't support manual roaming
[  238.104251] eth1: Lucent/Agere firmware doesn't support manual roaming
[  243.335383] eth1: Lucent/Agere firmware doesn't support manual roaming
[  248.596260] eth1: Lucent/Agere firmware doesn't support manual roaming
[  253.849330] eth1: Lucent/Agere firmware doesn't support manual roaming
[  259.142102] eth1: Lucent/Agere firmware doesn't support manual roaming
[  264.368256] eth1: Lucent/Agere firmware doesn't support manual roaming
[  269.584246] eth1: Lucent/Agere firmware doesn't support manual roaming
[  274.854944] eth1: Lucent/Agere firmware doesn't support manual roaming
[  280.112246] eth1: Lucent/Agere firmware doesn't support manual roaming
[  582.308280] eth1: Lucent/Agere firmware doesn't support manual roaming
[  587.554262] eth1: Lucent/Agere firmware doesn't support manual roaming
[  592.769742] eth1: Lucent/Agere firmware doesn't support manual roaming
[  597.992272] eth1: Lucent/Agere firmware doesn't support manual roaming
[  603.340285] eth1: Lucent/Agere firmware doesn't support manual roaming
[  608.560280] eth1: Lucent/Agere firmware doesn't support manual roaming
[  613.778928] eth1: Lucent/Agere firmware doesn't support manual roaming
[  619.000327] eth1: Lucent/Agere firmware doesn't support manual roaming
[  624.224265] eth1: Lucent/Agere firmware doesn't support manual roaming
[  629.435628] eth1: Lucent/Agere firmware doesn't support manual roaming
[  634.636566] eth1: Lucent/Agere firmware doesn't support manual roaming
[  640.056250] eth1: Lucent/Agere firmware doesn't support manual roaming
[  645.318802] eth1: Lucent/Agere firmware doesn't support manual roaming
[  650.600260] eth1: Lucent/Agere firmware doesn't support manual roaming
[  655.795731] eth1: Lucent/Agere firmware doesn't support manual roaming
[  661.016219] eth1: Lucent/Agere firmware doesn't support manual roaming
[  666.255467] eth1: Lucent/Agere firmware doesn't support manual roaming
[  671.500209] eth1: Lucent/Agere firmware doesn't support manual roaming
[  676.840261] eth1: Lucent/Agere firmware doesn't support manual roaming
[  682.099132] eth1: Lucent/Agere firmware doesn't support manual roaming
[  687.312245] eth1: Lucent/Agere firmware doesn't support manual roaming
[  692.500220] eth1: Lucent/Agere firmware doesn't support manual roaming
[  697.739842] eth1: Lucent/Agere firmware doesn't support manual roaming
[  702.777876] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  703.598834] eth1: Lucent/Agere firmware doesn't support manual roaming
[  708.884232] eth1: Lucent/Agere firmware doesn't support manual roaming
[  709.648649] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  711.513383] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  711.516226] e100 0000:02:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[  711.516772] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  712.004317] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  712.531636] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  712.728667] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  712.888704] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  713.376213] eth1: Lucent/Agere firmware doesn't support manual roaming
[  714.926059] eth1: Lucent/Agere firmware doesn't support manual roaming
[  718.634426] eth1: Lucent/Agere firmware doesn't support manual roaming
[  722.448069] eth0: no IPv6 routers present
[  723.398961] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  723.621634] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  723.624236] e100 0000:02:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[  723.624758] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  724.192178] eth1: Lucent/Agere firmware doesn't support manual roaming
[  729.465435] eth1: Lucent/Agere firmware doesn't support manual roaming
[  734.464065] eth0: no IPv6 routers present
[  734.921452] eth1: Lucent/Agere firmware doesn't support manual roaming
[  740.285735] eth1: Lucent/Agere firmware doesn't support manual roaming
[  745.077426] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  745.829863] eth1: Lucent/Agere firmware doesn't support manual roaming
[  751.084230] eth1: Lucent/Agere firmware doesn't support manual roaming
[  756.305430] eth1: Lucent/Agere firmware doesn't support manual roaming
[  874.729310] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  874.732210] e100 0000:02:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[  874.732882] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  885.568061] eth0: no IPv6 routers present
[ 1259.084705] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1259.656233] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1264.869609] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1270.104976] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1275.316221] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1280.537663] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1285.751076] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1290.970144] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1296.188247] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1301.452273] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1306.728244] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1311.976299] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1317.165792] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1323.307143] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1328.552262] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1333.826223] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1339.082178] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1344.301863] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1349.526415] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1354.755561] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1360.070474] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1365.341111] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1370.595957] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1375.871854] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1381.121824] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1386.322533] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1391.574530] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1396.804246] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1402.089717] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1407.291962] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1412.523766] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1417.739537] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1422.960271] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1440.173936] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1441.191023] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1449.309379] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1454.492223] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1459.708256] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1465.108434] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1470.368503] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1475.624274] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1480.900276] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1486.097575] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1491.321783] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1496.592701] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1501.813961] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1507.037001] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1581.597536] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1586.878478] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1592.174653] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1597.396112] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1602.612188] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1607.848259] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1613.124290] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1618.316459] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1623.541203] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1628.776744] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1633.996264] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1639.212249] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1942.288242] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1947.516255] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1952.776226] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1957.996249] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1963.247452] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1968.522707] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1973.768244] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1979.064166] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1984.284233] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1989.517863] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1994.739729] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2000.011091] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2005.279964] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2010.499149] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2015.738474] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2020.999519] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2026.256668] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2031.506129] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2036.787827] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2042.081510] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2047.370842] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2052.648460] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2057.982222] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2063.302305] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2068.344271] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2073.609934] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2078.867036] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2084.136178] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2089.423983] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2094.672216] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2099.943552] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2105.212325] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2110.468179] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2115.718918] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2120.971511] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2126.236261] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2131.248614] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2136.520255] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2141.772237] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2147.009778] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2152.307204] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2157.599908] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2162.866899] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2168.116162] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2173.386382] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2178.648238] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2183.890089] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2189.172130] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2491.261854] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2496.544220] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2501.800254] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2507.064186] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2512.324223] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2517.948261] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2523.192246] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2528.472067] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2533.732237] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2539.004675] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2544.276481] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2549.647444] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2554.275417] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2559.536253] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2565.178839] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2570.420282] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2575.691700] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2581.059807] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2586.310609] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2591.574341] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2596.937995] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2602.265358] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2607.517445] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2612.762419] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2617.288211] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2622.571052] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2627.856346] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2633.112701] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2638.372259] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2643.611054] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2648.857037] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2654.152210] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2659.428230] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2664.780180] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2670.086276] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2675.397754] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2680.316229] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2685.632694] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2690.921183] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2696.292220] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2701.516234] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2706.788002] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2712.060258] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2717.326380] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2722.568424] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2727.937276] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2733.219901] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 2738.474828] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 3040.326065] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 3045.642141] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 3050.882673] eth1: Lucent/Agere firmware doesn't support manual roaming

iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Paradise"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:17
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

cat /etc/modprobe.d/* | egrep 'acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist bcm43xx
blacklist bcma
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt

sudo hwinfo --netcard
> hal.1: read hal dataprocess 5250: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
20: PCI 208.0: 0200 Ethernet controller                         
  [Created at pci.318]
  Unique ID: rBUF.YtlofXqppM0
  Parent ID: 6NW+.Wc+DHj8LOy0
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:08.0
  SysFS BusID: 0000:02:08.0
  Hardware Class: network
  Model: "Toshiba America Info EtherExpress PRO/100 VE"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1031 "82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller"
  SubVendor: pci 0x1179 "Toshiba America Info Systems"
  SubDevice: pci 0x0001 "EtherExpress PRO/100 VE"
  Revision: 0x42
  Driver: "e100"
  Driver Modules: "e100"
  Device File: eth0
  Memory Range: 0xfceff000-0xfcefffff (rw,non-prefetchable)
  I/O Ports: 0xdf40-0xdf7f (rw)
  IRQ: 11 (48001 events)
  HW Address: 00:00:39:40:95:e7
  Link detected: yes
  Module Alias: "pci:v00008086d00001031sv00001179sd00000001bc02sc00i00"
  Driver Info #0:
    Driver Status: e100 is active
    Driver Activation Cmd: "modprobe e100"
  Driver Info #1:
    Driver Status: eepro100 is not active
    Driver Activation Cmd: "modprobe eepro100"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (PCI bridge)

37: PCMCIA 00.0: 0282 WLAN controller
  [Created at pcmcia.84]
  Unique ID: zbP0.lG4e6KMEdl8
  Parent ID: y9as.J5lSzbB0WR8
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:0a.0/0.0
  SysFS BusID: 0.0
  Hardware Class: network
  Model: "TOSHIBA Wireless LAN Card"
  Hotplug: CardBus
  Socket: 0
  Vendor: pcmcia 0x0156 "TOSHIBA"
  Device: pcmcia 0x0002 "Wireless LAN Card"
  Driver: "orinoco_cs"
  Driver Modules: "orinoco_cs"
  Device File: eth1
  Features: WLAN
  HW Address: 00:02:2d:6f:79:09
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pcmcia:m0156c0002f06fn00pfn00paB4585A1Apb0B537C13pcD27DEB1Apd00000000"
  Driver Info #0:
    Driver Status: hostap_cs is not active
    Driver Activation Cmd: "modprobe hostap_cs"
  Driver Info #1:
    Driver Status: orinoco_cs is active
    Driver Activation Cmd: "modprobe orinoco_cs"
  Extra Info: TOSHIBA, Wireless LAN Card, Version 01.01
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (CardBus bridge)

cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

sudo lsmod
Module                  Size  Used by
joydev                 17393  0 
michael_mic            12540  4 
orinoco_cs             12898  1 
orinoco                70112  1 orinoco_cs
cfg80211              178877  1 orinoco
snd_intel8x0           33455  2 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
nouveau               712674  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39826  1 orinoco_cs
ttm                    65344  1 nouveau
psmouse                86520  0 
drm_kms_helper         45466  1 nouveau
snd                    62218  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   197641  4 nouveau,ttm,drm_kms_helper
serio_raw              13027  0 
soundcore              14635  1 snd
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
i2c_algo_bit           13199  1 nouveau
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
pcmcia_core            21511  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
mxm_wmi                12893  1 nouveau
irda                  185517  0 
shpchp                 32325  0 
video                  19068  1 nouveau
crc_ccitt              12627  1 irda
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158479  7 bnep
ppdev                  12849  0 
toshiba_acpi           18158  0 
sparse_keymap          13658  1 toshiba_acpi
wmi                    18744  2 mxm_wmi,toshiba_acpi
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
e100                   36289  0 
usbhid                 41937  0 
hid                    77428  1 usbhid

So there's my story.  Any ideas?  All I can think of is that something is not right in my network/interfaces file, or that the orinoco_cs driver is just plain busted.

thanks

---

### Post by ahallubuntu on 2013-02-13
~

---

