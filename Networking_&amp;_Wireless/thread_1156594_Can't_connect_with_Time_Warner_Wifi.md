---
title: "Can't connect with Time Warner Wifi"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by TaraDLS on 2009-05-11
I am completely new to Linux and just got a Dell Inspiron Mini 9 with Ubuntu 8.04 installed. My wifi works everywhere else but at home and I called Time Warner Cable and they said that they do not support Linux as an operating system so I can't get connected to their network. I have tried just picking it as an option and typing in the WEP key and also tried just manually typing it in in the "Connect to Other Wireless Networks". So despite paying the insanely high price, I am unable to use wifi for my new laptop. Does anyone have a way around this? I contacted Dell and their solution was for me to download Windows XP and install it as an operating system. I am trying to move as much as possible to open source software but am really frustrated by the fact that I can't use my new computer at home.
If there's some way around it, I would unfortunately need very detailed instructions since I am new to Linux. 

Thanks!

---

### Post by pytheas22 on 2009-05-12
Please try connecting to your home wireless network once or twice.  When it fails, open a terminal from the Applications>Accessories menu, run the following commands and post the output here:
```

lshw -C Network
sudo iwlist scan
uname -rm
dmesg | grep -e wlan -e eth1
iwconfig
```

(If you don't have any Internet connection available on Ubuntu--not even a temporary wired connection--save the output into a text file, then use a USB stick to transfer it to another computer where you can copy and paste into this forum.)

With that information, we should be able to help you get connected.

---

### Post by TaraDLS on 2009-05-12
Thanks for your assistance. When I ran the first line of the command "1shw -C Network", the computer returned back "bash: 1shw: command not found"

I assume this is bad. Any more assistance would be greatly appreciated.

---

### Post by TaraDLS on 2009-05-12
Bear with me...I am new to this! 

I ran all of the commands and this is what I got. I am currently connected to the wifi network at work and have been able to successfully connect in other places, just not at home

tarados@tarados:~$ lshw -c network
bash: lshw: command not found
tarados@tarados:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:1C:01:01:50
                    ESSID:"QBPL_WIRELESS"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:2/5  Signal level:-74 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

tarados@tarados:~$ uname -rm
2.6.24-19-lpia i686
tarados@tarados:~$ dmesg | -e wlan -e ethl
bash: -e: command not found
tarados@tarados:~$ dmesg | -e wlan -e eth1
bash: -e: command not found
tarados@tarados:~$ 
tarados@tarados:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated

---

### Post by pytheas22 on 2009-05-12
Thanks for the information.  I would also need to see it when you're at home, however, because I need to know some information about the network you're trying to connect to.  So when you get home, please first try to connect to your network (this step is important because it should write information to the logs about why the connection failed), and after it fails, run these commands again (just these two will suffice) and post here:
```

sudo iwlist scan
dmesg | **grep** -e wlan -e eth1
```

Please note the 'grep' word in the second command--it looks like you left it off before, which is why you received a 'command not found' message.

---

### Post by TaraDLS on 2009-05-12
Ok, I ran the commands you suggested and also the commands suggested in the how to post a wireless issue thread.

Here's the first:

tarados@tarados:~$ lshw -C network
bash: lshw: command not found
tarados@tarados:~$ sudo iwlist scan
[sudo] password for tarados: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0E:9B:CE:D9:43
                    ESSID:"cbf0"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-77 dBm  Noise level:-3 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1C:DF:89:95:F7
                    ESSID:"gsmv"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-75 dBm  Noise level:-24 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDA50050F204104A00011010440001021041000100103B0001031047001000000000000000011000001CDF8995F71021001242656C6B696E20436F72706F726174696F6E102300114E20576972656C65737320526F7574657210240007332E30312E31301042000E31323830373832333330373237321054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s

tarados@tarados:~$ dmesg | grep -e wlan -e eth1
[   37.743722] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.9
[  330.941882] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  341.040817] eth1: no IPv6 routers present
tarados@tarados:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   

----------------------------

Will post 2nd set of commands in next post

---

### Post by TaraDLS on 2009-05-12
The second set of commands is attached and also posted below:



tarados@tarados:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

tarados@tarados:~$ lsusb
Bus 005 Device 002: ID 064e:a118 Suyin Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 05dc:0080 Lexar Media, Inc. Jumpdrive Secure 64MB
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

