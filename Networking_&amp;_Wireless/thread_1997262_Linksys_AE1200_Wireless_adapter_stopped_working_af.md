---
title: "Linksys AE1200 Wireless adapter stopped working after running update manager in 12.04"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by TruthIsRelative on 2012-06-04
Here is the problem, I use a Cisco/Linksys AE1200 wireless network  adapter to connect my desktop to a public wifi internet connection. I  use ndiswrapper to use the windows driver and it had been working fine  for me untill I ran the update manager overnight a few days ago. When I  woke up it was asking for the normal computer restart to implement the  changes but after rebooting the computer, the wireless adapter did not  work, the status light on the adapter did not light up even though  ubuntu recognizes it is there and according to ndiswrapper the drivers  are loaded and the hardware is present. 

All information  recommended in the "How to post a Wireless issue (ticket)" thread are as  follows, and the grep command is being a bitch for some unknown reason today so this will be long sorry


**Output from "lspci":**

00:00.0 Host  bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host  Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee  ATI RS480 PCI Bridge
00:12.0 SATA controller: Advanced Micro Devices  [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced  Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller:  Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB  controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3  USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4  USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5  USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB  Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI  SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced  Micro Devices [AMD] nee ATI SB600 IDE
00:14.3 ISA bridge: Advanced  Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI  bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
01:05.0  VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RC410  [Radeon Xpress 200]
02:02.0 Communication controller: Conexant  Systems, Inc. HSF 56k Data/Fax Modem
02:03.0 Multimedia audio  controller: Creative Labs CA0106 Soundblaster
02:05.0 Ethernet  controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev  10)




**Output from "lsusb":**


Bus 001  Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device  001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001:  ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID  1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID  1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID  1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID  13b1:0039 Linksys AE1200 802.11bgn Wireless Adapter [Broadcom BCM43235]
Bus  003 Device 002: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 004  Device 002: ID 1043:8006 iCreate Technologies Corp. Flash Disk 32-256 MB


[B]
Output  from "ifconfig":[/B]



eth0    Link encap:Ethernet  HWaddr  00:19:21:b6:af:7c  
          UP BROADCAST MULTICAST             MTU:1500  Metric:1        
          RX packets:0 errors:0 dropped:0  overruns:0 frame:0
          TX packets:0 errors:0 dropped:0  overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base  address:0xb400 

lo        Link encap:Local Loopback  
           inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128  Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:13232 errors:0 dropped:0 overruns:0 frame:0
          TX  packets:13232 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
          RX bytes:1084624 (1.0 MB)  TX  bytes:1084624 (1.0 MB)



**Output from "iwconfig":**

lo         no wireless extensions.

eth0      no wireless extensions.





