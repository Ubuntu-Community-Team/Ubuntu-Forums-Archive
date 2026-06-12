---
title: "Ubuntu 10.04 wireless connected, no internet access"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by Kallash on 2011-08-26
Hi,

I have installed ubuntu 10.04 and STA wireless driver. I am using a wimax modem, the wireless is connected (have IP addresses) but I do not have access to the internet.

I also have installed a windows XP as a guest OS (ubuntu is the host) on vmware. By using a bridged network connection, I am able to access internet. So I guess the problem is related to the ubuntu wireless driver.

Any ideas?

---

### Post by fdrake on 2011-08-26
results of:
```

iwconfig
sudo lshw -c network

```

---

### Post by Kallash on 2011-08-26
Thanks for the fast reply. These are the results:

```

~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:202  Noise level:170
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

pan0      no wireless extensions.

```for lswh: command not found
I tried installing lswh. There were lsw and lswm, but no lswh.

---

### Post by fdrake on 2011-08-26
> **Kallash said:**
> Thanks for the fast reply. These are the results:

```

~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:202  Noise level:170
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

pan0      no wireless extensions.

```for lswh: command not found
I tried installing lswh. There were lsw and lswm, but no lswh.

my bad i meant **lshw**!

---

### Post by Kallash on 2011-08-26
Excuse me.

```

~$ sudo lshw -c network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:cb:10:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:d4:89:41
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff

```

---

### Post by fdrake on 2011-08-26
> 
```

eth1      IEEE 802.11  [COLOR="Red"]**Access Point: Not-Associated**[/COLOR]   
          Link Quality:5  Signal level:202  Noise level:170
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```


