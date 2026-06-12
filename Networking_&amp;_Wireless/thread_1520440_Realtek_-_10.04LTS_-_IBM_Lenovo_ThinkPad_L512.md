---
title: "Realtek - 10.04LTS - IBM Lenovo ThinkPad L512"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by My 2 Cents Worth on 2010-06-29
I am sorry if this seems long I tried to only list the information I thought was pertinent to my wireless issue. I do get 2 of my neighbors wireless networks to show up but mine does not and it has the strongest signal by far. I have 3 other computers connected to it  also on Ubuntu 10.04 LTS


lspci -nn | grep Realtek
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)

iwconfig wlan0
wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod | grep r8192se_pci
r8192se_pci           486547  0 

dmesg
[   10.826085] Linux kernel driver for RTL8192 based WLAN cards
[   10.826086] Copyright (c) 2007-2008, Realsil Wlan Driver
[   10.826130] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.826136] rtl819xSE 0000:03:00.0: setting latency timer to 64
[   10.826317] Adapter(8192SE) is found - DeviceID=8172
[   10.827981] jmb38x_ms 0000:02:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.827990] jmb38x_ms 0000:02:00.3: setting latency timer to 64
[   11.032215] lp: driver loaded but no devices found
[   11.547590] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b1/0xb40000
[   11.547595] serio: Synaptics pass-through port at isa0060/serio4/input0
[   11.597064] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   11.848284] thinkpad_acpi: Not yet supported ThinkPad detected!
[   11.860033]   alloc irq_desc for 22 on node -1
[   11.860036]   alloc kstat_irqs on node -1
[   11.860043] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.860112] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.274761] hda_codec: ALC269: BIOS auto-probing.
[   12.275237] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   14.899371] rtl819xSE 0000:03:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   15.229791] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   15.239829] ===>rtllib_start_scan()
[   15.240370] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.242025] r8169: eth0: link down
[   15.242454] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.577328] type=1505 audit(1277830451.942:5):  operation="profile_load" pid=1026 name="/usr/share/gdm/guest-session/Xsession"
[   15.578959] type=1505 audit(1277830451.942:6):  operation="profile_replace" pid=1027 name="/sbin/dhclient3"
[   15.579454] type=1505 audit(1277830451.942:7):  operation="profile_replace" pid=1027 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.579722] type=1505 audit(1277830451.942:8):  operation="profile_replace" pid=1027 name="/usr/lib/connman/scripts/dhclient-script"
[   18.848101] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   18.960444] type=1505 audit(1277830455.323:9):  operation="profile_load" pid=1028 name="/usr/bin/evince"
[   18.961180] type=1505 audit(1277830455.323:10):  operation="profile_load" pid=1028 name="/usr/bin/evince-previewer"
[   18.961723] type=1505 audit(1277830455.323:11):  operation="profile_load" pid=1028 name="/usr/bin/evince-thumbnailer"
[   19.059185] type=1505 audit(1277830455.423:12):  operation="profile_load" pid=1045 name="/usr/lib/cups/backend/cups-pdf"
[   19.059775] type=1505 audit(1277830455.423:13):  operation="profile_load" pid=1045 name="/usr/sbin/cupsd"
[   19.094097] type=1505 audit(1277830455.463:14):  operation="profile_load" pid=1050 name="/usr/sbin/tcpdump"
[   19.140892] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio4/serio5/input/input9
[   20.599520] ppdev: user-space parallel port driver
[   22.234514] ----------->rtl8192se_check_hw_scan()
[   22.234518] FW Scan long time without stop, stop hw scan
[   22.235531] <-----------rtl8192se_check_hw_scan()

[ 3161.164275] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3168.165222] ----------->rtl8192se_check_hw_scan()
[ 3168.165227] FW Scan long time without stop, stop hw scan
[ 3168.166238] <-----------rtl8192se_check_hw_scan()
[ 3221.137466] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 3228.143417] ----------->rtl8192se_check_hw_scan()
[ 3228.143422] FW Scan long time without stop, stop hw scan
[ 3228.144434] <-----------rtl8192se_check_hw_scan()

 sudo lshw -c network
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: f0:7b:cb:a3:e9:87
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0600000-f0603fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: c8:0a:a9:9c:53:85
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.1.15 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:34 ioport:3000(size=256) memory:f0a04000-f0a04fff(prefetchable) memory:f0a00000-f0a03fff(prefetchable) memory:f0a20000-f0a3ffff(prefetchable)

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

lsb_release -d
Description:    Ubuntu 10.04 LTS

uname -mr
2.6.32-21-generic x86_64

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                  Ignoring unknown interface eth0=eth0.

---

### Post by My 2 Cents Worth on 2010-06-30
[SOLVED]
  When I installed the OS I ran in terminal sudo apt-get update and then sudo apt-get upgrade. I ran them again a second time just to make sure LOL. So I assumed I had all the updates it needed. When I downloaded and installed my BOINC software it wasn't working so I went to the BOINC website and read: BOINC applications will fail if you do not have the “ia32” package and dependent packages installed. These packages are included with some Linux64 distributions but not others; for example, they are not installed by default with Ubuntu 6.10 and 7.04 (but can be installed manually).
 
 So I installed the "ia32" package and dependent packages, and my BOINC Manager worked. I got up this morning and there were updates to install so I installed the updates and BAM my wireless worked and is picking up all the others in the area also just as it should. So I can only assume that the 64bit version of 10.04 LTS needed the "ia32" stuff for the wireless to work and I need to get in the habit of running sudo apt-get update and sudo apt-get upgrade after I install any new packages. Thats my best guess at any rate I am slowly learning.

---