tarados@tarados:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:e3:73:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:716072755 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:23:08:73:cd:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:632
          TX packets:46 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9327 (9.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56400 (55.0 KB)  TX bytes:56400 (55.0 KB)

tarados@tarados:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated 

tarados@tarados:~$ lsmod
Module                  Size  Used by
wl                   1077012  0 
parport_pc             36260  0 
ppdev                  10372  0 
parport                37704  2 parport_pc,ppdev
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
dcdbas                  9504  0 
rfcomm                 41232  2 
l2cap                  25472  13 rfcomm
hci_usb                16540  2 
bluetooth              60900  7 rfcomm,l2cap,hci_usb
i915                   32512  3 
acpi_cpufreq           10796  1 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5156  0 
drm                    82324  4 i915
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
snd_seq_midi            9376  0 
snd_seq_oss            35328  0 
snd_seq_dummy           4868  0 
snd_pcm_oss            42144  0 
snd_hda_intel         349712  3 
snd_seq_midi_event      8320  2 snd_seq_midi,snd_seq_oss
snd_rawmidi            25632  1 snd_seq_midi
snd_hwdep              10500  1 snd_hda_intel
snd_pcm                78596  2 snd_pcm_oss,snd_hda_intel
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_mixer_oss          17792  1 snd_pcm_oss
snd_seq                53968  6 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9484  5 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_rawmidi,snd_seq
snd 56868 17 snd_seq_oss,snd_seq_dummy,snd_pcm_oss,snd_hda_intel,snd_rawmidi,snd_hwdep,snd_pcm,snd_mixer_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
joydev                 13120  0 
ieee80211_crypt_tkip    11520  0 
r8169                  33156  0 
ieee80211_crypt         6912  2 wl,ieee80211_crypt_tkip
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               7940  0 
psmouse                40336  0 
fuse                   50324  3 
ahci                   28420  0 
squashfs               49032  0 
unionfs                73168  0 
ehci_hcd               37900  0 
isofs                  36004  0 
zlib_inflate           18176  2 squashfs,isofs


tarados@tarados:~$ dmesg
[ 0.000000] Linux version 2.6.24-19-lpia (root@macbook) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 3 15:25:26 UTC 2008 (Unofficial)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6d0000 - 000000003f6e2000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6e2000 - 000000003f6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6e3000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7fa0
[    0.000000] Entering add_active_range(0, 0, 259792) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259792
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259792
[    0.000000] On node 0 totalpages: 259792
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30179 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7F70 checksum 0
[    0.000000] ACPI: RSDP 000F7F70, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 3F6DC059, 006C (r1 PTLTD       XSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3F6E1D48, 00F4 (r3 INTEL  CALISTGA  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 3F6DCF3E, 4D96 (r1 INTEL  CALISTGA  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 3F6E2FC0, 0040
[    0.000000] ACPI: APIC 3F6E1E3C, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 3F6E1EA4, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 3F6E1EDC, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 3F6E1F18, 0032 (r1 PTLTD  CALISTGA  6040000  PTL        1)
[    0.000000] ACPI: TMOR 3F6E1F4A, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: APIC 3F6E1F70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3F6E1FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3F6DC0C5, 04F6 (r2  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:12 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 7:12 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257763
[    0.000000] Kernel command line: ro root=/dev/sda2 hpet=disabled quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.094 MHz processor.
[    9.239498] Console: colour VGA+ 80x25
[    9.239503] console [tty0] enabled
[    9.239881] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.240668] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.282751] Memory: 1021544k/1039168k available (3046k kernel code, 16904k reserved, 1315k data, 296k init, 121664k highmem)
[    9.282766] virtual kernel memory layout:
[    9.282768]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    9.282770]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.282772]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    9.282775]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    9.282777]       .init : 0xc054b000 - 0xc0595000   ( 296 kB)
[    9.282779]       .data : 0xc03f9831 - 0xc05424bc   (1315 kB)
[    9.282781]       .text : 0xc0100000 - 0xc03f9831   (3046 kB)
[    9.282787] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.282856] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    9.362820] Calibrating delay using timer specific routine.. 3196.48 BogoMIPS (lpj=6392971)
[    9.362866] Security Framework initialized
[    9.362874] SELinux:  Disabled at boot.
[    9.362900] AppArmor: AppArmor initialized
[    9.362908] Failure registering capabilities with primary security module.
[    9.362923] Mount-cache hash table entries: 512
[    9.363110] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    9.363127] monitor/mwait feature present.
[    9.363130] using mwait in idle threads.
[    9.363136] CPU: L1 I cache: 32K, L1 D cache: 24K
[    9.363140] CPU: L2 cache: 512K
[    9.363145] CPU: Physical Processor ID: 0
[    9.363149] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00003940 0040c39d 00000000 00000001 00000000
[    9.363160] Intel machine check architecture supported.
[    9.363165] Intel machine check reporting enabled on CPU#0.
[    9.363173] Compat vDSO mapped to ffffe000.
[    9.363189] Checking 'hlt' instruction... OK.
[    9.379277] SMP alternatives: switching to UP code
[    9.381481] Early unpacking initramfs... done
[    9.579193] ACPI: Core revision 20070126
[    9.579299] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.588268] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    9.588296] SMP alternatives: switching to SMP code
[    9.589040] Booting processor 1/1 eip 3000
[    9.599075] Initializing CPU#1
[    9.678536] Calibrating delay using timer specific routine.. 3192.23 BogoMIPS (lpj=6384465)
[    9.678550] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    9.678562] monitor/mwait feature present.
[    9.678568] CPU: L1 I cache: 32K, L1 D cache: 24K
[    9.678573] CPU: L2 cache: 512K
[    9.678577] CPU: Physical Processor ID: 0
[    9.678581] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00003940 0040c39d 00000000 00000001 00000000
[    9.678592] Intel machine check architecture supported.
[    9.678598] Intel machine check reporting enabled on CPU#1.
[    9.678886] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    9.678927] Total of 2 processors activated (6388.71 BogoMIPS).
[    9.679132] ENABLING IO-APIC IRQs
[    9.679352] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.826623] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    9.846628] Brought up 2 CPUs
[    9.846671] CPU0 attaching sched-domain:
[    9.846675]  domain 0: span 03
[    9.846678]   groups: 01 02
[    9.846685]   domain 1: span 03
[    9.846688]    groups: 03
[    9.846692] CPU1 attaching sched-domain:
[    9.846695]  domain 0: span 03
[    9.846698]   groups: 02 01
[    9.846703]   domain 1: span 03
[    9.846706]    groups: 03
[    9.847096] net_namespace: 64 bytes
[    9.847108] Booting paravirtualized kernel on bare hardware
[    9.848060] Time:  0:44:44  Date: 05/13/09
[    9.848154] NET: Registered protocol family 16
[    9.848505] No dock devices found.
[    9.848687] ACPI: bus type pci registered
[    9.849509] PCI: PCI BIOS revision 3.00 entry at 0xfde5f, last bus=5
[    9.849515] PCI: Using configuration type 1
[    9.849527] Setting up standard PCI resources
[    9.854391] ACPI: EC: Look up EC in DSDT
[    9.856974] ACPI: BIOS _OSI(Linux) query ignored
[    9.856980] ACPI: DMI System Vendor: Dell Inc.
[    9.856983] ACPI: DMI Product Name: Inspiron 910
[    9.856987] ACPI: DMI Product Version: A04
[    9.856989] ACPI: DMI Board Name: CN0J14
[    9.856992] ACPI: DMI BIOS Vendor: Dell Inc.
[    9.856995] ACPI: DMI BIOS Date: 12/29/2008
[    9.856998] ACPI: Please send DMI info above to [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
[    9.857002] ACPI: If "acpi_osi=Linux" works better, please notify [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
[    9.857803] ACPI: Interpreter enabled
[    9.857808] ACPI: (supports S0 S3 S4 S5)
[    9.857835] ACPI: Using IOAPIC for interrupt routing
[    9.858752] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.929740] ACPI: Device [J380] status [0000000a]: functional but not present; setting present
[    9.975448] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    9.975455] ACPI: EC: driver started in interrupt mode
[    9.975541] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.976495] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.976503] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    9.978432] PCI: Transparent bridge - 0000:00:1e.0
[    9.978490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.979055] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.979299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.979527] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    9.979779] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.991998] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    9.992181] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.992359] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.992536] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    9.992714] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    9.992892] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    9.993071] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    9.993248] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    9.993499] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.993564] pnp: PnP ACPI init
[    9.993579] ACPI: bus type pnp registered
[   10.014773] pnp: PnP ACPI: found 11 devices
[   10.014779] ACPI: ACPI bus type pnp unregistered
[   10.015117] SCSI subsystem initialized
[   10.015194] libata version 3.00 loaded.
[   10.015505] usbcore: registered new interface driver usbfs
[   10.015578] usbcore: registered new interface driver hub
[   10.015659] usbcore: registered new device driver usb
[   10.016285] PCI: Using ACPI for IRQ routing
[   10.016292] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.102192] NET: Registered protocol family 8
[   10.102198] NET: Registered protocol family 20
[   10.102308] AppArmor: AppArmor Filesystem Enabled
[   10.106173] Time: tsc clocksource has been installed.
[   10.122239] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   10.122246] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   10.122252] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   10.122258] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   10.122264] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   10.122270] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   10.122275] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   10.122281] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   10.122296] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   10.122307] system 00:06: ioport range 0x680-0x69f has been reserved
[   10.122312] system 00:06: ioport range 0x800-0x80f has been reserved
[   10.122318] system 00:06: ioport range 0x1000-0x107f has been reserved
[   10.122323] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   10.122328] system 00:06: ioport range 0x1640-0x164f has been reserved
[   10.122334] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[   10.122339] system 00:06: ioport range 0xff00-0xff7f has been reserved
[   10.122349] system 00:07: ioport range 0x6a0-0x6af has been reserved
[   10.122354] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[   10.153261] PCI: Bridge: 0000:00:1c.0
[   10.153266]   IO window: disabled.
[   10.153275]   MEM window: f0100000-f01fffff
[   10.153282]   PREFETCH window: 50000000-500fffff
[   10.153290] PCI: Bridge: 0000:00:1c.1
[   10.153293]   IO window: disabled.
[   10.153301]   MEM window: f0200000-f02fffff
[   10.153307]   PREFETCH window: disabled.
[   10.153316] PCI: Bridge: 0000:00:1c.2
[   10.153321]   IO window: 2000-2fff
[   10.153329]   MEM window: 50100000-501fffff
[   10.153336]   PREFETCH window: f0600000-f06fffff
[   10.153343] PCI: Bridge: 0000:00:1e.0
[   10.153346]   IO window: disabled.
[   10.153353]   MEM window: disabled.
[   10.153359]   PREFETCH window: disabled.
[   10.153406] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   10.153416] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.153448] ACPI: PCI Interrupt 0000:00:1c.1[b] -> GSI 16 (level, low) -> IRQ 17
[   10.153457] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.153487] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   10.153496] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   10.153514] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.153535] NET: Registered protocol family 2
[   10.194223] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.194691] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.195735] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.196290] TCP: Hash tables configured (established 131072 bind 65536)
[   10.196296] TCP reno registered
[   10.206354] checking if image is initramfs... it is
[   10.589467] Freeing initrd memory: 2699k freed
[   10.589769] Simple Boot Flag at 0x36 set to 0x80
[   10.590996] audit: initializing netlink socket (disabled)
[   10.591017] audit(1242175484.188:1): initialized
[   10.591281] highmem bounce pool size: 64 pages
[   10.595029] VFS: Disk quotas dquot_6.5.1
[   10.595175] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.596067] io scheduler noop registered
[   10.596073] io scheduler anticipatory registered
[   10.596077] io scheduler deadline registered
[   10.596190] io scheduler cfq registered (default)
[   10.596209] Boot video device is 0000:00:02.0
[   10.596498] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.596563] assign_interrupt_mode Found MSI capability
[   10.596620] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.596695] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.596838] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.596903] assign_interrupt_mode Found MSI capability
[   10.596956] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.597028] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.597169] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   10.597234] assign_interrupt_mode Found MSI capability
[   10.597287] Allocate Port Service[0000:00:1c.2: pcie00]
[   10.597351] Allocate Port Service[0000:00:1c.2: pcie02] 
[   10.602446] ACPI: AC Adapter [ACAD] (off-line)
[   10.649900] Switched to high resolution mode on CPU 1
[   10.653677] Switched to high resolution mode on CPU 0
[   10.737805] ACPI: Battery Slot [BAT1] (battery present)
[   10.738127] input: Power Button (FF) as /devices/virtual/input/input0
[   10.738135] ACPI: Power Button (FF) [PWRF]
[   10.738256] input: Lid Switch as /devices/virtual/input/input1
[   10.738335] ACPI: Lid Switch [LID0]
[   10.738455] input: Power Button (CM) as /devices/virtual/input/input2
[   10.738462] ACPI: Power Button (CM) [PWRB]
[   10.738589] input: Sleep Button (CM) as /devices/virtual/input/input3
[   10.738596] ACPI: Sleep Button (CM) [SLPB]
[   10.750501] ACPI: device:01 is registered as cooling_device0
[   10.750891] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[   10.750901] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.751607] ACPI: SSDT 3F6DCC25, 0245 (r2  PmRef  Cpu0Ist     3000 INTL 20050624)
[   10.751953] ACPI: SSDT 3F6DC5BB, 05E5 (r2  PmRef  Cpu0Cst     3001 INTL 20050624)
[   10.752651] Monitor-Mwait will be used to enter C-1 state
[   10.752656] Monitor-Mwait will be used to enter C-2 state
[   10.752661] Monitor-Mwait will be used to enter C-3 state
[   10.752740] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.752825] ACPI: ACPI0007:00 is registered as cooling_device1
[   10.752834] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.753323] ACPI: SSDT 3F6DCE6A, 00D4 (r2  PmRef  Cpu1Ist     3000 INTL 20050624)
[   10.753664] ACPI: SSDT 3F6DCBA0, 0085 (r2  PmRef  Cpu1Cst     3000 INTL 20050624)
[   10.754570] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   10.754655] ACPI: ACPI0007:01 is registered as cooling_device2
[   10.754663] ACPI: Processor [CPU1] (supports 8 throttling states)
[   10.779745] ACPI: LNXTHERM:01 is registered as thermal_zone0
[   10.786013] ACPI: Thermal Zone [TZ01] (31 C)
[   10.912839] Real Time Clock Driver v1.12ac
[   10.913192] hpet_acpi_add: no address or irqs in _CRS
[   10.913220] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.915445] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.916036] loop: module loaded
[   10.916119] Driver 'sd' needs updating - please use bus_type methods
[   10.916184] Driver 'sr' needs updating - please use bus_type methods
[   10.916385] ata_piix 0000:00:1f.1: version 2.12
[   10.916415] ACPI: PCI Interrupt 0000:00:1f.1[b] -> GSI 19 (level, low) -> IRQ 19
[   10.916470] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   10.916588] scsi0 : ata_piix
[   10.916725] scsi1 : ata_piix
[   10.917639] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   10.917646] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   11.081857] ata1.00: ATA-6: STEC PATA 16GB, E5221-10, max UDMA/133
[   11.081864] ata1.00: 30093840 sectors, multi 1: LBA 
[   11.089733] ata1.00: configured for UDMA/100
[   11.089789] ata2: port disabled. ignoring.
[   11.090004] scsi 0:0:0:0: Direct-Access     ATA      STEC PATA 16GB   E522 PQ: 0 ANSI: 5
[   11.090260] sd 0:0:0:0: [sda] 30093840 512-byte hardware sectors (15408 MB)
[   11.090288] sd 0:0:0:0: [sda] Write Protect is off
[   11.090295] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.090339] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.090436] sd 0:0:0:0: [sda] 30093840 512-byte hardware sectors (15408 MB)
[   11.090464] sd 0:0:0:0: [sda] Write Protect is off
[   11.090470] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.090518] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.090525]  sda: sda1 sda2
[   11.091135] sd 0:0:0:0: [sda] Attached SCSI disk
[   11.091273] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.091695] USB Universal Host Controller Interface driver v3.0
[   11.091804] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   11.091821] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.091828] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.091994] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.092038] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   11.092375] usb usb1: configuration #1 chosen from 1 choice
[   11.092460] hub 1-0:1.0: USB hub found
[   11.092472] hub 1-0:1.0: 2 ports detected
[   11.193316] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 19
[   11.193331] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.193338] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.193493] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.193535] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   11.193802] usb usb2: configuration #1 chosen from 1 choice
[   11.193892] hub 2-0:1.0: USB hub found
[   11.193910] hub 2-0:1.0: 2 ports detected
[   11.297204] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.297219] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.297225] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.297387] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.297428] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   11.297700] usb usb3: configuration #1 chosen from 1 choice
[   11.297787] hub 3-0:1.0: USB hub found
[   11.297798] hub 3-0:1.0: 2 ports detected
[   11.401100] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   11.401114] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.401120] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.401269] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.401310] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   11.401580] usb usb4: configuration #1 chosen from 1 choice
[   11.401664] hub 4-0:1.0: USB hub found
[   11.401678] hub 4-0:1.0: 2 ports detected
[   11.505019] Initializing USB Mass Storage driver...
[   11.505098] usbcore: registered new interface driver usb-storage
[   11.505104] USB Mass Storage support registered.
[   11.505181] usbcore: registered new interface driver libusual
[   11.505413] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.538308] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.538319] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.538537] mice: PS/2 mouse device common for all mice
[   11.613066] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   11.633995] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input6
[   11.684757] cpuidle: using governor ladder
[   12.684404] cpuidle: using governor menu
[   12.684472] sdhci: Secure Digital Host Controller Interface driver
[   12.684478] sdhci: Copyright(c) Pierre Ossman
[   12.684572] sdhci: SDHCI controller found at 0000:02:00.2 [197b:2381] (rev 0)
[   12.684618] ACPI: PCI Interrupt 0000:02:00.2[A] -> GSI 16 (level, low) -> IRQ 17
[   12.684654] PCI: Setting latency timer of device 0000:02:00.2 to 64
[   12.684805] mmc0: SDHCI at 0xf0100400 irq 17 DMA
[   12.688239] ACPI: PCI Interrupt 0000:02:00.3[A] -> GSI 16 (level, low) -> IRQ 17
[   12.688253] PCI: Setting latency timer of device 0000:02:00.3 to 64
[   12.688645] usbcore: registered new interface driver hiddev
[   12.688730] usbcore: registered new interface driver usbhid
[   12.688752] /root/src/hardy-netbook/debian/build/custom-source-lpia/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   12.688906] NET: Registered protocol family 1
[   12.689350] NET: Registered protocol family 10
[   12.689677] lo: Disabled Privacy Extensions
[   12.690237] NET: Registered protocol family 17
[   12.690275] Using IPI No-Shortcut mode
[   12.690492]   Magic number: 9:649:708
[   12.690824] Freeing unused kernel memory: 296k freed
[   13.079087] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   13.079116] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.079124] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.079328] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   13.083312] ehci_hcd 0000:00:1d.7: debug port 1
[   13.083332] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.083346] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf0544000
[   13.099394] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.099721] usb usb5: configuration #1 chosen from 1 choice
[   13.099820] hub 5-0:1.0: USB hub found
[   13.099835] hub 5-0:1.0: 8 ports detected
[   13.320110] Registering unionfs 1.4
[   13.320116] unionfs: debugging is not enabled
[   13.328170] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   13.413493] fuse init (API version 7.9)
[   13.603930] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   13.776867] usb 5-2: configuration #1 chosen from 1 choice
[   14.258316] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   14.437452] usb 4-1: configuration #1 chosen from 1 choice
[   14.744674] kjournald starting.  Commit interval 5 seconds
[   14.744696] EXT3-fs: mounted filesystem with ordered data mode.
[   15.145471] Clocksource tsc unstable (delta = -251259903 ns)
[   15.152145] Time: acpi_pm clocksource has been installed.
[   16.834010] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000
[   16.925995] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   17.103442] intel_rng: FWH not detected
[   17.152317] iTCO_vendor_support: vendor-support=0
[   17.174610] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   17.174909] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.174972] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.188025] ieee80211_crypt: registered algorithm 'NULL'
[   17.215500] r8169 Gigabit Ethernet driver 2.2LK loaded
[   17.215615] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   17.215684] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   17.217059] eth0: RTL8101e at 0xf8866000, 00:21:70:e3:73:15, XID 24a00000 IRQ 220
[   17.308917] ieee80211_crypt: registered algorithm 'TKIP'
[   17.376745] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   17.377180] EXT3 FS on sda2, internal journal
[   18.440686] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   18.440735] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.597928] Linux agpgart interface v0.102
[   18.610210] agpgart: Detected an Intel 945GME Chipset.
[   18.610455] agpgart: Detected 7932K stolen memory.
[   18.629391] agpgart: AGP aperture is 256M @ 0xd0000000
[   18.677333] [drm] Initialized drm 1.1.0 20060810
[   21.187510] drm_psb: exports duplicate symbol drm_order (owned by drm)
[   21.192302] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   21.192323] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   21.193464] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   35.479838] Bluetooth: Core ver 2.11
[   35.480775] NET: Registered protocol family 31
[   35.480787] Bluetooth: HCI device and connection manager initialized
[   35.480796] Bluetooth: HCI socket layer initialized
[   35.487625] Bluetooth: HCI USB driver ver 2.9
[   35.489299] usbcore: registered new interface driver hci_usb
[   35.566622] Bluetooth: L2CAP ver 2.9
[   35.566636] Bluetooth: L2CAP socket layer initialized
[   35.641661] Bluetooth: RFCOMM socket layer initialized
[   35.641690] Bluetooth: RFCOMM TTY layer initialized
[   35.641695] Bluetooth: RFCOMM ver 1.8
[   35.890992] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   35.940464] Linux video capture interface: v2.00
[   36.087823] uvcvideo: Found UVC 1.00 device Integrated Webcam (064e:a118)
[   36.103421] usbcore: registered new interface driver uvcvideo
[   36.103439] USB Video Class driver (v0.1.0)
[   36.692431] r8169: eth0: link down
[   36.694252] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.373667] ppdev: user-space parallel port driver
[   37.718869] wl: module license 'unspecified' taints kernel.
[   37.722658] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   37.722682] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   37.743722] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.9
[  330.941882] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  341.040817] eth1: no IPv6 routers present
[  645.558092] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  645.733918] usb 4-2: configuration #1 chosen from 1 choice
[  645.736845] scsi2 : SCSI emulation for USB Mass Storage devices
[  645.738401] usb-storage: device found at 3
[  645.738421] usb-storage: waiting for device to settle before scanning
[  650.735039] usb-storage: device scan complete
[  650.738052] scsi 2:0:0:0: Direct-Access     LEXAR    JUMPDRIVE        1.10 PQ: 0 ANSI: 1 CCS
[  650.745993] sd 2:0:0:0: [sdb] 251904 512-byte hardware sectors (129 MB)
[  650.751965] sd 2:0:0:0: [sdb] Write Protect is off
[  650.751988] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  650.752000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  650.765044] sd 2:0:0:0: [sdb] 251904 512-byte hardware sectors (129 MB)
[  650.769958] sd 2:0:0:0: [sdb] Write Protect is off
[  650.769981] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  650.769993] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  650.770015]  sdb: sdb1
[  650.779293] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  650.779470] sd 2:0:0:0: Attached scsi generic sg1 type 0


