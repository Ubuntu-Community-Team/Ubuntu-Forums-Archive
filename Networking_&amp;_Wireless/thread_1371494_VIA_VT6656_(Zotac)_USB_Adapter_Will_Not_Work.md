---
title: "VIA VT6656 (Zotac) USB Adapter Will Not Work"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by reddogracing on 2010-01-03
Hi, I am trying to get a USB wireless card to work under release 8.04.  The card came with a Zotac motherboard(nForce 630i-ITX) and has the VIA VT6656 chipset.
I installed this driver:
[http://www.viaarena.com/Driver/VT6656_linux_src_v1.20.03_x86.rar](http://www.viaarena.com/Driver/VT6656_linux_src_v1.20.03_x86.rar)
and it seemed to work, the card shows up under Devices in Network Tools and I can configure it under Network Settings.  But it will not connect to the network and I can not see why.
Please share any ideas on what I an try, along with any information required to troube shoot.  Barring that, I would appreciate suggestions for a USB wireless interface that is natively supported under Ubuntu that works without rewritting the whole oerating system :)

Thanks!

---

### Post by Nexer on 2010-01-13
Hey
I'm also having this issue and, i really dont want to fork out for a usb wifi dongle that works:-?

if anyone has found a fix can they please put the link up

---

### Post by reddogracing on 2010-01-14
OK, I read the sticky and got all the information suggested in it.  Maybe someone can suggest where to look based on all this:

caelinux@linux-CAE:~$  lsusb
Bus 002 Device 003: ID 160a:3184
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0dc6:3401 Precision Squared Technology Corp. 
Bus 001 Device 001: ID 0000:0000  

caelinux@linux-CAE:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      802.11-a/b/g  ESSID:""  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=0/255  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vntwpa    no wireless extensions.

caelinux@linux-CAE:~$ lsmod
Module                  Size  Used by
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
ipv6                  312104  18 
acpi_cpufreq           10832  0 
cpufreq_userspace       6180  0 
cpufreq_ondemand       11152  2 
cpufreq_stats           8416  0 
cpufreq_powersave       3200  0 
cpufreq_conservative    10632  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
dock                   12960  0 
video                  23444  0 
output                  5632  1 video
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
af_packet              27272  6 
ac                      8328  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
snd_hda_intel         442328  3 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92296  2 snd_hda_intel,snd_pcm_oss
vntwusb               221476  0 
wmi_acer               11076  0 
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               8858052  34 
serio_raw               9092  0 
snd                    70984  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 10912  0 
i2c_core               28544  1 nvidia
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
evdev                  14976  3 
soundcore              10400  1 snd
psmouse                46236  0 
pcspkr                  4992  0 
ext3                  149264  1 
jbd                    57128  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  3 
pata_amd               16772  0 
usbhid                 35680  0 
hid                    44992  1 usbhid
ahci                   33284  2 
pata_acpi               9856  0 
forcedeth              55564  0 
ata_generic             9988  0 
ehci_hcd               42124  0 
ohci_hcd               28956  0 
libata                176816  4 pata_amd,ahci,pata_acpi,ata_generic
scsi_mod              178744  4 sg,sr_mod,sd_mod,libata
usbcore               170288  5 vntwusb,usbhid,ehci_hcd,ohci_hcd
thermal                19744  0 
processor              40424  2 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4224  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

