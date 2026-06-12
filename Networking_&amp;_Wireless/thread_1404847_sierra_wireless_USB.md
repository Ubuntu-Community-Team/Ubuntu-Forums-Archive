---
title: "sierra wireless USB"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by kiwiblack123 on 2010-02-11
I am dual booting with ubuntu and visa. I am using Sierra Wireless USB308 modem which is recognised in windows but ubuntu mounts it as /media/disk.
I cannot get network manager to recognise it and it is recognised when I lsusb
Bus 002 Device 007: ID 1199:68a3 Sierra Wireless, Inc. 
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 04e8:6601 Samsung Electronics Co., Ltd Z100 Mobile Phone
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 03f0:4511 Hewlett-Packard Photosmart 2600
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 004 Device 002: ID 04ca:0027 Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
when I dmesg
[  392.889508] sd 7:0:0:0: [sdg] Attached SCSI removable disk
[  392.889590] sd 7:0:0:0: Attached scsi generic sg7 type 0
[  429.624017] usb 6-1: new full speed USB device using uhci_hcd and address 2
[  429.843971] usb 6-1: configuration #1 chosen from 1 choice
[  429.895028] cdc_acm 6-1:1.0: ttyACM0: USB ACM device
[  429.898131] usbcore: registered new interface driver cdc_acm
[  429.898135] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[  431.094040] usb 2-2: USB disconnect, address 4
[  431.142649] scsi 7:0:0:0: rejecting I/O to dead device
[  435.103622] PPP BSD Compression module registered
[  435.118477] PPP Deflate Compression module registered
[  554.464016] usb 2-2: new high speed USB device using ehci_hcd and address 6
[  554.597641] usb 2-2: config 1 has an invalid interface number: 9 but max is 0
[  554.597645] usb 2-2: config 1 has no interface number 0
[  554.599480] usb 2-2: configuration #1 chosen from 1 choice
[  554.603557] usb-storage: probe of 2-2:1.9 failed with error -5
[  555.376433] usb 2-2: USB disconnect, address 6
[  555.744014] usb 2-2: new high speed USB device using ehci_hcd and address 7
[  555.877422] usb 2-2: config 1 has an invalid interface number: 9 but max is 5
[  555.877426] usb 2-2: config 1 has an invalid interface number: 7 but max is 5
[  555.877428] usb 2-2: config 1 has no interface number 2
[  555.877431] usb 2-2: config 1 has no interface number 5
[  555.879006] usb 2-2: configuration #1 chosen from 1 choice
[  555.882991] scsi9 : SCSI emulation for USB Mass Storage devices
[  555.883065] usb-storage: device found at 7
[  555.883068] usb-storage: waiting for device to settle before scanning
[  560.880715] usb-storage: device scan complete
[  560.881330] scsi 9:0:0:0: Direct-Access     SWI      SD Card          2.31 PQ: 0 ANSI: 2
[  560.882681] sd 9:0:0:0: [sdg] 1930240 512-byte hardware sectors: (988 MB/942 MiB)
[  560.883304] sd 9:0:0:0: [sdg] Write Protect is off
[  560.883307] sd 9:0:0:0: [sdg] Mode Sense: 0f 0e 00 00
[  560.883310] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[  560.887683] sd 9:0:0:0: [sdg] 1930240 512-byte hardware sectors: (988 MB/942 MiB)
[  560.888555] sd 9:0:0:0: [sdg] Write Protect is off
[  560.888559] sd 9:0:0:0: [sdg] Mode Sense: 0f 0e 00 00
[  560.888562] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[  560.888568]  sdg: sdg1
[  560.891749] sd 9:0:0:0: [sdg] Attached SCSI removable disk
[  560.891835] sd 9:0:0:0: Attached scsi generic sg7 type 0
[ 1624.072053] usb 6-1: USB disconnect, address 2
[ 1635.456014] usb 6-1: new full speed USB device using uhci_hcd and address 3
[ 1635.671367] usb 6-1: configuration #1 chosen from 1 choice
[ 1635.674200] cdc_acm 6-1:1.0: ttyACM0: USB ACM device
[ 2552.548451] usblp0: removed
i don't want to use windows ,haven't for 5 years.I live in Australia and this modem is from bigpond.
I have no problem using a mobile phone as a modem.
thank you