tarados@tarados:~$ sudo lshw -C network
[sudo] password for tarados: 
sudo: lshw: command not found


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

tarados@tarados:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').


tarados@tarados:~$ lsb_release -d
Description:    Ubuntu 8.04.1

tarados@tarados:~$ uname -mr
2.6.24-19-lpia i686


tarados@tarados:~$ sudo /etc/init.d/networking restart

------------------------------------------------------------------------------

Nothing happens when I do the networking restart command. Also, my wifi network is cbf0. I'm just completely lost. I was able to connect at several other places today so I know the wifi is working.

Thank you so much for your help!

---

### Post by pytheas22 on 2009-05-13
Thanks for that information--it provides a much clearer picture of the potential sources of your problem.

The first thing that you should try is to install wicd, which is an alternative connection manager that may work better for you.  You can install wicd by connecting to the Internet (either wirelessly at work, or using the ethernet wire) and running these commands (if possible, you should copy and paste them, because it's important not to make typos when running commands that will modify your system, as these will):
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

When this is done, go to your Applications>Internet menu and you will see a program labeled 'WICD Connection Manager' (or something similar).  Open it up, and press the scan button to search for networks.  (If there are no scan results, press the 'Preferences' button in the top panel of wicd, and in the window that pops up, make sure your 'wireless interface' is set to 'eth1'.)

When the scan completes, scroll down the list of networks till you see yours.  Click on that section, then click 'advanced settings' to enter the WEP key (you need to enter the WEP key first; it won't automatically prompt you for it later).  When that's done, click connect, and hopefully it will get you online.

Please report back with your results.  If wicd doesn't help, there are several other things to try next.

---

### Post by TaraDLS on 2009-05-13
I ran the commands, copying and pasting them so they were exact and this is what I got. I am assuming that it didn't install. Is there something I did wrong or something else I can try?

Thanks!

----------------------------------
tarados@tarados:~$ echo 'deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras' | sudo tee -a /etc/apt/sources.list
[sudo] password for tarados: 
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
tarados@tarados:~$ wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -
OK
tarados@tarados:~$ sudo apt-get update
Get:1 [http://apt.wicd.net](http://apt.wicd.net) hardy Release.gpg [197B]
Get:2 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg [191B]
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_US
Ign [http://apt.wicd.net](http://apt.wicd.net) hardy/extras Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_US
Get:3 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg [189B]
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_US
Get:4 [http://apt.wicd.net](http://apt.wicd.net) hardy Release [17.2kB]
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_US
Get:5 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg [189B]
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_US
Get:6 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg [280B]
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_US
Get:7 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg [280B]
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Get:8 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release [58.5kB]
Get:9 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release [58.5kB]
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release
Get:10 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release [4656B]
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Get:11 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources [338kB]
Get:12 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources [1323kB]  
Get:13 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources [60.9kB]
Get:14 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources [1488B] 
Get:15 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages [294kB]
Get:16 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages [78.5kB]
Get:17 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages [14.2kB]
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages   
Get:18 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources [88.0kB]
Get:19 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources [22.7kB]
Get:20 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources [2795B]
Get:21 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources [908B]
Get:22 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages [48.4kB]
Get:23 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages [24.9kB]
Get:24 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages [5388B]
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages  
Get:25 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources [12.5kB]
Get:26 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources [4530B]
Get:27 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources [14B]
Get:28 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources [908B]
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages    
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources     
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources 
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages       
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages   
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages 
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages 
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources        
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources    
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources  
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources  
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages    
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources     
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources 
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Get:29 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages [120kB]
Get:30 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages [35.9kB]
Get:31 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages [1907B]
Get:32 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages [2425B]
Get:33 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources [29.4kB]
Get:34 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources [8081B]
Get:35 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources [541B]
Get:36 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources [989B]
Fetched 2661kB in 2min16s (19.4kB/s)                                           
W: Failed to fetch [http://apt.wicd.net/dists/hardy/Release](http://apt.wicd.net/dists/hardy/Release)  Unable to find expected entry  extras/binary-lpia/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
tarados@tarados:~$ sudo apt-get install wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wicd
tarados@tarados:~$

---

### Post by pytheas22 on 2009-05-13
hmm, that's strange.  It looks like there may have been a temporary problem with wicd's web server.  I just tried installing it now and it works fine.  Could you please try these commands again:
```

sudo apt-get update
sudo apt-get install wicd
```

---

### Post by TaraDLS on 2009-05-14
I tried running the commands again and this is what I got. My assumption (probably wrong) is that I need to run the command "dpkg --configure -a" but since I wasn't sure and didn't want to screw anything up, I did not do that. Any additional assistance you can provide would be greatly appreciated.

Thanks!

---------------------------------------------------------------
tarados@tarados:~$ echo 'deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras' | sudo tee -a /etc/apt/sources.list
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
tarados@tarados:~$ wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -
OK
tarados@tarados:~$ sudo apt-get update
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_US
Hit [http://apt.wicd.net](http://apt.wicd.net) hardy Release.gpg
Ign [http://apt.wicd.net](http://apt.wicd.net) hardy/extras Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_US
Hit [http://apt.wicd.net](http://apt.wicd.net) hardy Release          
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
W: Failed to fetch [http://apt.wicd.net/dists/hardy/Release](http://apt.wicd.net/dists/hardy/Release)  Unable to find expected entry  extras/binary-lpia/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
tarados@tarados:~$ sudo apt-get install wicd
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
tarados@tarados:~$

---

### Post by pytheas22 on 2009-05-14
I'm sorry this is proving more complicated than anticipated.  But yes, please try running:
```

sudo dpkg --configure -a
```

When that's done, run again:
```

sudo apt-get update
sudo apt-get install wicd
```

Please let me know how it goes.

---

### Post by TaraDLS on 2009-05-14
I really can't thank you enough for your assistance. I apologize that this is so complicated. I ran the command and got the following result. I assume I need to set up a superuser privilege but am unsure how to do that and still very confused.

Thank you again!

--------------------------------------------------------

tarados@tarados:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

---

### Post by pytheas22 on 2009-05-14
> I really can't thank you enough for your assistance. I apologize that this is so complicated. I ran the command and got the following result. I assume I need to set up a superuser privilege but am unsure how to do that and still very confused.


Exactly, you need to be the superuser.  You do that by prefixing the command with the word 'sudo'.  So type:
```

sudo dpkg --configure -a
```

It should work then.  When it's done, type again:
```

sudo apt-get update
sudo apt-get install wicd
```

If this still fails, you can also install wicd by downloading [this file]("http://sourceforge.net/project/downloading.php?group_id=194573&filename=wicd_1.5.8_all.deb&a=13443539"), saving it to your desktop in Ubuntu and double-clicking it (like you're used to with Windows).  You'll be asked for your password, then an installer for wicd will open.  This isn't the preferred way of installing applications, but since you're running into so many problems with the first method, you may find it easier just to download the installer directly and double-click.

---

### Post by TaraDLS on 2009-05-16
I apologize for how complicated this is. I am still having trouble. I ran the commands and still got an error. Then I downloaded the file that you suggested and attempted to install it. I got an error message that said "Error: conflicts with the installed package 'network manager'" I feel like a complete idiot and I am just about ready to send the computer back to Dell regardless of the 15% restocking fee as I am feeling way over my head with Ubuntu. I am willing to try a few more things but don't want to take up too much of anyone's time. Thanks!

tarados@tarados:~$ sudo apt-get update
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_US
Hit [http://apt.wicd.net](http://apt.wicd.net) hardy Release.gpg      
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg
Ign [http://apt.wicd.net](http://apt.wicd.net) hardy/extras Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_US
Hit [http://apt.wicd.net](http://apt.wicd.net) hardy Release          
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_US
Get:1 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg [280B]
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release
Get:2 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release [2742B]
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Get:3 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Packages [618kB]
Get:4 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Sources [175kB]
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Fetched 796kB in 3s (207kB/s)                       
W: Failed to fetch [http://apt.wicd.net/dists/hardy/Release](http://apt.wicd.net/dists/hardy/Release)  Unable to find expected entry  extras/binary-lpia/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
tarados@tarados:~$ sudo apt-get install wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wicd
tarados@tarados:~$

---

### Post by TaraDLS on 2009-05-16
I actually got it working. When I saw that the WICD package wouldn't install because of the 'network manager', I uninstalled 'network manager' and tried installng WICD again. That still didn't work, so I reinstalled 'network manager' and everything else associated with it so that I could at least use my wired connection and keep on trying to fix it. After reinstalling 'network manager' and restarting my computer, I got different options when I clicked on the network connections icon on the upper right hand side of my screen and was able to type in my WEP key and get connected. I don't know exactly what happened to make it work but it does now work.

Thank you very much for all your help. A completely different question now, is there a good beginner's book for Ubuntu and Linux. I'd like to learn more about how I can use and operate the system.

---

### Post by pytheas22 on 2009-05-16
hmmm, I'm not sure why that worked, but I'm glad it did :)

The only Ubuntu book I've used personally is [this one]("http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942"), which is well written and covers everything a normal user would want to know (it doesn't go into using the command line, but in my opinion that's good because most normal users don't want to use that).  There's also [free online documentation]("https://help.ubuntu.com/") that covers nearly everything anyone could ever want to know about Ubuntu, although some pages are not well written and others are out-of-date.

I hope you enjoy using Ubuntu!

---