```


**Output  from "lsmod":**


Module                          Size       Used by
nls_iso8859_1                12617      1 
nls_cp437                       12751      1 
vfat                               17308      1 
fat                                  55605      1 vfat
uas                               17828       0 
usb_storage                    39646      1 
nls_utf8                         12493      1 
udf                                 84366      1 
crc_itu_t                        12627      1 udf
snd_ca0106                    39279      2 
snd_ac97_codec             106082    1  snd_ca0106
ac97_bus                       12642      1 snd_ac97_codec
snd_pcm                         80845      2 snd_ca0106,snd_ac97_codec
rfcomm                           38139      0 
snd_seq_midi                 13132       0 
snd_rawmidi                    25424      2 snd_ca0106,snd_seq_midi
bnep                               17830      2 
parport_pc                      32114     0 
bluetooth                         158438    10 rfcomm,bnep
ppdev                              12849      0 
snd_seq_midi_event         14475     1 snd_seq_midi
snd_seq                           51567      2 snd_seq_midi,snd_seq_midi_event
snd_timer                        28931      2 snd_pcm,snd_seq
snd_seq_device               14172       3 snd_seq_midi,snd_rawmidi,snd_seq
snd                                 62064      11  snd_ca0106,          
 snd_ac97_codec,snd_pcm,snd_rawj9fe          snd_ca0106,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                       14635       1 snd
snd_page_alloc               14108       2  snd_ca0106,snd_pcm
sp5100_tco                     13495       0 
i2c_piix4                          13093       0 
radeon                           733693      3 
ttm                                  65344       1 radeon
drm_kms_helper              45466       1  radeon
drm                                197692     5  radeon,ttm,drm_kms_helper
i2c_algo_bit                      13199       1 radeon
mac_hid                          13077       0 
shpchp                             32325       0 
ati_agp                           13242        0 
lp                                    17455        0 
parport                           40930        3  parport_pc,ppdev,lp
usbhid                            41906        0 
hid                                  77367        1 usbhid
8139too                           23283       0  
8139cp                            26759       0 
pata_atiixp                        12999       1 


[B]
[IMG]file:///C:/Users/Cathy/AppData/Local/Temp/moz-screenshot-1.png[/IMG]Output from "sudo lshw -C network":
[/B]

*-network                       
     description: Ethernet interface       
     product:  RTL-8139/8139C/8139C+       
     vendor: Realtek Semiconductor Co.,  Ltd.       
     physical id: 5       
     bus info:  pci@0000:02:05.0       
     logical name: eth0      
      version: 10
     serial: 00:19:21:b6:af:7c       
     size:  10Mbit/s       
     capacity: 100Mbit/s       
     width: 32  bits       
     clock: 33MHz       
     capabilities: pm  bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 10  0bt-fd autonegotiation   
     configuration: autonegotiation=on  broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64  link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s  
      resources: irq:20 ioport:b400(size=256) memory:ff5fdc00-ff5fdcff



[IMG]file:///C:/Users/Cathy/AppData/Local/Temp/moz-screenshot.png[/IMG]
**Output from "iwlist scan":**
lo        Interface  doesn't support scanning.

eth0      Interface doesn't support  scanning.




[B]Output from "lsb_release -d":
[/B]
Ubuntu  12.04 LTS


[B]
Output from "uname -mr":[/B]

3.2.0-24-generic-pae  i686




**Output from "sudo /etc/init.d/networking  restart":**

 * Running /etc/init.d/networking restart is  deprecated because it may not enable again some interfaces
 *  Reconfiguring network interfaces...                                  [  OK ] 


``````

**Output from "dmesg":**


[     0.392340] pnp 00:01: [io  0x00c0-0x00df]
[    0.392416] pnp 00:01:  Plug and Play ACPI device, IDs PNP0200 (active)
[    0.392444] pnp  00:02: [io  0x0070-0x0071]
[    0.392466] pnp 00:02: [irq 8]
[     0.392536] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[     0.392557] pnp 00:03: [io  0x0061]
[    0.392633] pnp 00:03: Plug and  Play ACPI device, IDs PNP0800 (active)
[    0.392656] pnp 00:04:  [io  0x00f0-0x00ff]
[    0.392667] pnp 00:04: [irq 13]
[     0.392738] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[     0.394957] pnp 00:05: [io  0x0010-0x001f]
[    0.394964] pnp 00:05:  [io  0x0022-0x003f]
[    0.394969] pnp 00:05: [io  0x0062-0x0063]
[     0.394974] pnp 00:05: [io  0x0065-0x006f]
[    0.394978] pnp 00:05:  [io  0x0072-0x007f]
[    0.394983] pnp 00:05: [io  0x0080]
[     0.394987] pnp 00:05: [io  0x0084-0x0086]
[    0.394992] pnp 00:05:  [io  0x0088]
[    0.394997] pnp 00:05: [io  0x008c-0x008e]
[     0.395002] pnp 00:05: [io  0x0090-0x009f]
[    0.395007] pnp 00:05:  [io  0x00a2-0x00bf]
[    0.395011] pnp 00:05: [io  0x00b1]
[     0.395016] pnp 00:05: [io  0x00e0-0x00ef]
[    0.395021] pnp 00:05:  [io  0x04d0-0x04d1]
[    0.395026] pnp 00:05: [io  0x040b]
[     0.395030] pnp 00:05: [io  0x04d6]
[    0.395035] pnp 00:05: [io   0x0c00-0x0c01]
[    0.395039] pnp 00:05: [io  0x0c14]
[     0.395044] pnp 00:05: [io  0x0c50-0x0c51]
[    0.395049] pnp 00:05:  [io  0x0c52]
[    0.395053] pnp 00:05: [io  0x0c6c]
[    0.395058]  pnp 00:05: [io  0x0c6f]
[    0.395062] pnp 00:05: [io   0x0cd0-0x0cd1]
[    0.395067] pnp 00:05: [io  0x0cd2-0x0cd3]
[     0.395073] pnp 00:05: [io  0x0cd4-0x0cd5]
[    0.395079] pnp 00:05:  [io  0x0cd6-0x0cd7]
[    0.395084] pnp 00:05: [io  0x0cd8-0x0cdf]
[     0.395089] pnp 00:05: [io  0x0800-0x089f]
[    0.395095] pnp 00:05:  [io  0x0b10-0x0b1f]
[    0.395102] pnp 00:05: [io   0x0000-0xffffffffffffffff disabled]
[    0.395108] pnp 00:05: [io   0x0900-0x090f]
[    0.395113] pnp 00:05: [io  0x0910-0x091f]
[     0.395117] pnp 00:05: [io  0xfe00-0xfefe]
[    0.395123] pnp 00:05:  [mem 0xffb80000-0xffbfffff]
[    0.395128] pnp 00:05: [mem  0xfff80000-0xffffffff]
[    0.395322] system 00:05: [io   0x04d0-0x04d1] has been reserved
[    0.395334] system 00:05: [io   0x040b] has been reserved
[    0.395340] system 00:05: [io  0x04d6]  has been reserved
[    0.395346] system 00:05: [io  0x0c00-0x0c01]  has been reserved
[    0.395352] system 00:05: [io  0x0c14] has been  reserved
[    0.395358] system 00:05: [io  0x0c50-0x0c51] has been  reserved
[    0.395365] system 00:05: [io  0x0c52] has been reserved
[     0.395371] system 00:05: [io  0x0c6c] has been reserved
[     0.395377] system 00:05: [io  0x0c6f] has been reserved
[    0.395383]  system 00:05: [io  0x0cd0-0x0cd1] has been reserved
[    0.395389]  system 00:05: [io  0x0cd2-0x0cd3] has been reserved
[    0.395396]  system 00:05: [io  0x0cd4-0x0cd5] has been reserved
[    0.395402]  system 00:05: [io  0x0cd6-0x0cd7] has been reserved
[    0.395408]  system 00:05: [io  0x0cd8-0x0cdf] has been reserved
[    0.395414]  system 00:05: [io  0x0800-0x089f] has been reserved
[    0.395421]  system 00:05: [io  0x0b10-0x0b1f] has been reserved
[    0.395427]  system 00:05: [io  0x0900-0x090f] has been reserved
[    0.395433]  system 00:05: [io  0x0910-0x091f] has been reserved
[    0.395440]  system 00:05: [io  0xfe00-0xfefe] has been reserved
[    0.395448]  system 00:05: [mem 0xffb80000-0xffbfffff] has been reserved
[     0.395454] system 00:05: [mem 0xfff80000-0xffffffff] has been reserved
[     0.395463] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[     0.395539] pnp 00:06: [io  0x0060]
[    0.395545] pnp 00:06: [io   0x0064]
[    0.395556] pnp 00:06: [irq 1]
[    0.395650] pnp  00:06: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[     0.396112] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[     0.396118] pnp 00:07: [io  0x0a00-0x0a0f]
[    0.396124] pnp 00:07:  [io  0x0a10-0x0a1f]
[    0.396128] pnp 00:07: [io  0x0a20-0x0a2f]
[     0.396133] pnp 00:07: [io  0x0a30-0x0a3f]
[    0.396265] system  00:07: [io  0x0a00-0x0a0f] has been reserved
[    0.396272] system  00:07: [io  0x0a10-0x0a1f] has been reserved
[    0.396278] system  00:07: [io  0x0a20-0x0a2f] has been reserved
[    0.396285] system  00:07: [io  0x0a30-0x0a3f] has been reserved
[    0.396293] system  00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.396404]  pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.396489] pnp 00:08:  Plug and Play ACPI device, IDs PNP0103 (active)
[    0.396598] pnp  00:09: [mem 0xfec00000-0xfec00fff]
[    0.396605] pnp 00:09: [mem  0xfee00000-0xfee00fff]
[    0.396716] system 00:09: [mem  0xfec00000-0xfec00fff] could not be reserved
[    0.396724] system  00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.396732]  system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[     0.396880] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.397013]  system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[     0.397026] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[     0.397491] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.397497] pnp  00:0b: [mem 0x000c0000-0x000cffff]
[    0.397503] pnp 00:0b: [mem  0x000e0000-0x000fffff]
[    0.397508] pnp 00:0b: [mem  0x00100000-0x6fffffff]
[    0.397521] pnp 00:0b: [mem  0x00000000-0xffffffffffffffff disabled]
[    0.397540] pnp 00:0b:  disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0  BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.397555] pnp 00:0b:  disabling [mem 0x000c0000-0x000cffff] because it overlaps 0000:00:00.0  BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.397567] pnp 00:0b:  disabling [mem 0x000e0000-0x000fffff] because it overlaps 0000:00:00.0  BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.397575] pnp 00:0b:  disabling [mem 0x00100000-0x6fffffff] because it overlaps 0000:00:00.0  BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.397712] system 00:0b:  Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.397968] pnp:  PnP ACPI: found 12 devices
[    0.397973] ACPI: ACPI bus type pnp  unregistered
[    0.397982] PnPBIOS: Disabled by ACPI PNP
[     0.437199] PCI: max bus depth: 1 pci_try_num: 2
[    0.437229] pci  0000:00:01.0: PCI bridge to [bus 01-01]
[    0.437236] pci  0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.437246] pci  0000:00:01.0:   bridge window [mem 0xff400000-0xff4fffff]
[     0.437254] pci 0000:00:01.0:   bridge window [mem 0xbff00000-0xdfefffff  pref]
[    0.437264] pci 0000:00:14.4: PCI bridge to [bus 02-02]
[     0.437272] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[     0.437283] pci 0000:00:14.4:   bridge window [mem 0xff500000-0xff5fffff]
[     0.437320] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[     0.437326] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[     0.437332] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[     0.437337] pci_bus 0000:01: resource 1 [mem 0xff400000-0xff4fffff]
[     0.437343] pci_bus 0000:01: resource 2 [mem 0xbff00000-0xdfefffff pref]
[     0.437349] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[     0.437355] pci_bus 0000:02: resource 1 [mem 0xff500000-0xff5fffff]
[     0.437360] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[     0.437365] pci_bus 0000:02: resource 5 [mem 0x00000000-0xfffffffff]
[     0.437454] NET: Registered protocol family 2
[    0.437615] IP route  cache hash table entries: 32768 (order: 5, 131072 bytes)
[     0.438150] TCP established hash table entries: 131072 (order: 8, 1048576  bytes)
[    0.439032] TCP bind hash table entries: 65536 (order: 7,  524288 bytes)
[    0.439496] TCP: Hash tables configured (established  131072 bind 65536)
[    0.439502] TCP reno registered
[     0.439509] UDP hash table entries: 512 (order: 2, 16384 bytes)
[     0.439528] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[     0.439697] NET: Registered protocol family 1
[    0.439723] pci  0000:00:00.0: MSI quirk detected; MSI disabled
[    0.439736] pci  0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[     0.439781] pci 0000:00:13.0: PCI INT A -> GSI 16 (level, low) ->  IRQ 16
[    0.552084] pci 0000:00:13.0: PCI INT A disabled
[     0.552136] pci 0000:00:13.1: PCI INT B -> GSI 17 (level, low) ->  IRQ 17
[    0.632082] pci 0000:00:13.1: PCI INT B disabled
[     0.632160] pci 0000:00:13.2: PCI INT C -> GSI 18 (level, low) ->  IRQ 18
[    0.681697] Freeing initrd memory: 13796k freed
[     0.712082] pci 0000:00:13.2: PCI INT C disabled
[    0.712117] pci  0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[     0.792033] pci 0000:00:13.3: PCI INT B disabled
[    0.792048] pci  0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[     0.872034] pci 0000:00:13.4: PCI INT C disabled
[    0.872072] pci  0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[     0.872097] pci 0000:00:13.5: PCI INT D disabled
[    0.872122] pci  0000:01:05.0: Boot video device
[    0.872138] PCI: CLS 64 bytes,  default 64
[    0.872837] audit: initializing netlink socket  (disabled)
[    0.872860] type=2000 audit(1338793053.868:1):  initialized
[    0.905338] highmem bounce pool size: 64 pages
[     0.905349] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[     0.915960] VFS: Disk quotas dquot_6.5.2
[    0.916093] Dquot-cache  hash table entries: 1024 (order 0, 4096 bytes)
[    0.917038] fuse  init (API version 7.17)
[    0.917212] msgmni has been set to 1718
[     0.917901] Block layer SCSI generic (bsg) driver version 0.4 loaded  (major 253)
[    0.917954] io scheduler noop registered
[     0.917960] io scheduler deadline registered
[    0.917975] io  scheduler cfq registered (default)
[    0.918182] pci_hotplug: PCI  Hot Plug PCI Core version: 0.5
[    0.918226] pciehp: PCI Express Hot  Plug Controller Driver version: 0.4
[    0.918486] input: Power  Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[     0.918496] ACPI: Power Button [PWRB]
[    0.918577] input: Power  Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[     0.918583] ACPI: Power Button [PWRF]
[    0.922120] ERST: Table is not  found!
[    0.922124] GHES: HEST is not enabled!
[    0.922183]  isapnp: Scanning for PnP cards...
[    0.922269] Serial: 8250/16550  driver, 32 ports, IRQ sharing enabled
[    1.276516] isapnp: No Plug  & Play device found
[    1.332672] Linux agpgart interface v0.103
[     1.335476] brd: module loaded
[    1.336906] loop: module loaded
[     1.337111] ahci 0000:00:12.0: version 3.0
[    1.337127] ahci  0000:00:12.0: enabling device (0005 -> 0007)
[    1.337151] ahci  0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[     1.337190] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing  32bit
[    1.337349] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4  ports 3 Gbps 0xf impl SATA mode
[    1.337355] ahci 0000:00:12.0:  flags: ncq sntf ilck led clo pmp pio slum part ccc 
[    1.337363]  ahci 0000:00:12.0: setting latency timer to 64
[    1.338749] scsi0 :  ahci
[    1.338933] scsi1 : ahci
[    1.339088] scsi2 : ahci
[     1.339239] scsi3 : ahci
[    1.339442] ata1: SATA max UDMA/133 abar  m1024@0xfec01000 port 0xfec01100 irq 22
[    1.339448] ata2: SATA max  UDMA/133 abar m1024@0xfec01000 port 0xfec01180 irq 22
[    1.339453]  ata3: SATA max UDMA/133 abar m1024@0xfec01000 port 0xfec01200 irq 22
[     1.339458] ata4: SATA max UDMA/133 abar m1024@0xfec01000 port 0xfec01280  irq 22
[    1.339852] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16  (level, low) -> IRQ 16
[    1.340546] Fixed MDIO Bus: probed
[     1.340585] tun: Universal TUN/TAP device driver, 1.6
[    1.340588]  tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[     1.340692] PPP generic driver version 2.4.2
[    1.340886] ehci_hcd:  USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.340912]  ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[     1.340935] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    1.341018]  ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[     1.341062] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze  workaround
[    1.341084] ehci_hcd 0000:00:13.5: debug port 1
[     1.341115] ehci_hcd 0000:00:13.5: irq 19, io mem 0xff6ff800
[     1.352035] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[     1.352303] hub 1-0:1.0: USB hub found
[    1.352311] hub 1-0:1.0: 10  ports detected
[    1.352457] ohci_hcd: USB 1.1 'Open' Host  Controller (OHCI) Driver
[    1.352479] ohci_hcd 0000:00:13.0: PCI  INT A -> GSI 16 (level, low) -> IRQ 16
[    1.352498] ohci_hcd  0000:00:13.0: OHCI Host Controller
[    1.352589] ohci_hcd  0000:00:13.0: new USB bus registered, assigned bus number 2
[     1.352628] ohci_hcd 0000:00:13.0: irq 16, io mem 0xff6fe000
[     1.412252] hub 2-0:1.0: USB hub found
[    1.412262] hub 2-0:1.0: 2  ports detected
[    1.412361] ohci_hcd 0000:00:13.1: PCI INT B ->  GSI 17 (level, low) -> IRQ 17
[    1.412379] ohci_hcd  0000:00:13.1: OHCI Host Controller
[    1.412472] ohci_hcd  0000:00:13.1: new USB bus registered, assigned bus number 3
[     1.412510] ohci_hcd 0000:00:13.1: irq 17, io mem 0xff6fd000
[     1.472226] hub 3-0:1.0: USB hub found
[    1.472236] hub 3-0:1.0: 2  ports detected
[    1.472334] ohci_hcd 0000:00:13.2: PCI INT C ->  GSI 18 (level, low) -> IRQ 18
[    1.472352] ohci_hcd  0000:00:13.2: OHCI Host Controller
[    1.472445] ohci_hcd  0000:00:13.2: new USB bus registered, assigned bus number 4
[     1.472482] ohci_hcd 0000:00:13.2: irq 18, io mem 0xff6fc000
[     1.532241] hub 4-0:1.0: USB hub found
[    1.532251] hub 4-0:1.0: 2  ports detected
[    1.532345] ohci_hcd 0000:00:13.3: PCI INT B ->  GSI 17 (level, low) -> IRQ 17
[    1.532364] ohci_hcd  0000:00:13.3: OHCI Host Controller
[    1.532457] ohci_hcd  0000:00:13.3: new USB bus registered, assigned bus number 5
[     1.532481] ohci_hcd 0000:00:13.3: irq 17, io mem 0xff6fb000
[     1.592224] hub 5-0:1.0: USB hub found
[    1.592234] hub 5-0:1.0: 2  ports detected
[    1.592335] ohci_hcd 0000:00:13.4: PCI INT C ->  GSI 18 (level, low) -> IRQ 18
[    1.592353] ohci_hcd  0000:00:13.4: OHCI Host Controller
[    1.592436] ohci_hcd  0000:00:13.4: new USB bus registered, assigned bus number 6
[     1.592460] ohci_hcd 0000:00:13.4: irq 18, io mem 0xff6fa000
[     1.652221] hub 6-0:1.0: USB hub found
[    1.652231] hub 6-0:1.0: 2  ports detected
[    1.652330] uhci_hcd: USB Universal Host Controller  Interface driver
[    1.652436] usbcore: registered new interface  driver libusual
[    1.652505] i8042: PNP: PS/2 Controller  [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.652508] i8042: PNP: PS/2  appears to have AUX port disabled, if this is incorrect please boot with  i8042.nopnp
[    1.652714] serio: i8042 KBD port at 0x60,0x64 irq 1
[     1.652909] mousedev: PS/2 mouse device common for all mice
[     1.653171] rtc_cmos 00:02: RTC can wake from S4
[    1.653336]  rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.653376]  rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[     1.653466] device-mapper: uevent: version 1.0.3
[    1.653593]  device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised:  [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.653651] EISA: Probing bus 0 at eisa.0
[     1.653706] EISA: Detected 0 cards.
[    1.653720] cpufreq-nforce2: No  nForce2 chipset.
[    1.653725] cpuidle: using governor ladder
[     1.653727] cpuidle: using governor menu
[    1.653730] EFI Variables  Facility v0.08 2004-May-17
[    1.654143] TCP cubic registered
[     1.654339] NET: Registered protocol family 10
[    1.655283] NET:  Registered protocol family 17
[    1.655307] Registering the  dns_resolver key type
[    1.655361] Using IPI No-Shortcut mode
[     1.655566] PM: Hibernation image not present or could not be loaded.
[     1.655590] registered taskstats version 1
[    1.658376] ata3: SATA  link down (SStatus 0 SControl 300)
[    1.660106] ata4: SATA link  down (SStatus 0 SControl 300)
[    1.660170] ata2: SATA link down  (SStatus 0 SControl 300)
[    1.670558]   Magic number: 0:376:973
[     1.670690] rtc_cmos 00:02: setting system clock to 2012-06-04 06:57:35  UTC (1338793055)
[    1.670725] BIOS EDD facility v0.16 2004-Jun-25, 0  devices found
[    1.670728] EDD information not available.
[     1.673103] input: AT Translated Set 2 keyboard as  /devices/platform/i8042/serio0/input/input2
[    1.720032] usb 1-5:  new high-speed USB device number 3 using ehci_hcd
[    1.828040]  ata1: softreset failed (device not ready)
[    1.828048] ata1:  applying PMP SRST workaround and retrying
[    1.872043] Refined TSC  clocksource calibration: 2992.499 MHz.
[    1.872053] Switching to  clocksource tsc
[    1.988016] usb 3-1: new low-speed USB device  number 2 using ohci_hcd
[    2.000031] ata1: SATA link up 3.0 Gbps  (SStatus 123 SControl 300)
[    2.000596] ata1.00: ATA-7: WDC  WD2500JS-60NCB1, 10.02E02, max UDMA/100
[    2.000601] ata1.00:  488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[     2.000606] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[     2.001210] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[     2.001215] ata1.00: configured for UDMA/100
[    2.001425] scsi  0:0:0:0: Direct-Access     ATA      WDC WD2500JS-60N 10.0 PQ: 0 ANSI: 5
[     2.001644] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250  GB/232 GiB)
[    2.001727] sd 0:0:0:0: Attached scsi generic sg0 type  0
[    2.001781] sd 0:0:0:0: [sda] Write Protect is off
[     2.001789] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.001846] sd  0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't  support DPO or FUA
[    2.036390]  sda: sda1 sda2 < sda5 sda6 >
[     2.037052] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.037163]  Freeing unused kernel memory: 740k freed
[    2.037944] Write  protecting the kernel text: 5828k
[    2.037973] Write protecting the  kernel read-only data: 2376k
[    2.037977] NX-protecting the kernel  data: 4412k
[    2.065037] udevd[92]: starting version 175
[     2.241895] scsi4 : pata_atiixp
[    2.245624] scsi5 : pata_atiixp
[     2.246411] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22,  2004)
[    2.246502] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10)  is not an 8139C+ compatible chip, use 8139too
[    2.247410] 8139too:  8139too Fast Ethernet driver 0.9.28
[    2.247482] 8139too  0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[     2.248306] ata5: PATA max UDMA/100 cmd 0xe800 ctl 0xe400 bmdma 0xd800 irq  16
[    2.248343] ata6: PATA max UDMA/100 cmd 0xe000 ctl 0xdc00  bmdma 0xd808 irq 16
[    2.250349] 8139too 0000:02:05.0: eth0:  RealTek RTL8139 at 0xb400, 00:19:21:b6:af:7c, IRQ 20
[    2.412545]  ata5.00: ATAPI: TSSTcorpCD/DVDW TS-H652M, 0414, max UDMA/33
[     2.428504] ata5.00: configured for UDMA/33
[    2.429418] scsi  4:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H652M 0414 PQ: 0 ANSI: 5
[     2.432770] sr0: scsi3-mmc drive: 94x/94x writer dvd-ram cd/rw xa/form2  cdda tray
[    2.432775] cdrom: Uniform CD-ROM driver Revision: 3.20
[     2.433037] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.433296] sr  4:0:0:0: Attached scsi generic sg1 type 5
[    2.440299] input:  Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as  /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input3
[     2.441799] generic-usb 0003:045E:0053.0001: input,hidraw0: USB HID v1.10  Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on  usb-0000:00:13.1-1/input0
[    2.441844] usbcore: registered new  interface driver usbhid
[    2.441849] usbhid: USB HID core driver
[     2.549046] EXT4-fs (sda6): INFO: recovery required on readonly  filesystem
[    2.549052] EXT4-fs (sda6): write access will be  enabled during recovery
[    2.583305] EXT4-fs (sda6): recovery  complete
[    2.583485] EXT4-fs (sda6): mounted filesystem with  ordered data mode. Opts: (null)
[   13.415027] ADDRCONF(NETDEV_UP):  eth0: link is not ready
[   13.448347] udevd[295]: starting version  175
[   13.497916] Adding 2095100k swap on /dev/sda5.  Priority:-1  extents:1 across:2095100k 
[   13.510945] lp: driver loaded but no  devices found
[   13.611091] shpchp: Standard Hot Plug PCI Controller  Driver version: 0.4
[   13.708578] EXT4-fs (sda6): re-mounted. Opts:  errors=remount-ro
[   13.723517] [drm] Initialized drm 1.1.0  20060810
[   13.852621] [drm] radeon defaulting to kernel  modesetting.
[   13.852630] [drm] radeon kernel modesetting enabled.
[    13.852749] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low)  -> IRQ 17
[   13.854455] [drm] initializing kernel modesetting  (RS400 0x1002:0x5A61 0x103C:0x2A4F).
[   13.854503] [drm] register  mmio base: 0xFF4F0000
[   13.854508] [drm] register mmio size: 65536
[    13.857421] [drm] Generation 2 PCI interface, using max accessible  memory
[   13.857434] radeon 0000:01:05.0: VRAM: 256M  0x0000000070000000 - 0x000000007FFFFFFF (256M used)
[   13.857441]  radeon 0000:01:05.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[    13.857462] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    13.857468] [drm] Driver supports precise vblank timestamp query.
[    13.857487] [drm] radeon: irq initialized.
[   13.860083] [drm]  Detected VRAM RAM=256M, BAR=256M
[   13.860090] [drm] RAM width  128bits DDR
[   13.863625] [TTM] Zone  kernel: Available graphics  memory: 440372 kiB.
[   13.863631] [TTM] Zone highmem: Available  graphics memory: 901016 kiB.
[   13.863636] [TTM] Initializing pool  allocator.
[   13.863687] [drm] radeon: 256M of VRAM memory ready
[    13.863692] [drm] radeon: 512M of GTT memory ready.
[   13.863728]  [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.887102]  [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   13.897195]  [drm] PCIE GART of 512M enabled (table at 0x0000000032E80000).
[    13.901641] radeon 0000:01:05.0: WB enabled
[   13.901742] [drm]  Loading R300 Microcode
[   13.968038] piix4_smbus 0000:00:14.0: SMBus  Host Controller at 0xb00, revision 0
[   13.978290] SP5100 TCO  timer: SP5100 TCO WatchDog Timer Driver v0.01
[   13.978562] SP5100  TCO timer: mmio address 0xfec000f0 already in use
[   14.052890]  type=1400 audit(1338793067.880:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient" pid=483  comm="apparmor_parser"
[   14.053847] type=1400  audit(1338793067.880:3): apparmor="STATUS" operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=483  comm="apparmor_parser"
[   14.054614] type=1400  audit(1338793067.880:4): apparmor="STATUS" operation="profile_load"  name="/usr/lib/connman/scripts/dhclient-script" pid=483  comm="apparmor_parser"
[   14.327383] Bluetooth: Core ver 2.16
[    14.327422] NET: Registered protocol family 31
[   14.327427]  Bluetooth: HCI device and connection manager initialized
[    14.327432] Bluetooth: HCI socket layer initialized
[   14.327437]  Bluetooth: L2CAP socket layer initialized
[   14.327449] Bluetooth:  SCO socket layer initialized
[   14.349317] ppdev: user-space  parallel port driver
[   14.369776] Bluetooth: BNEP (Ethernet  Emulation) ver 1.3
[   14.369784] Bluetooth: BNEP filters: protocol  multicast
[   14.533817] Bluetooth: RFCOMM TTY layer initialized
[    14.533837] Bluetooth: RFCOMM socket layer initialized
[   14.533843]  Bluetooth: RFCOMM ver 1.11
[   14.560426] type=1400  audit(1338793068.388:5): apparmor="STATUS" operation="profile_load"  name="/usr/lib/cups/backend/cups-pdf" pid=651 comm="apparmor_parser"
[    14.573068] type=1400 audit(1338793068.400:6): apparmor="STATUS"  operation="profile_load" name="/usr/sbin/cupsd" pid=651  comm="apparmor_parser"
[   14.631397] [drm] radeon: ring at  0x0000000080001000
[   14.631423] [drm] ring test succeeded in 1  usecs
[   14.631764] [drm] radeon: ib pool ready.
[   14.631896]  [drm] ib test succeeded in 0 usecs
[   14.636370]  [drm:radeon_add_legacy_connector] *ERROR* DVI: Failed to assign ddc bus!  Check dmesg for i2c errors.
[   14.636587] [drm] Radeon Display  Connectors
[   14.636593] [drm] Connector 0:
[   14.636597]  [drm]   VGA
[   14.636602] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68  0x68 0x68
[   14.636606] [drm]   Encoders:
[   14.636610]  [drm]     CRT1: INTERNAL_DAC2
[   14.636614] [drm] Connector 1:
[    14.636617] [drm]   DVI-D
[   14.636620] [drm]   HPD2
[    14.636624] [drm]   DDC: no ddc bus - possible BIOS bug - please report  to [EMAIL="xorg-driver-ati@lists.x.org"]xorg-driver-ati@lists.x.org[/EMAIL]
[   14.636628] [drm]   Encoders:
[    14.636632] [drm]     DFP2: INTERNAL_DVO1
[   14.636636] [drm]  Connector 2:
[   14.636639] [drm]   S-video
[   14.636642] [drm]    Encoders:
[   14.636646] [drm]     TV1: INTERNAL_DAC2
[    14.671977] init: failsafe main process (631) killed by TERM signal
[    14.676382] snd_ca0106 0000:02:03.0: PCI INT A -> GSI 23 (level, low)  -> IRQ 23
[   14.676443] snd-ca0106: Model 100a Rev 00000000  Serial 100a1102
[   14.957602] type=1400 audit(1338793068.784:7):  apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient"  pid=745 comm="apparmor_parser"
[   14.960939] 8139too 0000:02:05.0:  eth0: link down
[   14.964480] ADDRCONF(NETDEV_UP): eth0: link is not  ready
[   14.965516] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    14.976849] type=1400 audit(1338793068.804:8): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=744  comm="apparmor_parser"
[   14.979451] type=1400  audit(1338793068.804:9): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=745  comm="apparmor_parser"
[   14.980106] type=1400  audit(1338793068.808:10): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=745  comm="apparmor_parser"
[   15.011174] type=1400  audit(1338793068.836:11): apparmor="STATUS" operation="profile_load"  name="/usr/lib/telepathy/mission-control-5" pid=755  comm="apparmor_parser"
[   15.062228] [drm] fb mappable at 0xC0040000
[    15.062234] [drm] vram apper at 0xC0000000
[   15.062238] [drm] size  5242880
[   15.062241] [drm] fb depth is 24
[   15.062245]  [drm]    pitch is 5120
[   15.066715] fbcon: radeondrmfb (fb0) is  primary device
[   15.138737] Console: switching to colour frame  buffer device 160x64
[   15.145620] fb0: radeondrmfb frame buffer  device
[   15.145624] drm: registered panic notifier
[    15.145636] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on  minor 0
[   16.430776] init: plymouth-stop pre-start process (1034)  terminated with status 1
[   30.094540] UDF-fs: Partition marked  readonly; forcing readonly mount
[   30.114709] UDF-fs: INFO Mounting  volume '10/3/2011', timestamp 2011/10/03 19:44 (1e98)
[  121.142078]  usb 1-5: USB disconnect, device number 3
[  122.684024] usb 1-6: new  high-speed USB device number 4 using ehci_hcd
[  310.117837] usb  1-6: USB disconnect, device number 4
[  311.476026] usb 1-5: new  high-speed USB device number 5 using ehci_hcd
[  317.197517] usb 1-5:  USB disconnect, device number 5
[  318.240026] usb 1-6: new  high-speed USB device number 6 using ehci_hcd
[  319.249788] usb 1-6:  USB disconnect, device number 6
[  320.228024] usb 1-6: new  high-speed USB device number 7 using ehci_hcd
[  444.729307] usb 1-6:  USB disconnect, device number 7
[  446.120024] usb 1-6: new  high-speed USB device number 8 using ehci_hcd
[ 2114.639291] usb 1-6:  USB disconnect, device number 8
[ 2116.428024] usb 1-5: new  high-speed USB device number 9 using ehci_hcd
[48854.696021] usb 4-2:  new full-speed USB device number 2 using ohci_hcd
[48854.894678]  Initializing USB Mass Storage driver...
[48854.894951] scsi6 :  usb-storage 4-2:1.0
[48854.895126] usbcore: registered new interface  driver usb-storage
[48854.895131] USB Mass Storage support  registered.
[48854.897555] usbcore: registered new interface driver  uas
[48855.899097] scsi 6:0:0:0: Direct-Access     USB 2.0  USB Flash  Driver %z!Y PQ: 0 ANSI: 2
[48855.900766] sd 6:0:0:0: Attached scsi  generic sg2 type 0
[48855.920096] sd 6:0:0:0: [sdb] 254720 512-byte  logical blocks: (130 MB/124 MiB)
[48855.929085] sd 6:0:0:0: [sdb]  Write Protect is off
[48855.929092] sd 6:0:0:0: [sdb] Mode Sense: 0b  00 00 08
[48855.935069] sd 6:0:0:0: [sdb] No Caching mode page  present
[48855.935074] sd 6:0:0:0: [sdb] Assuming drive cache: write  through
[48855.971075] sd 6:0:0:0: [sdb] No Caching mode page present
[48855.971082]  sd 6:0:0:0: [sdb] Assuming drive cache: write through
[48855.981158]   sdb: sdb1
[48856.015075] sd 6:0:0:0: [sdb] No Caching mode page  present
[48856.015083] sd 6:0:0:0: [sdb] Assuming drive cache: write  through
[48856.015088] sd 6:0:0:0: [sdb] Attached SCSI removable disk
```

---

### Post by TruthIsRelative on 2012-06-06
scratch this post

---