---

### Post by sharke on 2010-02-12
kiwiblack123
which version of ubuntu are you using.
Cheers
Sharke

---

### Post by kiwiblack123 on 2010-02-12
I am using Ubuntu 9.04.:p
  	 	 	 	 	 	   sudo lshw -C network
   	 	 	 	 	 	  *-network                
        description: Ethernet interface  
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: eth0  
        version: 02  
        serial: 00:24:e8:06:8a:85  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s  
   *-network  
        description: Ethernet interface  
        physical id: 1  
        logical name: pan0  
        serial: 5a:09:33:aa:97:63  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by kiwiblack123 on 2010-02-12
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:06:8a:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:24:e8:06:8a:85  
          inet addr:169.254.6.200  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4253 (4.2 KB)  TX bytes:4253 (4.2 KB)

pan0      Link encap:Ethernet  HWaddr 5a:09:33:aa:97:63  
          inet6 addr: fe80::5809:33ff:feaa:9763/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:23337 (23.3 KB)

pan0:avahi Link encap:Ethernet  HWaddr 5a:09:33:aa:97:63  
          inet addr:169.254.6.185  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.222.100.237  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3557434 (3.5 MB)  TX bytes:336902 (336.9 KB)


 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.


I hope these help and all help is appreciated
thank you:P

---

### Post by sharke on 2010-02-12
with 9.04 your in luck . 9.10 does not support
Why it is showing as amedia device is because it has the window drivers loaded in the device and ubuntu is seeing this as much the same as ausbstick.
In aterminal
sudo apt-get install usb-modeswitch
reebot and should now be seen correctly.
regards
Sharke

---

### Post by kiwiblack123 on 2010-02-12
did what you suggested but still networkmanager will not recognise it .Still no connection to internet.
Here is my /etc/network/interfaces
auto lo
iface lo inet loopback


iface ppp0 inet ppp
provider ppp0



iface eth0 inet dhcp

auto eth0

iface pan0 inet dhcp



auto pan0

thank you:p

---

### Post by sharke on 2010-02-17
Take a look here [http://vk6hgr.echidna.id.au/blog/?p=41](http://vk6hgr.echidna.id.au/blog/?p=41)
although this is not the same modem i think your problem is the same.
cheers
Sharky

---

### Post by kiwiblack123 on 2010-03-20
Thank you for your help, Sharke I have managed to get the Sierra Wireless UAB 308 working in Ubuntu 9.10. It was a combination of looking in forums and your help. It is not as fast as windows but well worth the effort to get it working.

---

### Post by sharke on 2010-03-23
> **kiwiblack123 said:**
> Thank you for your help, Sharke I have managed to get the Sierra Wireless UAB 308 working in Ubuntu 9.10. It was a combination of looking in forums and your help. It is not as fast as windows but well worth the effort to get it working.

Glad to see you have it working.The speed problem may be the dns servers your connection is using .
Cheers
Sharke

---

### Post by steve888 on 2010-04-19
I've installed the Telstra Elite wireless modem (Sierra USB 308 on Ubuntu 9.10, working fine, very fast (updates via Synaptic running over 300 KiB/s).

(note the modem comes with an external aerial, providing excellent network connections).

Settings (in networkmanager):

Number: *99#
Username: (blank)
Password: (blank)

APN: telstra.internet (I tried telstra.datapack, but it didn't work, even though MS Vista seems to select telsta.datapack by default).

Network: (blank)
PIN: xxxx (as per sim card that comes with the modem).

Overall, fast connection, good service coverage. Recommended.

Other settings (IPv4 settings are default).

Steve

update: spoke too soon. rebooted, couldn't connect? Set up another connection profile using APN= telstra.datapack, no PIN, now working ok.

---