caelinux@linux-CAE:~$ dmesg
<snip>
[   16.216057] NET: Registered protocol family 16
<snip>
[   16.311365] NET: Registered protocol family 2
[   16.347001] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.348093] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   16.352542] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   16.353106] TCP: Hash tables configured (established 524288 bind 65536)
[   16.353108] TCP reno registered
[   16.363027] checking if image is initramfs... it is
[   16.944662] Freeing initrd memory: 8212k freed
[   16.950898] audit: initializing netlink socket (disabled)
[   16.950917] audit(1263508654.260:1): initialized
[   16.952450] VFS: Disk quotas dquot_6.5.1
[   16.952498] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
<snip>
[   18.462291] usb usb1: configuration #1 chosen from 1 choice
[   18.462309] hub 1-0:1.0: USB hub found
[   18.462317] hub 1-0:1.0: 10 ports detected
<snip>
[   18.681471] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   18.681762] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   18.681769] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
[   18.681773] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   19.199695] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:24:0c:14
[   19.199698] forcedeth 0000:00:0f.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[   19.199733] ahci 0000:00:0e.0: version 3.0
[   19.200027] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   19.200033] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   19.274457] usb 2-8: new high speed USB device using ehci_hcd and address 3
[   19.422455] usb 2-8: configuration #1 chosen from 1 choice
[   19.725766] usb 1-3: new low speed USB device using ohci_hcd and address 2
[   19.945093] usb 1-3: configuration #1 chosen from 1 choice
[   19.954430] usbcore: registered new interface driver hiddev
[   19.962187] input:   SCISSORS Keyboard as /devices/pci0000:00/0000:00:04.0/usb1/1-3/1-3:1.0/input/input1
[   19.985396] input,hidraw0: USB HID v1.00 Keyboard [  SCISSORS Keyboard] on usb-0000:00:04.0-3
[   19.985406] usbcore: registered new interface driver usbhid
[   19.985408] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   20.201050] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   20.201053] ahci 0000:00:0e.0: flags: 64bit sntf led clo pmp pio 
<snip>
[   32.057426] /usr/local/src/VT6656linuxsrcv1.20.03x86/driver/main_usb.c: VIA Networking Wireless LAN USB Driver 1.20.03
[   32.057468] VIA Networking Wireless LAN USB Driver Ver. 1.20.03
[   32.057470] Copyright (c) 2004 VIA Networking Technologies, Inc.
[   32.124461] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   32.124465] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 22
[   32.124935] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   32.157591] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   32.166809] usb 2-8: reset high speed USB device using ehci_hcd and address 3
[   32.304646] usbcore: registered new interface driver vntwusb
[   32.312189] Config_FileOperation file Not exist
[   32.837003] Zone=[2][E][U]!!
[   32.837005] Antenna AUX&MAIN all available!
[   32.978334] lp: driver loaded but no devices found
[   33.057593] Adding 11100872k swap on /dev/sda5.  Priority:-1 extents:1 across:11100872k
[   33.086808] NET: Registered protocol family 17
[   33.603326] EXT3 FS on sda1, internal journal
[   34.728582] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.226237] No dock devices found.
[   35.880656] NET: Registered protocol family 10
[   35.880847] lo: Disabled Privacy Extensions
[   36.963047] ppdev: user-space parallel port driver
[   37.137228] audit(1263508674.546:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5286 profile="/usr/sbin/cupsd" namespace="default"
[   37.943714] Bluetooth: Core ver 2.11
[   37.943820] NET: Registered protocol family 31
[   37.943822] Bluetooth: HCI device and connection manager initialized
[   37.943827] Bluetooth: HCI socket layer initialized
[   37.958397] Bluetooth: L2CAP ver 2.9
[   37.958403] Bluetooth: L2CAP socket layer initialized
[   37.963540] Bluetooth: RFCOMM socket layer initialized
[   37.963557] Bluetooth: RFCOMM TTY layer initialized
[   37.963560] Bluetooth: RFCOMM ver 1.8
[   45.873909] eth1: no IPv6 routers present
[   46.445037] eth0: no IPv6 routers present
[ 8841.970952] eth0: link down.
[ 8901.487003] eth0: link up.
[11394.785246] usb 1-3: USB disconnect, address 2
[11413.198069] usb 1-3: new low speed USB device using ohci_hcd and address 3
[11413.412890] usb 1-3: configuration #1 chosen from 1 choice
[11413.427158] input:   SCISSORS Keyboard as /devices/pci0000:00/0000:00:04.0/usb1/1-3/1-3:1.0/input/input6
[11413.465685] input,hidraw0: USB HID v1.00 Keyboard [  SCISSORS Keyboard] on usb-0000:00:04.0-3

caelinux@linux-CAE:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:01:2e:24:0c:14
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.4 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:12:7b:43:ce:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11-a/b/g

caelinux@linux-CAE:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Resource temporarily unavailable

vntwpa    Interface doesn't support scanning.

caelinux@linux-CAE:~$ lsb_release -d
Description:    Ubuntu 8.04.3 LTS

caelinux@linux-CAE:~$ uname -mr
2.6.24-26-generic x86_64


caelinux@linux-CAE:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5007
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

vntwpa: unknown hardware address type 801
vntwpa: unknown hardware address type 801
Listening on LPF/eth0/00:01:2e:24:0c:14
Sending on   LPF/eth0/00:01:2e:24:0c:14
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 5742
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

vntwpa: unknown hardware address type 801
vntwpa: unknown hardware address type 801
Listening on LPF/eth1/00:12:7b:43:ce:b3
Sending on   LPF/eth1/00:12:7b:43:ce:b3
Sending on   Socket/fallback
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Invalid argument.
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

vntwpa: unknown hardware address type 801
vntwpa: unknown hardware address type 801
Listening on LPF/eth1/00:12:7b:43:ce:b3
Sending on   LPF/eth1/00:12:7b:43:ce:b3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

vntwpa: unknown hardware address type 801
vntwpa: unknown hardware address type 801
Listening on LPF/eth0/00:01:2e:24:0c:14
Sending on   LPF/eth0/00:01:2e:24:0c:14
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.0.4 from 192.168.0.1
DHCPREQUEST of 192.168.0.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.4 from 192.168.0.1
bound to 192.168.0.4 -- renewal in 41711 seconds.

---

### Post by hamx0r on 2010-10-21
i have a solution here.  based on what was said in this thread, ubuntu 9.10 giving the same results as 10.04 (what I'm running).  I also have a Zotac Geforce 9300 mobo with the same VT6656 wireless device.  

I'll save the solution for last and note what I tried here:

[LIST=1]
[*] Compile 3rd party driver from here: [http://vt6656.wordpress.com/download/](http://vt6656.wordpress.com/download/)
[*] Compile/install ubuntu driver here: [https://help.ubuntu.com/community/WifiDocs/Driver/vntwusb](https://help.ubuntu.com/community/WifiDocs/Driver/vntwusb)
[*] Compile VIA's source per instructions here: [http://www.logicsupply.com/blog/2008/01/02/building-the-vt6656-linux-driver-for-ubuntu/](http://www.logicsupply.com/blog/2008/01/02/building-the-vt6656-linux-driver-for-ubuntu/)
[*] Trying several other VIA source code downloads I found
[/LIST]

In all of the above, I had to get the kernel source in order to compile in the driver.  Nothing really worked.  And now the solution: Right after installing ubuntu, i also noticed an eth1 device (eth0 was my wired device).  This ends up being the wifi device, so all of us who are showing an eth1 on this mobo already have drivers installed correctly.  The problem is bringing the interface up correctly ("sudo ifconfig eth1 up" doesn't do the trick).  Here's what got it working for me in a few easy steps:
[LIST=1]
[*]Manually set up a wireless connection with System -> Preferences -> Network Connection
[*]In Wireless tab, make a name for your connection, type in the SSID and put in the right type of security info as appropriate.
[*]edit your /etc/network/interfaces file (sudo vi /etc/network/interfaces) and change "eth0" to "eth1" in the last 2 lines (in VI, "i" puts you in insert mode, after modifying file, hit Esc to exit insert mode, then hit ":wq" to write and quit)
[*]restart networking with "sudo /etc/init.d/networking restart"
[*]give it a minute and eventually the wifi should connect and grab an IP.
[/LIST]

This last part of what to do is described more here:
[http://ubuntuforums.org/showthread.php?t=293493](http://ubuntuforums.org/showthread.php?t=293493)

---