you don't have an access point to your router!
i have to go now but i will check this thread later on tonight.
check this, may help: [http://ubuntuforums.org/showthread.php?t=1510828](http://ubuntuforums.org/showthread.php?t=1510828)

---

### Post by Kallash on 2011-08-26
I searched for > IEEE 802.11  [COLOR=Red]**Access Point: Not-Associated**[/COLOR] but found nothing useful. The results for rout and ping commands are:

```

~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
192.168.141.0   *               255.255.255.0   U     0      0        0 vmnet8
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         kallash.local 0.0.0.0         UG    0      0        0 eth1

```and

```

~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.054 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.042 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.043 ms
^C
--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.042/0.046/0.054/0.007 ms

```Thanks for now.

---

### Post by wildmanne39 on 2011-08-26
Hi, open a terminal please and run this command.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
then disconnect your wired connection and restart your computer if you still can not connect post the out come of these commands.
```
lsmod | grep b43
```
```
rfkill list all
```
```
dmesg | grep b43
```
Thank you

---

### Post by Kallash on 2011-08-27
Hi wildmanne39,

I installed b43-fwcutter and firmware-b43-installer. I restarted the computer but the problem is not solved. Apt-get couldn't find firmware-b43-installer and I downloaded a .deb package and installed it manually.

These are the results of the commands you wanted to see:

```

$ lsmod | grep 43
bnep                    9436  2 
mii                     4381  1 b44
videodev               34361  1 uvcvideo
intel_agp              24375  0

``````

$ lsmod | grep 44
b44                    25574  0 
ssb                    38934  1 b44
mii                     4381  1 b44
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

``````

$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

``````

$ dmesg | grep b43
$

```Nothing found for b43.
```

$ dmesg | grep b44
[   20.060433] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.124092] b44.c:v2.0
[  189.816413] b44: eth0: Link is up at 100 Mbps, full duplex.
[  189.816420] b44: eth0: Flow control is off for TX and off for RX.

``````

$ dmesg | grep 43
[    0.000000] ACPI: DSDT 7fe6f800 05658 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] pcpu-alloc: s36312 r0 d21032 u2097152 alloc=1*4194304
[    0.000000] Memory: 2050664k/2095540k available (4675k kernel code, 43504k reserved, 2127k data, 668k init, 1186236k highmem)
[    0.004043] Mount-cache hash table entries: 512
[    0.031060] ftrace: allocating 21725 entries in 43 pages
[    0.243013] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.243016] pci 0000:00:01.0: PME# disabled
[    0.243106] pci 0000:00:1a.0: reg 20 io port: [0x6f20-0x6f3f]
[    0.243172] pci 0000:00:1a.1: reg 20 io port: [0x6f00-0x6f1f]
[    0.243244] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
[    0.243310] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.243316] pci 0000:00:1a.7: PME# disabled
[    0.243371] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfebfc000-0xfebfffff]
[    0.243434] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.243438] pci 0000:00:1b.0: PME# disabled
[    0.243534] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.243539] pci 0000:00:1c.0: PME# disabled
[    0.243639] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.243644] pci 0000:00:1c.1: PME# disabled
[    0.243745] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.243750] pci 0000:00:1c.3: PME# disabled
[    0.243818] pci 0000:00:1d.0: reg 20 io port: [0x6f80-0x6f9f]
[    0.243885] pci 0000:00:1d.1: reg 20 io port: [0x6f60-0x6f7f]
[    0.243951] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
[    0.244304] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.244360] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.244368] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.244376] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.244384] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.244391] pci 0000:00:1f.1: reg 20 io port: [0x6fa0-0x6faf]
[    0.334323] NET: Registered protocol family 2
[    0.335881] type=2000 audit(1314431463.335:1): initialized
[    0.343959] highmem bounce pool size: 64 pages
[    0.343964] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.347043] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.366434] ata_piix 0000:00:1f.1: version 2.13
[    0.569434] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.576736] rtc_cmos 00:03: setting system clock to 2011-08-27 07:51:04 UTC (1314431464)
[    1.334308] ata3.00: ATA-8: SAMSUNG HM250JI, HS100-11, max UDMA7
[    1.334314] ata3.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.348437] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   19.706989] type=1505 audit(1314431483.628:2):  operation="profile_load" pid=729 name="/sbin/dhclient3"
[   19.707562] type=1505 audit(1314431483.628:3):  operation="profile_load" pid=729 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.707879] type=1505 audit(1314431483.628:4):  operation="profile_load" pid=729 name="/usr/lib/connman/scripts/dhclient-script"
[   19.945431] NET: Registered protocol family 31
[   19.945433] Bluetooth: HCI device and connection manager initialized
[   19.945435] Bluetooth: HCI socket layer initialized
[   20.049686] eth0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   20.060433] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.245435] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   21.378744] type=1505 audit(1314431485.299:5):  operation="profile_load" pid=1038 name="/usr/share/gdm/guest-session/Xsession"
[   21.378886] type=1505 audit(1314431485.299:6):  operation="profile_replace" pid=1039 name="/sbin/dhclient3"
[   21.379469] type=1505 audit(1314431485.299:7):  operation="profile_replace" pid=1039 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.379791] type=1505 audit(1314431485.299:8):  operation="profile_replace" pid=1039 name="/usr/lib/connman/scripts/dhclient-script"
[   21.383173] type=1505 audit(1314431485.303:9):  operation="profile_load" pid=1042 name="/usr/lib/cups/backend/cups-pdf"
[   21.384206] type=1505 audit(1314431485.307:10):  operation="profile_load" pid=1042 name="/usr/sbin/cupsd"
[   21.386337] type=1505 audit(1314431485.307:11):  operation="profile_load" pid=1040 name="/usr/bin/evince"
[   23.319243] /dev/vmmon[1134]: Module vmmon: registered with major=10 minor=165
[   25.043515] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.043517] Bluetooth: BNEP filters: protocol multicast
[   57.865643] bridge-eth1: up
[  129.325643] /dev/vmnet: open called by PID 1205 (vmnet-bridge)

``````

$ dmesg | grep 44
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004192] CPU: L2 cache: 6144K
[    0.031055] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032044] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.008000] CPU: L2 cache: 6144K
[    0.243244] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
[    0.243644] pci 0000:00:1c.1: PME# disabled
[    0.244035] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
[    0.244100] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.244106] pci 0000:00:1d.7: PME# disabled
[    0.244287] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.244293] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.244298] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.244304] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.244360] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.244368] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.244376] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.244384] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.244391] pci 0000:00:1f.1: reg 20 io port: [0x6fa0-0x6faf]
[    0.244449] pci 0000:00:1f.2: reg 10 io port: [0x6eb0-0x6eb7]
[    0.244456] pci 0000:00:1f.2: reg 14 io port: [0x6eb8-0x6ebb]
[    0.244464] pci 0000:00:1f.2: reg 18 io port: [0x6ec0-0x6ec7]
[    0.244472] pci 0000:00:1f.2: reg 1c io port: [0x6ec8-0x6ecb]
[    0.244480] pci 0000:00:1f.2: reg 20 io port: [0x6ee0-0x6eef]
[    0.244487] pci 0000:00:1f.2: reg 24 io port: [0xeff0-0xefff]
[    0.244518] pci 0000:00:1f.2: PME# supported from D3hot
[    0.244522] pci 0000:00:1f.2: PME# disabled
[    0.244550] pci 0000:00:1f.3: reg 10 32bit mmio: [0xfebfbf00-0xfebfbfff]
[    0.244575] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.244655] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.244671] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.244687] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.244696] pci 0000:01:00.0: reg 24 io port: [0xdf00-0xdf7f]
[    0.244705] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfea00000-0xfea1ffff]
[    0.244816] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.244819] pci 0000:00:01.0: bridge 32bit mmio: [0xfa000000-0xfeafffff]
[    0.244823] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.257944] libata version 3.00 loaded.
[    0.334410] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.335881] type=2000 audit(1314431463.335:1): initialized
[    0.366445] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.576736] rtc_cmos 00:03: setting system clock to 2011-08-27 07:51:04 UTC (1314431464)
[    3.353479] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc0000a9b2dc1]
[   18.844017] Linux agpgart interface v0.103
[   19.706989] type=1505 audit(1314431483.628:2):  operation="profile_load" pid=729 name="/sbin/dhclient3"
[   19.707562] type=1505 audit(1314431483.628:3):  operation="profile_load" pid=729 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.707879] type=1505 audit(1314431483.628:4):  operation="profile_load" pid=729 name="/usr/lib/connman/scripts/dhclient-script"
[   19.935449] USB Video Class driver (v0.1.0)
[   20.060433] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.124092] b44.c:v2.0
[   20.141975] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:d4:89:41
[   21.378744] type=1505 audit(1314431485.299:5):  operation="profile_load" pid=1038 name="/usr/share/gdm/guest-session/Xsession"
[   21.378886] type=1505 audit(1314431485.299:6):  operation="profile_replace" pid=1039 name="/sbin/dhclient3"
[   21.379469] type=1505 audit(1314431485.299:7):  operation="profile_replace" pid=1039 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.379791] type=1505 audit(1314431485.299:8):  operation="profile_replace" pid=1039 name="/usr/lib/connman/scripts/dhclient-script"
[   21.383173] type=1505 audit(1314431485.303:9):  operation="profile_load" pid=1042 name="/usr/lib/cups/backend/cups-pdf"
[   21.384206] type=1505 audit(1314431485.307:10):  operation="profile_load" pid=1042 name="/usr/sbin/cupsd"
[   21.386337] type=1505 audit(1314431485.307:11):  operation="profile_load" pid=1040 name="/usr/bin/evince"
[   23.327244] /dev/vmci[1142]: Module vmci: registered with major=10 minor=55
[  189.816413] b44: eth0: Link is up at 100 Mbps, full duplex.
[  189.816420] b44: eth0: Flow control is off for TX and off for RX.
[  253.044041] eth1: no IPv6 routers present

```

Thank you.

---

### Post by praseodym on 2011-08-27
Please show:

```
dmesg | egrep 'wl|eth1|radio|kill'
lsmod #complete
cat /etc/udev/rules.d/70-persistent-net.rules
sudo iwlist scan
```
You are using the STA-driver, which renames the interface from wlan0 to eth1.

---

### Post by Kallash on 2011-08-27
Hi again and thanks for helping,

```

$ dmesg | egrep 'wl|eth1|radio|kill'
[   20.027307] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.027321] wl 0000:0c:00.0: setting latency timer to 64
[   20.141975] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:d4:89:41
[   20.146610] udev: renamed network interface eth0 to eth1
[   20.147083] udev: renamed network interface eth1_rename to eth0
[   32.088058] eth1: no IPv6 routers present
[   57.865640] bridge-eth1: device is wireless, enabling SMAC
[   57.865643] bridge-eth1: up
[   57.865645] bridge-eth1: attached
[  127.001101] bridge-eth1: disabling the bridge
[  127.021023] bridge-eth1: down
[  127.021031] bridge-eth1: detached
[  129.325742] bridge-eth1: device is wireless, enabling SMAC
[  129.325750] bridge-eth1: up
[  129.325869] bridge-eth1: attached
[  129.326804] bridge-eth1: disabling the bridge
[  129.337915] bridge-eth1: down
[  129.337932] bridge-eth1: detached
[  129.338159] bridge-eth1: device is wireless, enabling SMAC
[  129.338168] bridge-eth1: up
[  129.338177] bridge-eth1: attached
[  139.968255] eth1: no IPv6 routers present
[  140.397706] bridge-eth1: disabling the bridge
[  140.408055] bridge-eth1: down
[  140.408070] bridge-eth1: detached
[  141.117133] bridge-eth1: device is wireless, enabling SMAC
[  141.117142] bridge-eth1: up
[  141.117148] bridge-eth1: attached
[  191.602094] bridge-eth1: disabling the bridge
[  191.616026] bridge-eth1: down
[  191.616034] bridge-eth1: detached
[  253.044041] eth1: no IPv6 routers present
[  258.757093] bridge-eth1: device is wireless, enabling SMAC
[  258.757096] bridge-eth1: up
[  258.757099] bridge-eth1: attached
[ 1047.226012] bridge-eth1: disabling the bridge
[ 1047.236036] bridge-eth1: down
[ 1047.236052] bridge-eth1: detached
[ 9529.756698] bridge-eth1: device is wireless, enabling SMAC
[ 9529.756701] bridge-eth1: up
[ 9529.756705] bridge-eth1: attached
[ 9587.088265] bridge-eth1: disabling the bridge
[ 9587.093100] bridge-eth1: down
[ 9587.093115] bridge-eth1: detached
[ 9587.108143] bridge-eth1: device is wireless, enabling SMAC
[ 9587.108145] bridge-eth1: up
[ 9587.108147] bridge-eth1: attached
[ 9587.108169] bridge-eth1: disabling the bridge
[ 9587.124245] bridge-eth1: down
[ 9587.124258] bridge-eth1: detached
[ 9587.692457] bridge-eth1: device is wireless, enabling SMAC
[ 9587.692467] bridge-eth1: up
[ 9587.692476] bridge-eth1: attached

``````

$ lsmod #complete
Module                  Size  Used by
rfcomm                 33421  4 
sco                     7917  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
binfmt_misc             6587  1 
vmnet                  40983  13 
ppdev                   5259  0 
parport_pc             25962  0 
vmblock                10766  1 
vsock                  37367  0 
vmci                   52974  1 vsock
vmmon                  62872  0 
joydev                  8740  0 
snd_hda_codec_idt      52042  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b44                    25574  0 
ssb                    38934  1 b44
mii                     4381  1 b44
lib80211_crypt_tkip     7596  0 
wl                   1959598  0 
btusb                  11053  2 
dell_wmi                1793  0 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             6888  0 
dcdbas                  5422  1 dell_laptop
psmouse                63677  0 
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
sdhci_pci               5470  0 
sdhci                  15494  1 sdhci_pci
led_class               2864  1 sdhci
nvidia               9961216  42 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
intel_agp              24375  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
agpgart                31724  2 nvidia,intel_agp
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394

``````

$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x4315 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:44:cb:10:4d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:09:d4:89:41", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:44:cb:10:4d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

``````

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1E:E5:22:68:B0
                    ESSID:"Sp Wi Lan"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-51 dBm  Noise level:-88 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1E:E5:22:64:18
                    ESSID:"Sp Wi Lan"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:2/5  Signal level:-77 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1E:E5:22:61:20
                    ESSID:"Sp Wi Lan"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-77 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 14:D6:4D:98:63:50
                    ESSID:"NWV"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 05 - Address: 00:23:69:05:BC:08
                    ESSID:"Yavari Wireless Lan"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: F4:EC:38:F5:C3:F4
                    ESSID:"TP-LINK_F5C3F4"
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-88 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

---

### Post by bkratz on 2011-08-27
> **praseodym said:**
> Please show:

```
dmesg | egrep 'wl|eth1|radio|kill'
lsmod #complete
cat /etc/udev/rules.d/70-persistent-net.rules
sudo iwlist scan
```
You are using the STA-driver, which renames the interface from wlan0 to eth1.



I suspect that the op probably now has blacklist problems after trying both the STA and B43 (even worse the wired connection may have been affected too) So I believe we should also see.


```
egrep -e b43 -e ssb  /etc/modprobe.d/*
```

---

### Post by praseodym on 2011-08-27
Did you ever install the linux-backports-modules-wireless-lucid-generic? These drivers from linux-wireless include new 80211-subsystem drivers which dont work together with the STA (I dont think you did, otherwise there would be error messages with "dmesg").

Just to be sure:

```
sudo apt-get remove --purge linux-backports-modules-wireless-lucid-generic linux-backports-modules-wireless-$(uname -r)
```
If it is uninstalled you have to reinstall the kernel plus driver:

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) linux-headers-generic dkms patch fakeroot bcmwl-kernel-source build-essential
```
It may be more than neccessary, just to be sure.

If nothing is uninstalled you can ignore the 2nd line.

---

### Post by Kallash on 2011-08-27
Here are the results:

```

$ egrep -e b43 -e ssb  /etc/modprobe.d/*
/etc/modprobe.d/blacklist-bcm43.conf:blacklist b43
/etc/modprobe.d/blacklist-bcm43.conf:blacklist b43legacy
/etc/modprobe.d/blacklist-bcm43.conf:blacklist ssb
/etc/modprobe.d/blacklist-bcm43.conf:install wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl ; modprobe --ignore-install b44
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.

```Also, linux-backports-modules-wireless-lucid-generic is not installed.
```

$ sudo apt-get remove --purge linux-backports-modules-wireless-lucid-generic linux-backports-modules-wireless-$(uname -r)
[sudo] password for kaveh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-backports-modules-wireless-lucid-generic is not installed, so not removed
Package linux-backports-modules-wireless-2.6.32-33-generic is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libglade2-ruby1.8 libgconf2-ruby libatk1-ruby1.8 libglade2-ruby libgnome2-ruby1.8 libgnomecanvas2-ruby1.8 gnome-splashscreen-manager libgnome2-ruby
  libgconf2-ruby1.8 libglib2-ruby1.8 libcairo-ruby1.8 libgdk-pixbuf2-ruby1.8 libart2-ruby1.8 libgtk2-ruby1.8 libpango1-ruby1.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by northd_tech on 2011-08-27
> **Kallash said:**
> **lsmod **
Module                  Size  Used by
[COLOR=Blue]**b44   **[/COLOR]                 25574  0 
**ssb **                   38934  1 **[COLOR=Blue]b44[/COLOR]**
mii                     4381  1 [COLOR=Blue]**b44**[/COLOR]
lib80211_crypt_tkip     7596  0 
[COLOR=Red]**wl **[/COLOR]                  1959598  0 
[COLOR=Purple]dell_wmi                1793  0 
dell_laptop             6888  0 [/COLOR] 
lib80211                5046  2 lib80211_crypt_tkip,[COLOR=Red]**wl**[/COLOR]

I can see obvious module conflicts above- the "STA" driver uses the [COLOR=Red]**wl**[/COLOR] module, along with **lib80211** and l**ib80211_crypt_tkip** modules ONLY, according to my working "STA" Broadcom "4328" that I'm using to post this wirelessly.

The "b43" and [COLOR=Blue]**b44**[/COLOR] modules are usually accompanied by that[COLOR=Blue]** ssb, mii**[/COLOR], and possibly a few other modules from what I recall (I once had to use the "b43" drivers with my 802.11n Broadcom "4328" after I abandoned the Windows drivers under Linux, although it only gave 802.11g speeds).

I think that bkratz is on the correct 'path' on the blacklisting thing somewhere near [COLOR=Green]/etc/modprobe.d/blacklist.conf,[/COLOR] and we might ought to take a look at this as well:

```
cat /etc/modules
```Also, those [COLOR=DarkOrchid][COLOR=Black][Dell][/COLOR] [COLOR=Purple]laptop keyboard driver/switch modules[/COLOR][/COLOR] have been known to cause dozens of problems/conflicts with wireless interfaces of MANY flavors, but Chili555 is probably the guy to see on that part...
========================================================
[COLOR=Red]========================================================[/COLOR]
========================================================
[COLOR=Blue]========================================================[/COLOR]
----------------------------------------------------------------------------------------------------------------------------
EDIT:  Once upon a time, the [COLOR=Blue]Broadcom 4312[/COLOR] **should have** worked with either the "b43" or the "STA" driver (although they were mutually-exclusive and needed careful blacklisting, even back then).  I'm not certain that is true of the Ubuntu 11.xx versions now, however...

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
> These packages contain Broadcom's IEEE 802.11a/b/g/n hybrid Linux® device driver for use with Broadcom's [COLOR=Blue]BCM4311-,** BCM4312**[/COLOR]-, BCM4313-, [COLOR=Red]**BCM4321-, BCM4322**[/COLOR]-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware. **There are different tars for 32-bit and 64-bit x86 CPU architectures. Make sure that you download the appropriate tar because the hybrid binary file must be of the appropriate architecture type.** The hybrid binary file is [COLOR=Magenta]**agnostic to the specific version of the Linux kernel because it is designed to perform all interactions with the operating system through operating-system-specific files and an operating system abstraction layer file. All Linux operating-system-specific code is provided in source form, making it possible to retarget to different kernel versions and fix operating system related issues.**[/COLOR]
 NOTE: **You must read the LICENSE.TXT file in the lib directory before using this software.**
 Support questions for the latest version of these drivers may be directed to [EMAIL="linux-wlan-client-support-list@broadcom.com"]linux-wlan-client-support-list@broadcom.com[/EMAIL].


---

### Post by Kallash on 2011-08-27
This is the "modules" file content:
```

$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

```I have used my wireless card for 3 years on ubuntu 8.04. That time I was using NDIS wrapper to convert my windows driver and it was forking just fine. I do not know what to do:confused:. Should I use the NDIS wrapper program again on 10.04, which I used for utilizing my wireless card when ubuntu 8.04 was installed?

---

### Post by northd_tech on 2011-08-27
No, let's not go back to **ndiswrapper** just yet, especially since that was **one** module** that wasn't **in conflict from what I read before.

Apparently you are using a 10.xx version of Ubuntu- that's a GOOD thing IMHO!  Let's try to go the "STA" way and get rid of the "b43" and "b44" stuff first.

First, let's get rid of the conflicting modules:

```
sudo rmmod ssb mii b44
sudo rmmod b43

```Then post the output of the following terminal command:

```
lsmod
```You may or may not need a restart after that, but 'in theory'- that might have fixed your wireless connection.  You still might need to set up the wireless authentication keys (WEP, WPA, WPA2, WPS, etc.) but that should be fairly easy if we can get the wireless 'radio' talking to the US DoD radio 'crew...'

Unfortunately, I'm running out of 'graveyard,' and it is apparently past my bedtime.

Peace,
NDT

---

### Post by Kallash on 2011-08-27
Something strange happening here (at least for me!). I was connected through wired. Then used the command:
```

$ sudo rmmod ssb mii b44
ERROR: Module ssb is in use by b44
ERROR: Module mii is in use by b44

```and wired connection disappeared. Then:
```

$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules

```I switched to the wireless and pulled off the wire. I was connected through wireless and everything seemed fine (and I was very happy to see that!).
lsmod output is now:
```

$ lsmod
Module                  Size  Used by
rfcomm                 33421  4
sco                     7917  2
bridge                 45582  0
stp                     1655  1 bridge
bnep                    9436  2
binfmt_misc             6587  1
l2cap                  30624  16 rfcomm,bnep
vmnet                  40983  13
ppdev                   5259  0
parport_pc             25962  0
vmblock                10766  1
vsock                  37367  0
vmci                   52974  1 vsock
vmmon                  62872  0
joydev                  8740  0
snd_hda_codec_idt      52042  1
snd_hda_intel          22069  2
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0
snd_seq_oss            26722  0
dell_wmi                1793  0
snd_seq_midi            4557  0
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
btusb                  11053  2
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
dell_laptop             6888  0
dcdbas                  5422  1 dell_laptop
fbcon                  35102  71
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvcvideo               57374  0
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
sdhci_pci               5470  0
sdhci                  15494  1 sdhci_pci
led_class               2864  1 sdhci
psmouse                63677  0
serio_raw               3978  0
ssb                    38934  0
mii                     4381  0
lib80211_crypt_tkip     7596  0
wl                   1959598  0
lib80211                5046  2 lib80211_crypt_tkip,wl
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0
output                  1871  1 video
nvidia               9961216  42
vga16fb                11385  1
vgastate                8961  1 vga16fb
intel_agp              24375  0
agpgart                31724  2 nvidia,intel_agp
lp                      7028  0
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0
hid                    67288  1 usbhid
ohci1394               26950  0
ieee1394               81181  1 ohci1394

```Then I restarted the computer. Wired connection is back now, but the same problem again! It is driving me crazy (I mean it!).

lsmod output now: (not working)
```

$ lsmod
Module                  Size  Used by
rfcomm                 33421  4 
sco                     7917  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
binfmt_misc             6587  1 
vmnet                  40983  13 
ppdev                   5259  0 
parport_pc             25962  0 
vmblock                10766  1 
vsock                  37367  0 
vmci                   52974  1 vsock
vmmon                  62872  0 
snd_hda_codec_idt      52042  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
b44                    25574  0 
snd_seq_midi            4557  0 
ssb                    38934  1 b44
mii                     4381  1 b44
snd_rawmidi            19056  1 snd_seq_midi
lib80211_crypt_tkip     7596  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
btusb                  11053  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
dell_wmi                1793  0 
wl                   1959598  0 
sdhci_pci               5470  0 
sdhci                  15494  1 sdhci_pci
uvcvideo               57374  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
nvidia               9961216  42 
dell_laptop             6888  0 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2864  1 sdhci
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
video                  17375  0 
output                  1871  1 video
dcdbas                  5422  1 dell_laptop
psmouse                63677  0 
serio_raw               3978  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
intel_agp              24375  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 nvidia,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394

```

---

### Post by praseodym on 2011-08-27
Hello,

b44 is the driver for wired, b43 for wireless. With kernel 2.6.32 from Lucid b43 doesnt work (yet). You may try to reinstall the current kernel and the STA driver as mentioned above and reboot.

Controls:

```
lsmod
dmesg | egrep 'wl|wmi|eth1'
iwconfig
route -n
cat /etc/resolv.conf
sudo iwlist scan
```

---

### Post by Kallash on 2011-08-27
Hi praseodym,

> b44 is the driver for wired, b43 for wireless. With kernel 2.6.32 from  Lucid b43 doesnt work (yet). You may try to reinstall the current kernel  and the STA driver as mentioned above and reboot.I am not sure what you mean by reinstalling the kernel and STA driver. Would you please tell me how to do it? Thanks in advance.

---

### Post by praseodym on 2011-08-27
```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) dkms patch fakeroot bcmwl-kernel-source build-essential
```

Please show the outputs.

---

### Post by Kallash on 2011-08-27
I did what you said. The results are:

```

$ sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) dkms patch fakeroot bcmwl-kernel-source build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglade2-ruby1.8 libgconf2-ruby libatk1-ruby1.8 libglade2-ruby libgnome2-ruby1.8 libgnomecanvas2-ruby1.8 gnome-splashscreen-manager libgnome2-ruby
  libgconf2-ruby1.8 libglib2-ruby1.8 libcairo-ruby1.8 libgdk-pixbuf2-ruby1.8 libart2-ruby1.8 libgtk2-ruby1.8 libpango1-ruby1.8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev xz-utils
Suggested packages:
  debian-keyring debian-maintainers
The following NEW packages will be installed:
  build-essential dpkg-dev xz-utils
0 upgraded, 3 newly installed, 6 reinstalled, 0 to remove and 0 not upgraded.
Need to get 2,095kB/34.4MB of archives.
After this operation, 2,642kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  linux-image-2.6.32-33-generic bcmwl-kernel-source xz-utils dpkg-dev build-essential dkms fakeroot linux-headers-2.6.32-33-generic patch
Install these packages without verification [y/N]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 [895kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid/main xz-utils 4.999.9beta+20091116-1 [228kB]
Get:3 http://archive.ubuntu.com/ubuntu/ lucid-updates/main dpkg-dev 1.15.5.6ubuntu4.5 [654kB]
Get:4 http://archive.ubuntu.com/ubuntu/ lucid/main build-essential 11.4build1 [7,278B]
Get:5 http://archive.ubuntu.com/ubuntu/ lucid-updates/main dkms 2.1.1.2-2ubuntu1 [70.8kB]
Get:6 http://archive.ubuntu.com/ubuntu/ lucid/main fakeroot 1.14.4-1ubuntu1 [118kB]
Get:7 http://archive.ubuntu.com/ubuntu/ lucid/main patch 2.6-2ubuntu1 [123kB]
Fetched 2,095kB in 5s (415kB/s)
(Reading database ... 316250 files and directories currently installed.)
Preparing to replace linux-image-2.6.32-33-generic 2.6.32-33.72 (using .../linux-image-2.6.32-33-generic_2.6.32-33.72_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.32-33-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Selecting previously deselected package xz-utils.
Unpacking xz-utils (from .../xz-utils_4.999.9beta+20091116-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.5.6ubuntu4.5_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4build1_i386.deb) ...
Preparing to replace dkms 2.1.1.2-2ubuntu1 (using .../dkms_2.1.1.2-2ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace fakeroot 1.14.4-1ubuntu1 (using .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Unpacking replacement fakeroot ...
Preparing to replace linux-headers-2.6.32-33-generic 2.6.32-33.72 (using .../linux-headers-2.6.32-33-generic_2.6.32-33.72_i386.deb) ...
Unpacking replacement linux-headers-2.6.32-33-generic ...
Preparing to replace patch 2.6-2ubuntu1 (using .../patch_2.6-2ubuntu1_i386.deb) ...
Unpacking replacement patch ...
Processing triggers for man-db ...
Setting up linux-image-2.6.32-33-generic (2.6.32-33.72) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-33.72 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-33.72 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic

Setting up xz-utils (4.999.9beta+20091116-1) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...

Setting up linux-headers-2.6.32-33-generic (2.6.32-33.72) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic

Setting up patch (2.6-2ubuntu1) ...
Setting up dpkg-dev (1.15.5.6ubuntu4.5) ...
Setting up build-essential (11.4build1) ...
Setting up dkms (2.1.1.2-2ubuntu1) ...

Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.32-33-generic
Building for architecture i686
Building initial module for 2.6.32-33-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-33-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic

``````

$ lsmod
Module                  Size  Used by
rfcomm                 33421  4 
sco                     7917  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
binfmt_misc             6587  1 
l2cap                  30624  16 rfcomm,bnep
vmnet                  40983  13 
ppdev                   5259  0 
parport_pc             25962  0 
vmblock                10766  1 
vsock                  37367  0 
vmci                   52974  1 vsock
vmmon                  62872  0 
snd_hda_codec_idt      52042  1 
btusb                  11053  2 
dell_wmi                1793  0 
joydev                  8740  0 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
b44                    25574  0 
ssb                    38934  1 b44
mii                     4381  1 b44
lib80211_crypt_tkip     7596  0 
wl                   1959598  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               5470  0 
dell_laptop             6888  0 
sdhci                  15494  1 sdhci_pci
led_class               2864  1 sdhci
dcdbas                  5422  1 dell_laptop
nvidia               9961216  42 
vga16fb                11385  1 
psmouse                63677  0 
vgastate                8961  1 vga16fb
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lib80211                5046  2 lib80211_crypt_tkip,wl
intel_agp              24375  0 
agpgart                31724  2 nvidia,intel_agp
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394

``````

$ dmesg | egrep 'wl|wmi|eth1'
[   19.929076] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.929088] wl 0000:0c:00.0: setting latency timer to 64
[   20.046535] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:d4:89:41
[   20.053863] udev: renamed network interface eth1 to eth0
[   20.103441] udev: renamed network interface eth0_rename to eth1
[   32.408056] eth1: no IPv6 routers present
[   57.969590] bridge-eth1: device is wireless, enabling SMAC
[   57.969594] bridge-eth1: up
[   57.969596] bridge-eth1: attached
[   90.819729] bridge-eth1: disabling the bridge
[   90.829019] bridge-eth1: down
[   90.829025] bridge-eth1: detached
[   92.935510] bridge-eth1: device is wireless, enabling SMAC
[   92.935518] bridge-eth1: up
[   92.935767] bridge-eth1: attached
[   92.937142] bridge-eth1: disabling the bridge
[   92.949056] bridge-eth1: down
[   92.949065] bridge-eth1: detached
[   92.949183] bridge-eth1: device is wireless, enabling SMAC
[   92.949187] bridge-eth1: up
[   92.949191] bridge-eth1: attached
[  103.740239] eth1: no IPv6 routers present
[  104.024219] bridge-eth1: disabling the bridge
[  104.033034] bridge-eth1: down
[  104.033048] bridge-eth1: detached
[  104.817447] bridge-eth1: device is wireless, enabling SMAC
[  104.817450] bridge-eth1: up
[  104.817453] bridge-eth1: attached
[  505.644150] bridge-eth1: disabling the bridge
[  505.656065] bridge-eth1: down
[  505.656080] bridge-eth1: detached
[  597.817360] bridge-eth1: device is wireless, enabling SMAC
[  597.817363] bridge-eth1: up
[  597.817365] bridge-eth1: attached

``````

$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:208  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

pan0      no wireless extensions.

``````

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.48.0    0.0.0.0         255.255.255.0   U     2      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.141.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.48.1    0.0.0.0         UG    0      0        0 eth1

``````

$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.2
nameserver 192.168.1.3

``````

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1E:E5:22:68:B0
                    ESSID:"Sharafi Wireless Lan"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-49 dBm  Noise level:-87 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1E:E5:22:64:18
                    ESSID:"Sharafi Wireless Lan"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:2/5  Signal level:-74 dBm  Noise level:-78 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 50:67:F0:7C:28:30
                    ESSID:"zyxel-shatel"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:15:6D:FC:0C:13
                    ESSID:"Toofantelco-Azadegan"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-91 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: F4:EC:38:F5:C3:F4
                    ESSID:"TP-LINK_F5C3F4"
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:1/5  Signal level:-90 dBm  Noise level:-88 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

---

### Post by fdrake on 2011-08-29
A:source :[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218) Post#1.
> 
  B43 driver
Known issues:
1) If you have an ethernet driver supported by ssb/b44, you will not be able to use this

B:Source [http://wiki.debian.org/wl#Known_Issues](http://wiki.debian.org/wl#Known_Issues)
> 
  STA driver
**_Known Issue_**s
      The Sonics Silicon Backplane driver (ssb) conflicts with the wl driver
                .   .   .
      Frequent disconnections can be experienced. 
                .   .   .
      Monitor mode is not supported. 

[COLOR="Red"]
just wanted to point out that your b43 driver and STA driver will not work, reason being is that you have an ethernet driver supported by ssb/b44. [/COLOR]

You can still use ndiswrapper and install a win driver and hope they work properly with your kernel. Remember that by using a driver with ndiswrapper you will have to recompile ndiswrapper everytime you upgrade/update your kernel. it seems like there is no other option left unless you can find a driver that does not use wl.


I am kinda lost now because you uninstalled the driver and installed back the kernel. so i don't know which driver are u using now:

1.run this 1 LINE COMMAND please and post the output.
```
sudo lspci | grep "Ethernet controller:" | cut -d " " -f 1 |tee > log2.txt; less "" > log1.txt; cat log2.txt | while read line; do sudo lspci -vvvs $line |tee >> log1.txt; driver=$(sudo lspci -vvvs $line | grep "Kernel driver in use:" |cut -d " " -f 5); done ; less log1.txt | grep -e "Kernel modules" -e "Kernel driver in use" -e "Ethernet controller:"  ; rm log1.txt log2.txt

```

2 by running these commands:
> 
sudo ifconfig eth0 down
sudo ifconfig eth1 down
sudo ifconfig eth1 up

are you able to connect to a network with the wifi?

to rest the settings do:
```
sudo ifconfig eth0 up
```

---

### Post by bkratz on 2011-08-29
[COLOR="Black"][QUOTE=fdrake;11197600]A:source :[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218) Post#1.

B:Source [http://wiki.debian.org/wl#Known_Issues](http://wiki.debian.org/wl#Known_Issues)


just wanted to point out that your b43 driver and STA driver will not work, reason being is that you have an ethernet driver supported by ssb/b44. 
[/COLOR]

___________________________________________________________________________


[COLOR="Red"]@fdrake[/COLOR], that is a pretty old link, many users successfully use b43,b44 and ssb at the same time. Perhaps b43 has been improved since 2008. Generally, even if the STA driver blacklists the ssb driver it seems to load anyway. It may be necessary to correct the order of loading (another topic altogether), but generally not even that is required. Many users here use either the b43 or STA with a Broadcom ethernet card depending on which chipset is invelved.
Here is a pretty good post showing which driver works with which chipset.

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by Kallash on 2011-08-30
Hi fdrake, jackjwalt and bkratz,

@jackjwalt: Everything is updated.

@fdrake:
```

$ sudo lspci | grep "Ethernet controller:" | cut -d " " -f 1 |tee > log2.txt; less "" > log1.txt; cat log2.txt | while read line; do sudo lspci -vvvs $line |tee >> log1.txt; driver=$(sudo lspci -vvvs $line | grep "Kernel driver in use:" |cut -d " " -f 5); done ; less log1.txt | grep -e "Kernel modules" -e "Kernel driver in use" -e "Ethernet controller:"  ; rm log1.txt log2.txt
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
    Kernel driver in use: b44
    Kernel modules: b44

```I also did the 3 commands but nothing changed.

I used NDISWrapper to install the driver. It is not working either. Should I do anything else to use it?

---

### Post by fdrake on 2011-08-31
ehhmm it looks like your wireless card is not listed in the PCI bus. ....
sending commands one by one will take quite a while and scrolling the page up and down it's not that great either.
can you please download my attachment and do:
(download/move this script in your Desktop please!)
```

sudo chmod +x ~/Desktop/net.sh
sudo bash ~/Desktop/net.sh

```
so we get everything at once

the script will create a results.txt (text)file/log. please attach this file in your next post. the more informations we get from you the clearer will be to find out the source of the problem.

ps. are you able to connect to open(no encryption/password) wifi-hot spots?)

---

