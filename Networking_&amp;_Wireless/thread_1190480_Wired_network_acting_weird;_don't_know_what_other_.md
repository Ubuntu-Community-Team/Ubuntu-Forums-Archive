---
title: "Wired network acting weird; don't know what other info to give"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by Veteropinguis on 2009-06-17
I'm running 9.04 on a machine I built myself. When I first installed Jaunty, my network was recognized right away. A few days ago, my network connection had stopped working when I came home.

My router is a Linksys WRTP54G. The rest of my family uses our wireless network, which has been fine. My laptop, running 8.10, can connect to the wireless network with no problems. I don't know how to find out what my network hardware is.

All I know how to tell you is that the network indicator has two green dots and the swirling blue lines cycle around once, and then I get a notification telling me I've been disconnected from the wireless network.

What can I do to troubleshoot this?

EDIT: Argh. I seem to have removed the network connector icon from my panels and I can't find out how to get it back. I know that's very vague but maybe some of you know what I mean. So, maybe some of you lovely people could tell me how to put that back...

I tried [http://ubuntuforums.org/archive/index.php/t-868077.html](http://ubuntuforums.org/archive/index.php/t-868077.html) and while I unmounted the driver with no problems, when I tried to remount it I got this:

FATAL: Error inserting e1000 (/lib/modules/2.6.28-11-generic/kernel/drivers/net/e1000/e1000.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I don't know what that is, but that's not good. I might just reinstall soon. This separate /home partition was a great idea.

---

### Post by aesis05401 on 2009-06-17
*snip* I see your latest edit, and you are beyond any of my suggestions... so I will just zap this post.  Good luck.

---

### Post by Veteropinguis on 2009-06-17
Aesis, if you see this again, would you mind putting your post back if you can?

It might be helpful if my reinstall doesn't fix this, or if the problem pops up again.

---

### Post by MaindotC on 2009-06-17
Post the output of:
```

lshw -C network
lsmod
ifconfig
iwconfig
iwlist scan

```
Please also try to recount anything that happened prior to this event.  Locate messages in your syslog if you recall the date, any applications you installed or hardware changes, anomalies, etc.

---

### Post by Veteropinguis on 2009-06-18
Looks like the reinstall killed my syslog, so nothing's there.

I don't think I did anything in the last couple days to mess anything up. I installed a few games (Super Tux, Frozen Bubble) and fiddled a bit with Anki. Connected my iPod a few times, don't know why that would do anything- especially since I didn't even sync it.

Here's the output from those commands:

veteropinguis@archimedes:~$ sudo lshw -C network
[sudo] password for veteropinguis: 
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 00
       serial: 00:19:db:62:df:57
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-10 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:ee:45:fa:b6:a4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
veteropinguis@archimedes:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
ppdev                  15620  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
psmouse                61972  0 
serio_raw              13316  0 
pcspkr                 10496  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
parport_pc             40100  1 
i82975x_edac           12292  0 
parport                42220  3 lp,ppdev,parport_pc
edac_core              47404  1 i82975x_edac
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
floppy                 64324  0 
e1000e                121136  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
veteropinguis@archimedes:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

veteropinguis@archimedes:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:db:62:df:57  
          inet6 addr: fe80::219:dbff:fe62:df57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:7614 (7.6 KB)
          Memory:fdce0000-fdd00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

veteropinguis@archimedes:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

veteropinguis@archimedes:~$

---

### Post by Veteropinguis on 2009-06-18
Bump...

I've been doing research, but nothing has helped. I'm guessing the '*-network DISABLED' thing is the root of my woes but I don't know how to fix it.

---

### Post by Veteropinguis on 2009-06-18
It looks like auto eth0 is set to 'never', I imagine that's a big part of my problem. I'm not sure how I didn't notice this before, and I also can't figure out how to turn it on.

---

### Post by Veteropinguis on 2009-06-18
Anyone? I can't find how to fix my auto eth0 problem. Why is it set to 'never' and how do I make it work? I also tried making Wired Connection 1, but it was also automatically set to 'never'. Why?

---

### Post by Veteropinguis on 2009-06-18
This is what's in my /etc/network/interfaces file:

auto lo
iface lo inet loopback
auto eth0
iface ethl inet dhcp

---

### Post by Cacadril on 2009-06-18
You don't have any wireless network adapter in your computer? By comparison, I have three entries, and the third is "disabled" with "logical name" pan0, just like yours. I don't know what "pan0" is, it turned up first with some kernel, may be a year ago. I always thought it was some dummy device because all my real devices show up as before.

A possible reason why your network was gone when you came home could be that you had automatic updates enabled, and got a new kernel. Is that possible? I am browsing this forum because my network stopped working when I updated and got kernel 2.6.28-13. Rebooting and selecting the previous kernel (...28-11) fixed the problem for now.

I suggest you post the output of "lspci" as well. It shows the contents of the PCI bus. Next look through /var/log/kern.log.

---

### Post by Veteropinguis on 2009-06-18
lspci:
```
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

```

Is there anything in particular I should look for in the log? That's a massive wall of text and I think it was too big for me to post here in one go.

---

### Post by Veteropinguis on 2009-06-18
kern.log (edited down): ```
Jun 18 19:45:46 archimedes kernel: [   60.358600] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 19:45:46 archimedes kernel: [   60.358607] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 19:45:46 archimedes kernel: [   61.090613] mtrr: no MTRR for d0000000,ff00000 found
Jun 18 19:45:46 archimedes kernel: [   61.190247] 0000:04:00.0: eth0: Link is Down
Jun 18 19:45:48 archimedes kernel: [   62.970562] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 19:45:48 archimedes kernel: [   62.970568] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 19:45:49 archimedes kernel: [   63.808136] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:21 archimedes kernel: Inspecting /boot/System.map-2.6.28-11-generic
Jun 18 20:02:21 archimedes kernel: Cannot find map file.
Jun 18 20:02:21 archimedes kernel: Loaded 54150 symbols from 40 modules.
Jun 18 20:02:21 archimedes kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
Jun 18 20:02:21 archimedes kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 18 20:02:21 archimedes kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 18 20:02:21 archimedes kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
Jun 18 20:02:21 archimedes kernel: [    0.000000] KERNEL supported cpus:
Jun 18 20:02:21 archimedes kernel: [    0.000000]   Intel GenuineIntel
Jun 18 20:02:21 archimedes kernel: [    0.000000]   AMD AuthenticAMD
Jun 18 20:02:21 archimedes kernel: [    0.000000]   NSC Geode by NSC
Jun 18 20:02:21 archimedes kernel: [    0.000000]   Cyrix CyrixInstead
Jun 18 20:02:21 archimedes kernel: [    0.000000]   Centaur CentaurHauls
Jun 18 20:02:21 archimedes kernel: [    0.000000]   Transmeta GenuineTMx86
Jun 18 20:02:21 archimedes kernel: [    0.000000]   Transmeta TransmetaCPU
Jun 18 20:02:21 archimedes kernel: [    0.000000]   UMC UMC UMC UMC
Jun 18 20:02:21 archimedes kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 18 20:02:21 archimedes kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000] DMI 2.4 present.
Jun 18 20:02:21 archimedes kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Jun 18 20:02:21 archimedes kernel: [    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
Jun 18 20:02:21 archimedes kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jun 18 20:02:21 archimedes kernel: [    0.000000] modified physical RAM map:
Jun 18 20:02:21 archimedes kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Jun 18 20:02:21 archimedes kernel: [    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
Jun 18 20:02:21 archimedes kernel: [    0.000000] RAMDISK: 378be000 - 37fefef0
Jun 18 20:02:21 archimedes kernel: [    0.000000] Allocated new RAMDISK: 00881000 - 00fb2ef0
Jun 18 20:02:21 archimedes kernel: [    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fefeef to 00881000 - 00fb2eef
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: RSDP 000F9150, 0014 (r0 IntelR)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: DSDT 7FEE3180, 4E92 (r1 INTELR AWRDACPI     1000 MSFT  100000E)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: _HPT 7FEE8180, 0038 (r1 IntelR AWRDACPI 42302E31 AWRD       98)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: MCFG 7FEE8200, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: APIC 7FEE8080, 0084 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: SSDT 7FEE8280, 01EF (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: SSDT 7FEE87E0, 02F9 (r1  PmRef    CpuPm     3000 INTL 20041203)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 18 20:02:21 archimedes kernel: [    0.000000] 1162MB HIGHMEM available.
Jun 18 20:02:21 archimedes kernel: [    0.000000] 883MB LOWMEM available.
Jun 18 20:02:21 archimedes kernel: [    0.000000]   mapped low ram: 0 - 373fe000
Jun 18 20:02:21 archimedes kernel: [    0.000000]   low ram: 00000000 - 373fe000
Jun 18 20:02:21 archimedes kernel: [    0.000000]   bootmap 00012000 - 00018e80
Jun 18 20:02:21 archimedes kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
Jun 18 20:02:21 archimedes kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 18 20:02:21 archimedes kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jun 18 20:02:21 archimedes kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jun 18 20:02:21 archimedes kernel: [    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
Jun 18 20:02:21 archimedes kernel: [    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
Jun 18 20:02:21 archimedes kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Jun 18 20:02:21 archimedes kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jun 18 20:02:21 archimedes kernel: [    0.000000]   #7 [0000881000 - 0000fb2ef0]      NEW RAMDISK ==> [0000881000 - 0000fb2ef0]
Jun 18 20:02:21 archimedes kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Jun 18 20:02:21 archimedes kernel: [    0.000000] found SMP MP-table at [c00f4fa0] 000f4fa0
Jun 18 20:02:21 archimedes kernel: [    0.000000] Zone PFN ranges:
Jun 18 20:02:21 archimedes kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 18 20:02:21 archimedes kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
Jun 18 20:02:21 archimedes kernel: [    0.000000]   HighMem  0x000373fe -> 0x0007fee0
Jun 18 20:02:21 archimedes kernel: [    0.000000] Movable zone start PFN for each node
Jun 18 20:02:21 archimedes kernel: [    0.000000] early_node_map[2] active PFN ranges
Jun 18 20:02:21 archimedes kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jun 18 20:02:21 archimedes kernel: [    0.000000]     0: 0x00000100 -> 0x0007fee0
Jun 18 20:02:21 archimedes kernel: [    0.000000] On node 0 totalpages: 523887
Jun 18 20:02:21 archimedes kernel: [    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
Jun 18 20:02:21 archimedes kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jun 18 20:02:21 archimedes kernel: [    0.000000]   DMA zone: 0 pages reserved
Jun 18 20:02:21 archimedes kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jun 18 20:02:21 archimedes kernel: [    0.000000]   Normal zone: 1736 pages used for memmap
Jun 18 20:02:21 archimedes kernel: [    0.000000]   Normal zone: 220470 pages, LIFO batch:31
Jun 18 20:02:21 archimedes kernel: [    0.000000]   HighMem zone: 2326 pages used for memmap
Jun 18 20:02:21 archimedes kernel: [    0.000000]   HighMem zone: 295372 pages, LIFO batch:31
Jun 18 20:02:21 archimedes kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jun 18 20:02:21 archimedes kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 18 20:02:21 archimedes kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 18 20:02:21 archimedes kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 18 20:02:21 archimedes kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 18 20:02:21 archimedes kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jun 18 20:02:21 archimedes kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 18 20:02:21 archimedes kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jun 18 20:02:21 archimedes kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jun 18 20:02:21 archimedes kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
Jun 18 20:02:21 archimedes kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
Jun 18 20:02:21 archimedes kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Jun 18 20:02:21 archimedes kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519793
Jun 18 20:02:21 archimedes kernel: [    0.000000] Kernel command line: root=UUID=b781086a-bfe1-4896-80cd-480cf1060764 ro quiet splash 
Jun 18 20:02:21 archimedes kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 18 20:02:21 archimedes kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 18 20:02:21 archimedes kernel: [    0.000000] Initializing CPU#0
Jun 18 20:02:21 archimedes kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun 18 20:02:21 archimedes kernel: [    0.000000] Fast TSC calibration using PIT
Jun 18 20:02:21 archimedes kernel: [    0.000000] Detected 3014.584 MHz processor.
Jun 18 20:02:21 archimedes kernel: [    0.004000] Console: colour VGA+ 80x25
Jun 18 20:02:21 archimedes kernel: [    0.004000] console [tty0] enabled
Jun 18 20:02:21 archimedes kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 18 20:02:21 archimedes kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 18 20:02:21 archimedes kernel: [    0.004000] allocated 10479680 bytes of page_cgroup
Jun 18 20:02:21 archimedes kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Jun 18 20:02:21 archimedes kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Jun 18 20:02:21 archimedes kernel: [    0.004000] Memory: 2052060k/2096000k available (4126k kernel code, 42708k reserved, 2208k data, 532k init, 1190792k highmem)
Jun 18 20:02:21 archimedes kernel: [    0.004000] virtual kernel memory layout:
Jun 18 20:02:21 archimedes kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jun 18 20:02:21 archimedes kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jun 18 20:02:21 archimedes kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
Jun 18 20:02:21 archimedes kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
Jun 18 20:02:21 archimedes kernel: [    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
Jun 18 20:02:21 archimedes kernel: [    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
Jun 18 20:02:21 archimedes kernel: [    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
Jun 18 20:02:21 archimedes kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun 18 20:02:21 archimedes kernel: [    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jun 18 20:02:21 archimedes kernel: [    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 6029.16 BogoMIPS (lpj=12058336)
Jun 18 20:02:21 archimedes kernel: [    0.004032] Security Framework initialized
Jun 18 20:02:21 archimedes kernel: [    0.004039] SELinux:  Disabled at boot.
Jun 18 20:02:21 archimedes kernel: [    0.004061] AppArmor: AppArmor initialized
Jun 18 20:02:21 archimedes kernel: [    0.004073] Mount-cache hash table entries: 512
Jun 18 20:02:21 archimedes kernel: [    0.004233] Initializing cgroup subsys ns
Jun 18 20:02:21 archimedes kernel: [    0.004237] Initializing cgroup subsys cpuacct
Jun 18 20:02:21 archimedes kernel: [    0.004241] Initializing cgroup subsys memory
Jun 18 20:02:21 archimedes kernel: [    0.004245] Initializing cgroup subsys freezer
Jun 18 20:02:21 archimedes kernel: [    0.004265] CPU: Trace cache: 12K uops, L1 D cache: 16K
Jun 18 20:02:21 archimedes kernel: [    0.004268] CPU: L2 cache: 2048K
Jun 18 20:02:21 archimedes kernel: [    0.004272] CPU: Physical Processor ID: 0
Jun 18 20:02:21 archimedes kernel: [    0.004274] CPU: Processor Core ID: 0
Jun 18 20:02:21 archimedes kernel: [    0.004277] using mwait in idle threads.
Jun 18 20:02:21 archimedes kernel: [    0.004290] Checking 'hlt' instruction... OK.
Jun 18 20:02:21 archimedes kernel: [    0.023288] ACPI: Core revision 20080926
Jun 18 20:02:21 archimedes kernel: [    0.025852] ACPI: Checking initramfs for custom DSDT
Jun 18 20:02:21 archimedes kernel: [    0.316489] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 18 20:02:21 archimedes kernel: [    0.359181] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
Jun 18 20:02:21 archimedes kernel: [    0.360001] Booting processor 1 APIC 0x1 ip 0x6000
Jun 18 20:02:21 archimedes kernel: [    0.004000] Initializing CPU#1
Jun 18 20:02:21 archimedes kernel: [    0.004000] Calibrating delay using timer specific routine.. 6029.97 BogoMIPS (lpj=12059947)
Jun 18 20:02:21 archimedes kernel: [    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
Jun 18 20:02:21 archimedes kernel: [    0.004000] CPU: L2 cache: 2048K
Jun 18 20:02:21 archimedes kernel: [    0.004000] CPU: Physical Processor ID: 0
Jun 18 20:02:21 archimedes kernel: [    0.004000] CPU: Processor Core ID: 0
Jun 18 20:02:21 archimedes kernel: [    0.448573] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
Jun 18 20:02:21 archimedes kernel: [    0.448598] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun 18 20:02:21 archimedes kernel: [    0.452047] Brought up 2 CPUs
Jun 18 20:02:21 archimedes kernel: [    0.452052] Total of 2 processors activated (12059.14 BogoMIPS).
Jun 18 20:02:21 archimedes kernel: [    0.452108] CPU0 attaching sched-domain:
Jun 18 20:02:21 archimedes kernel: [    0.452112]  domain 0: span 0-1 level SIBLING
Jun 18 20:02:21 archimedes kernel: [    0.452115]   groups: 0 1
Jun 18 20:02:21 archimedes kernel: [    0.452123] CPU1 attaching sched-domain:
Jun 18 20:02:21 archimedes kernel: [    0.452126]  domain 0: span 0-1 level SIBLING
Jun 18 20:02:21 archimedes kernel: [    0.452129]   groups: 1 0
Jun 18 20:02:21 archimedes kernel: [    0.452215] net_namespace: 776 bytes
Jun 18 20:02:21 archimedes kernel: [    0.452215] Booting paravirtualized kernel on bare hardware
Jun 18 20:02:21 archimedes kernel: [    0.452426] Time: 23:59:01  Date: 06/18/09
Jun 18 20:02:21 archimedes kernel: [    0.452426] regulator: core version 0.5
Jun 18 20:02:21 archimedes kernel: [    0.452426] NET: Registered protocol family 16
Jun 18 20:02:21 archimedes kernel: [    0.452426] EISA bus registered
Jun 18 20:02:21 archimedes kernel: [    0.452426] ACPI: bus type pci registered
Jun 18 20:02:21 archimedes kernel: [    0.452426] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jun 18 20:02:21 archimedes kernel: [    0.452426] PCI: MCFG area at e0000000 reserved in E820
Jun 18 20:02:21 archimedes kernel: [    0.452426] PCI: Using MMCONFIG for extended config space
Jun 18 20:02:21 archimedes kernel: [    0.452426] PCI: Using configuration type 1 for base access
Jun 18 20:02:21 archimedes kernel: [    0.456205] ACPI: EC: Look up EC in DSDT
Jun 18 20:02:21 archimedes kernel: [    0.464952] ACPI: Interpreter enabled
Jun 18 20:02:21 archimedes kernel: [    0.464962] ACPI: (supports S0 S1 S4 S5)
Jun 18 20:02:21 archimedes kernel: [    0.464989] ACPI: Using IOAPIC for interrupt routing
Jun 18 20:02:21 archimedes kernel: [    0.471934] ACPI: No dock devices found.
Jun 18 20:02:21 archimedes kernel: [    0.471950] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 18 20:02:21 archimedes kernel: [    0.472087] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jun 18 20:02:21 archimedes kernel: [    0.472092] pci 0000:00:01.0: PME# disabled
Jun 18 20:02:21 archimedes kernel: [    0.472179] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff8000-0xfdffbfff]
Jun 18 20:02:21 archimedes kernel: [    0.472218] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun 18 20:02:21 archimedes kernel: [    0.472223] pci 0000:00:1b.0: PME# disabled
Jun 18 20:02:21 archimedes kernel: [    0.472286] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun 18 20:02:21 archimedes kernel: [    0.472291] pci 0000:00:1c.0: PME# disabled
Jun 18 20:02:21 archimedes kernel: [    0.472356] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jun 18 20:02:21 archimedes kernel: [    0.472361] pci 0000:00:1c.1: PME# disabled
Jun 18 20:02:21 archimedes kernel: [    0.472430] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jun 18 20:02:21 archimedes kernel: [    0.472435] pci 0000:00:1c.5: PME# disabled
Jun 18 20:02:21 archimedes kernel: [    0.472493] pci 0000:00:1d.0: reg 20 io port: [0xff00-0xff1f]
Jun 18 20:02:21 archimedes kernel: [    0.472551] pci 0000:00:1d.1: reg 20 io port: [0xfe00-0xfe1f]
Jun 18 20:02:21 archimedes kernel: [    0.472609] pci 0000:00:1d.2: reg 20 io port: [0xfd00-0xfd1f]
Jun 18 20:02:21 archimedes kernel: [    0.472669] pci 0000:00:1d.3: reg 20 io port: [0xfc00-0xfc1f]
Jun 18 20:02:21 archimedes kernel: [    0.472723] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdfff000-0xfdfff3ff]
Jun 18 20:02:21 archimedes kernel: [    0.472768] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jun 18 20:02:21 archimedes kernel: [    0.472774] pci 0000:00:1d.7: PME# disabled
Jun 18 20:02:21 archimedes kernel: [    0.472949] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
Jun 18 20:02:21 archimedes kernel: [    0.472957] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
Jun 18 20:02:21 archimedes kernel: [    0.472965] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
Jun 18 20:02:21 archimedes kernel: [    0.472972] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
Jun 18 20:02:21 archimedes kernel: [    0.472980] pci 0000:00:1f.1: reg 20 io port: [0xfb00-0xfb0f]
Jun 18 20:02:21 archimedes kernel: [    0.473031] pci 0000:00:1f.2: reg 10 io port: [0xfa00-0xfa07]
Jun 18 20:02:21 archimedes kernel: [    0.473039] pci 0000:00:1f.2: reg 14 io port: [0xf900-0xf903]
Jun 18 20:02:21 archimedes kernel: [    0.473046] pci 0000:00:1f.2: reg 18 io port: [0xf800-0xf807]
Jun 18 20:02:21 archimedes kernel: [    0.473054] pci 0000:00:1f.2: reg 1c io port: [0xf700-0xf703]
Jun 18 20:02:21 archimedes kernel: [    0.473062] pci 0000:00:1f.2: reg 20 io port: [0xf600-0xf60f]
Jun 18 20:02:21 archimedes kernel: [    0.473070] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfdffe000-0xfdffe3ff]
Jun 18 20:02:21 archimedes kernel: [    0.473089] pci 0000:00:1f.2: PME# supported from D3hot
Jun 18 20:02:21 archimedes kernel: [    0.473094] pci 0000:00:1f.2: PME# disabled
Jun 18 20:02:21 archimedes kernel: [    0.473153] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
Jun 18 20:02:21 archimedes kernel: [    0.473219] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
Jun 18 20:02:21 archimedes kernel: [    0.473231] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
Jun 18 20:02:21 archimedes kernel: [    0.473243] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
Jun 18 20:02:21 archimedes kernel: [    0.473250] pci 0000:01:00.0: reg 24 io port: [0xbf00-0xbf7f]
Jun 18 20:02:21 archimedes kernel: [    0.473257] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
Jun 18 20:02:21 archimedes kernel: [    0.473322] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
Jun 18 20:02:21 archimedes kernel: [    0.473327] pci 0000:00:01.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
Jun 18 20:02:21 archimedes kernel: [    0.473333] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
Jun 18 20:02:21 archimedes kernel: [    0.473389] pci 0000:00:1c.0: bridge io port: [0xa000-0xafff]
Jun 18 20:02:21 archimedes kernel: [    0.473394] pci 0000:00:1c.0: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
Jun 18 20:02:21 archimedes kernel: [    0.473402] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfd600000-0xfd6fffff]
Jun 18 20:02:21 archimedes kernel: [    0.473517] pci 0000:03:00.0: reg 24 32bit mmio: [0xfdefe000-0xfdefffff]
Jun 18 20:02:21 archimedes kernel: [    0.473543] pci 0000:03:00.0: PME# supported from D3hot
Jun 18 20:02:21 archimedes kernel: [    0.473550] pci 0000:03:00.0: PME# disabled
Jun 18 20:02:21 archimedes kernel: [    0.473616] pci 0000:03:00.1: reg 10 io port: [0xef00-0xef07]
Jun 18 20:02:21 archimedes kernel: [    0.473627] pci 0000:03:00.1: reg 14 io port: [0xee00-0xee03]
Jun 18 20:02:21 archimedes kernel: [    0.473639] pci 0000:03:00.1: reg 18 io port: [0xed00-0xed07]
Jun 18 20:02:21 archimedes kernel: [    0.473650] pci 0000:03:00.1: reg 1c io port: [0xec00-0xec03]
Jun 18 20:02:21 archimedes kernel: [    0.473661] pci 0000:03:00.1: reg 20 io port: [0xeb00-0xeb0f]
Jun 18 20:02:21 archimedes kernel: [    0.473765] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
Jun 18 20:02:21 archimedes kernel: [    0.473770] pci 0000:00:1c.1: bridge 32bit mmio: [0xfde00000-0xfdefffff]
Jun 18 20:02:21 archimedes kernel: [    0.473778] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
Jun 18 20:02:21 archimedes kernel: [    0.473858] pci 0000:04:00.0: reg 10 32bit mmio: [0xfdce0000-0xfdcfffff]
Jun 18 20:02:21 archimedes kernel: [    0.473872] pci 0000:04:00.0: reg 14 32bit mmio: [0xfdb00000-0xfdbfffff]
Jun 18 20:02:21 archimedes kernel: [    0.473885] pci 0000:04:00.0: reg 18 io port: [0xdf00-0xdf1f]
Jun 18 20:02:21 archimedes kernel: [    0.473949] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
Jun 18 20:02:21 archimedes kernel: [    0.473957] pci 0000:04:00.0: PME# disabled
Jun 18 20:02:21 archimedes kernel: [    0.474030] pci 0000:00:1c.5: bridge io port: [0xd000-0xdfff]
Jun 18 20:02:21 archimedes kernel: [    0.474036] pci 0000:00:1c.5: bridge 32bit mmio: [0xfdb00000-0xfdcfffff]
Jun 18 20:02:21 archimedes kernel: [    0.474044] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
Jun 18 20:02:21 archimedes kernel: [    0.474097] pci 0000:05:03.0: reg 10 32bit mmio: [0xfd8ff000-0xfd8ff7ff]
Jun 18 20:02:21 archimedes kernel: [    0.474107] pci 0000:05:03.0: reg 14 io port: [0xcf00-0xcf7f]
Jun 18 20:02:21 archimedes kernel: [    0.474155] pci 0000:05:03.0: supports D2
Jun 18 20:02:21 archimedes kernel: [    0.474157] pci 0000:05:03.0: PME# supported from D2 D3hot D3cold
Jun 18 20:02:21 archimedes kernel: [    0.474163] pci 0000:05:03.0: PME# disabled
Jun 18 20:02:21 archimedes kernel: [    0.474220] pci 0000:00:1e.0: transparent bridge
Jun 18 20:02:21 archimedes kernel: [    0.474225] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
Jun 18 20:02:21 archimedes kernel: [    0.474231] pci 0000:00:1e.0: bridge 32bit mmio: [0xfd800000-0xfd8fffff]
Jun 18 20:02:21 archimedes kernel: [    0.474239] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xfd700000-0xfd7fffff]
Jun 18 20:02:21 archimedes kernel: [    0.474268] bus 00 -> node 0
Jun 18 20:02:21 archimedes kernel: [    0.474280] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 18 20:02:21 archimedes kernel: [    0.474656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Jun 18 20:02:21 archimedes kernel: [    0.474804] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
Jun 18 20:02:21 archimedes kernel: [    0.474962] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
Jun 18 20:02:21 archimedes kernel: [    0.475110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jun 18 20:02:21 archimedes kernel: [    0.489221] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Jun 18 20:02:21 archimedes kernel: [    0.489385] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jun 18 20:02:21 archimedes kernel: [    0.489547] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jun 18 20:02:21 archimedes kernel: [    0.489708] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 11 12 14 *15)
Jun 18 20:02:21 archimedes kernel: [    0.489869] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 18 20:02:21 archimedes kernel: [    0.490031] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 18 20:02:21 archimedes kernel: [    0.490193] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 18 20:02:21 archimedes kernel: [    0.490357] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Jun 18 20:02:21 archimedes kernel: [    0.490647] ACPI: WMI: Mapper loaded
Jun 18 20:02:21 archimedes kernel: [    0.490704] SCSI subsystem initialized
Jun 18 20:02:21 archimedes kernel: [    0.490704] libata version 3.00 loaded.
Jun 18 20:02:21 archimedes kernel: [    0.490704] usbcore: registered new interface driver usbfs
Jun 18 20:02:21 archimedes kernel: [    0.490704] usbcore: registered new interface driver hub
Jun 18 20:02:21 archimedes kernel: [    0.490704] usbcore: registered new device driver usb
Jun 18 20:02:21 archimedes kernel: [    0.490704] PCI: Using ACPI for IRQ routing
Jun 18 20:02:21 archimedes kernel: [    0.496017] Bluetooth: Core ver 2.13
Jun 18 20:02:21 archimedes kernel: [    0.496040] NET: Registered protocol family 31
Jun 18 20:02:21 archimedes kernel: [    0.496040] Bluetooth: HCI device and connection manager initialized
Jun 18 20:02:21 archimedes kernel: [    0.496040] Bluetooth: HCI socket layer initialized
Jun 18 20:02:21 archimedes kernel: [    0.496040] NET: Registered protocol family 8
Jun 18 20:02:21 archimedes kernel: [    0.496041] NET: Registered protocol family 20
Jun 18 20:02:21 archimedes kernel: [    0.496056] NetLabel: Initializing
Jun 18 20:02:21 archimedes kernel: [    0.496058] NetLabel:  domain hash size = 128
Jun 18 20:02:21 archimedes kernel: [    0.496060] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 18 20:02:21 archimedes kernel: [    0.496088] NetLabel:  unlabeled traffic allowed by default
Jun 18 20:02:21 archimedes kernel: [    0.496171] AppArmor: AppArmor Filesystem Enabled
Jun 18 20:02:21 archimedes kernel: [    0.500019] pnp: PnP ACPI init
Jun 18 20:02:21 archimedes kernel: [    0.500035] ACPI: bus type pnp registered
Jun 18 20:02:21 archimedes kernel: [    0.504309] pnp: PnP ACPI: found 15 devices
Jun 18 20:02:21 archimedes kernel: [    0.504312] ACPI: ACPI bus type pnp unregistered
Jun 18 20:02:21 archimedes kernel: [    0.504317] PnPBIOS: Disabled by ACPI PNP
Jun 18 20:02:21 archimedes kernel: [    0.504329] system 00:01: ioport range 0xb78-0xb7b has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504333] system 00:01: ioport range 0xf78-0xf7b has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504336] system 00:01: ioport range 0xa78-0xa7b has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504339] system 00:01: ioport range 0xe78-0xe7b has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504342] system 00:01: ioport range 0xbbc-0xbbf has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504345] system 00:01: ioport range 0xfbc-0xfbf has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504347] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504350] system 00:01: ioport range 0x294-0x297 has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504353] system 00:01: ioport range 0x800-0x87f has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504356] system 00:01: ioport range 0x880-0x88f has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504368] system 00:0b: ioport range 0x400-0x4bf has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504377] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504388] system 00:0e: iomem range 0xf0000-0xfffff could not be reserved
Jun 18 20:02:21 archimedes kernel: [    0.504392] system 00:0e: iomem range 0xfed00000-0xfed000ff has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504396] system 00:0e: iomem range 0x7fee0000-0x7fefffff could not be reserved
Jun 18 20:02:21 archimedes kernel: [    0.504399] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jun 18 20:02:21 archimedes kernel: [    0.504402] system 00:0e: iomem range 0x100000-0x7fedffff could not be reserved
Jun 18 20:02:21 archimedes kernel: [    0.504406] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504409] system 00:0e: iomem range 0xfed13000-0xfed1dfff has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504412] system 00:0e: iomem range 0xfed20000-0xfed8ffff has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504415] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504418] system 00:0e: iomem range 0xffb00000-0xffb7ffff has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504421] system 00:0e: iomem range 0xfff00000-0xffffffff has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.504425] system 00:0e: iomem range 0xe0000-0xeffff has been reserved
Jun 18 20:02:21 archimedes kernel: [    0.539190] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jun 18 20:02:21 archimedes kernel: [    0.539195] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
Jun 18 20:02:21 archimedes kernel: [    0.539200] pci 0000:00:01.0:   MEM window: 0xf8000000-0xfbffffff
Jun 18 20:02:21 archimedes kernel: [    0.539205] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jun 18 20:02:21 archimedes kernel: [    0.539211] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Jun 18 20:02:21 archimedes kernel: [    0.539215] pci 0000:00:1c.0:   IO window: 0xa000-0xafff
Jun 18 20:02:21 archimedes kernel: [    0.539221] pci 0000:00:1c.0:   MEM window: 0xfd900000-0xfd9fffff
Jun 18 20:02:21 archimedes kernel: [    0.539227] pci 0000:00:1c.0:   PREFETCH window: 0x000000fd600000-0x000000fd6fffff
Jun 18 20:02:21 archimedes kernel: [    0.539235] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Jun 18 20:02:21 archimedes kernel: [    0.539239] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
Jun 18 20:02:21 archimedes kernel: [    0.539245] pci 0000:00:1c.1:   MEM window: 0xfde00000-0xfdefffff
Jun 18 20:02:21 archimedes kernel: [    0.539251] pci 0000:00:1c.1:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Jun 18 20:02:21 archimedes kernel: [    0.539259] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
Jun 18 20:02:21 archimedes kernel: [    0.539262] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
Jun 18 20:02:21 archimedes kernel: [    0.539269] pci 0000:00:1c.5:   MEM window: 0xfdb00000-0xfdcfffff
Jun 18 20:02:21 archimedes kernel: [    0.539274] pci 0000:00:1c.5:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
Jun 18 20:02:21 archimedes kernel: [    0.539282] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Jun 18 20:02:21 archimedes kernel: [    0.539286] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Jun 18 20:02:21 archimedes kernel: [    0.539293] pci 0000:00:1e.0:   MEM window: 0xfd800000-0xfd8fffff
Jun 18 20:02:21 archimedes kernel: [    0.539298] pci 0000:00:1e.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
Jun 18 20:02:21 archimedes kernel: [    0.539315] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 18 20:02:21 archimedes kernel: [    0.539320] pci 0000:00:01.0: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    0.539329] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 18 20:02:21 archimedes kernel: [    0.539335] pci 0000:00:1c.0: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    0.539346] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 18 20:02:21 archimedes kernel: [    0.539351] pci 0000:00:1c.1: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    0.539362] pci 0000:00:1c.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jun 18 20:02:21 archimedes kernel: [    0.539367] pci 0000:00:1c.5: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    0.539375] pci 0000:00:1e.0: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    0.539380] bus: 00 index 0 io port: [0x00-0xffff]
Jun 18 20:02:21 archimedes kernel: [    0.539383] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Jun 18 20:02:21 archimedes kernel: [    0.539386] bus: 01 index 0 io port: [0xb000-0xbfff]
Jun 18 20:02:21 archimedes kernel: [    0.539388] bus: 01 index 1 mmio: [0xf8000000-0xfbffffff]
Jun 18 20:02:21 archimedes kernel: [    0.539391] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
Jun 18 20:02:21 archimedes kernel: [    0.539393] bus: 01 index 3 mmio: [0x0-0x0]
Jun 18 20:02:21 archimedes kernel: [    0.539395] bus: 02 index 0 io port: [0xa000-0xafff]
Jun 18 20:02:21 archimedes kernel: [    0.539398] bus: 02 index 1 mmio: [0xfd900000-0xfd9fffff]
Jun 18 20:02:21 archimedes kernel: [    0.539400] bus: 02 index 2 mmio: [0xfd600000-0xfd6fffff]
Jun 18 20:02:21 archimedes kernel: [    0.539402] bus: 02 index 3 mmio: [0x0-0x0]
Jun 18 20:02:21 archimedes kernel: [    0.539405] bus: 03 index 0 io port: [0xe000-0xefff]
Jun 18 20:02:21 archimedes kernel: [    0.539407] bus: 03 index 1 mmio: [0xfde00000-0xfdefffff]
Jun 18 20:02:21 archimedes kernel: [    0.539410] bus: 03 index 2 mmio: [0xfdd00000-0xfddfffff]
Jun 18 20:02:21 archimedes kernel: [    0.539412] bus: 03 index 3 mmio: [0x0-0x0]
Jun 18 20:02:21 archimedes kernel: [    0.539414] bus: 04 index 0 io port: [0xd000-0xdfff]
Jun 18 20:02:21 archimedes kernel: [    0.539416] bus: 04 index 1 mmio: [0xfdb00000-0xfdcfffff]
Jun 18 20:02:21 archimedes kernel: [    0.539419] bus: 04 index 2 mmio: [0xfda00000-0xfdafffff]
Jun 18 20:02:21 archimedes kernel: [    0.539421] bus: 04 index 3 mmio: [0x0-0x0]
Jun 18 20:02:21 archimedes kernel: [    0.539424] bus: 05 index 0 io port: [0xc000-0xcfff]
Jun 18 20:02:21 archimedes kernel: [    0.539426] bus: 05 index 1 mmio: [0xfd800000-0xfd8fffff]
Jun 18 20:02:21 archimedes kernel: [    0.539428] bus: 05 index 2 mmio: [0xfd700000-0xfd7fffff]
Jun 18 20:02:21 archimedes kernel: [    0.539431] bus: 05 index 3 io port: [0x00-0xffff]
Jun 18 20:02:21 archimedes kernel: [    0.539433] bus: 05 index 4 mmio: [0x000000-0xffffffff]
Jun 18 20:02:21 archimedes kernel: [    0.539441] NET: Registered protocol family 2
Jun 18 20:02:21 archimedes kernel: [    0.552105] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 18 20:02:21 archimedes kernel: [    0.552431] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 18 20:02:21 archimedes kernel: [    0.552771] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 18 20:02:21 archimedes kernel: [    0.552947] TCP: Hash tables configured (established 131072 bind 65536)
Jun 18 20:02:21 archimedes kernel: [    0.552950] TCP reno registered
Jun 18 20:02:21 archimedes kernel: [    0.560135] NET: Registered protocol family 1
Jun 18 20:02:21 archimedes kernel: [    0.560292] checking if image is initramfs... it is
Jun 18 20:02:21 archimedes kernel: [    1.036736] Switched to high resolution mode on CPU 1
Jun 18 20:02:21 archimedes kernel: [    1.040090] Switched to high resolution mode on CPU 0
Jun 18 20:02:21 archimedes kernel: [    1.151990] Freeing initrd memory: 7367k freed
Jun 18 20:02:21 archimedes kernel: [    1.152215] cpufreq: No nForce2 chipset.
Jun 18 20:02:21 archimedes kernel: [    1.152384] audit: initializing netlink socket (disabled)
Jun 18 20:02:21 archimedes kernel: [    1.152407] type=2000 audit(1245369541.148:1): initialized
Jun 18 20:02:21 archimedes kernel: [    1.160342] highmem bounce pool size: 64 pages
Jun 18 20:02:21 archimedes kernel: [    1.160352] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jun 18 20:02:21 archimedes kernel: [    1.161931] VFS: Disk quotas dquot_6.5.1
Jun 18 20:02:21 archimedes kernel: [    1.162006] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 18 20:02:21 archimedes kernel: [    1.162803] fuse init (API version 7.10)
Jun 18 20:02:21 archimedes kernel: [    1.162915] msgmni has been set to 1698
Jun 18 20:02:21 archimedes kernel: [    1.163135] alg: No test for stdrng (krng)
Jun 18 20:02:21 archimedes kernel: [    1.163164] io scheduler noop registered
Jun 18 20:02:21 archimedes kernel: [    1.163167] io scheduler anticipatory registered
Jun 18 20:02:21 archimedes kernel: [    1.163169] io scheduler deadline registered
Jun 18 20:02:21 archimedes kernel: [    1.163188] io scheduler cfq registered (default)
Jun 18 20:02:21 archimedes kernel: [    1.163315] pci 0000:01:00.0: Boot video device
Jun 18 20:02:21 archimedes kernel: [    1.167437] pcieport-driver 0000:00:01.0: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    1.167483] pcieport-driver 0000:00:01.0: found MSI capability
Jun 18 20:02:21 archimedes kernel: [    1.167514] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
Jun 18 20:02:21 archimedes kernel: [    1.167527] pci_express 0000:00:01.0:pcie00: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.167547] pci_express 0000:00:01.0:pcie03: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.167609] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    1.167655] pcieport-driver 0000:00:1c.0: found MSI capability
Jun 18 20:02:21 archimedes kernel: [    1.167687] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
Jun 18 20:02:21 archimedes kernel: [    1.167704] pci_express 0000:00:1c.0:pcie00: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.167722] pci_express 0000:00:1c.0:pcie02: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.167739] pci_express 0000:00:1c.0:pcie03: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.167815] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    1.167861] pcieport-driver 0000:00:1c.1: found MSI capability
Jun 18 20:02:21 archimedes kernel: [    1.167893] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
Jun 18 20:02:21 archimedes kernel: [    1.167909] pci_express 0000:00:1c.1:pcie00: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.167927] pci_express 0000:00:1c.1:pcie02: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.167944] pci_express 0000:00:1c.1:pcie03: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.168022] pcieport-driver 0000:00:1c.5: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    1.168068] pcieport-driver 0000:00:1c.5: found MSI capability
Jun 18 20:02:21 archimedes kernel: [    1.168100] pcieport-driver 0000:00:1c.5: irq 2300 for MSI/MSI-X
Jun 18 20:02:21 archimedes kernel: [    1.168115] pci_express 0000:00:1c.5:pcie00: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.168133] pci_express 0000:00:1c.5:pcie02: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.168151] pci_express 0000:00:1c.5:pcie03: allocate port service
Jun 18 20:02:21 archimedes kernel: [    1.168247] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 18 20:02:21 archimedes kernel: [    1.168556] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 18 20:02:21 archimedes kernel: [    1.168723] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Jun 18 20:02:21 archimedes kernel: [    1.168727] ACPI: Power Button (FF) [PWRF]
Jun 18 20:02:21 archimedes kernel: [    1.168786] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Jun 18 20:02:21 archimedes kernel: [    1.168790] ACPI: Power Button (CM) [PWRB]
Jun 18 20:02:21 archimedes kernel: [    1.168864] fan PNP0C0B:00: registered as cooling_device0
Jun 18 20:02:21 archimedes kernel: [    1.168871] ACPI: Fan [FAN] (on)
Jun 18 20:02:21 archimedes kernel: [    1.169450] ACPI Error (psparse-0524): Method parse/execution failed [\_PR_.CPU0._PDC] (Node f6c19408), AE_ALREADY_EXISTS
Jun 18 20:02:21 archimedes kernel: [    1.169462] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
Jun 18 20:02:21 archimedes kernel: [    1.169523] processor ACPI_CPU:00: registered as cooling_device1
Jun 18 20:02:21 archimedes kernel: [    1.169777] ACPI: SSDT 7FEE8710, 00CE (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
Jun 18 20:02:21 archimedes kernel: [    1.170118] processor ACPI_CPU:01: registered as cooling_device2
Jun 18 20:02:21 archimedes kernel: [    1.173207] thermal LNXTHERM:01: registered as thermal_zone0
Jun 18 20:02:21 archimedes kernel: [    1.173629] ACPI: Thermal Zone [THRM] (36 C)
Jun 18 20:02:21 archimedes kernel: [    1.173696] isapnp: Scanning for PnP cards...
Jun 18 20:02:21 archimedes kernel: [    1.525404] isapnp: No Plug & Play device found
Jun 18 20:02:21 archimedes kernel: [    1.532686] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jun 18 20:02:21 archimedes kernel: [    1.532802] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 18 20:02:21 archimedes kernel: [    1.533227] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 18 20:02:21 archimedes kernel: [    1.534310] brd: module loaded
Jun 18 20:02:21 archimedes kernel: [    1.534737] loop: module loaded
Jun 18 20:02:21 archimedes kernel: [    1.534825] Fixed MDIO Bus: probed
Jun 18 20:02:21 archimedes kernel: [    1.534832] PPP generic driver version 2.4.2
Jun 18 20:02:21 archimedes kernel: [    1.534902] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jun 18 20:02:21 archimedes kernel: [    1.534938] Driver 'sd' needs updating - please use bus_type methods
Jun 18 20:02:21 archimedes kernel: [    1.534950] Driver 'sr' needs updating - please use bus_type methods
Jun 18 20:02:21 archimedes kernel: [    1.534998] ahci 0000:03:00.0: version 3.0
Jun 18 20:02:21 archimedes kernel: [    1.535015] ahci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 18 20:02:21 archimedes kernel: [    1.535059] ahci 0000:03:00.0: JMB361 has only one port, port_map 0x3 -> 0x1
Jun 18 20:02:21 archimedes kernel: [    1.548042] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x1 impl SATA mode
Jun 18 20:02:21 archimedes kernel: [    1.548047] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Jun 18 20:02:21 archimedes kernel: [    1.548056] ahci 0000:03:00.0: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    1.548206] scsi0 : ahci
Jun 18 20:02:21 archimedes kernel: [    1.548324] scsi1 : ahci
Jun 18 20:02:21 archimedes kernel: [    1.548426] ata1: SATA max UDMA/133 abar m8192@0xfdefe000 port 0xfdefe100 irq 17
Jun 18 20:02:21 archimedes kernel: [    1.548429] ata2: DUMMY
Jun 18 20:02:21 archimedes kernel: [    1.868037] ata1: SATA link down (SStatus 0 SControl 300)
Jun 18 20:02:21 archimedes kernel: [    1.884115] ata_piix 0000:00:1f.1: version 2.12
Jun 18 20:02:21 archimedes kernel: [    1.884127] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 18 20:02:21 archimedes kernel: [    1.884168] ata_piix 0000:00:1f.1: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    1.884248] scsi2 : ata_piix
Jun 18 20:02:21 archimedes kernel: [    1.884332] scsi3 : ata_piix
Jun 18 20:02:21 archimedes kernel: [    1.885089] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfb00 irq 14
Jun 18 20:02:21 archimedes kernel: [    1.885092] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfb08 irq 15
Jun 18 20:02:21 archimedes kernel: [    2.040122] ata4: port disabled. ignoring.
Jun 18 20:02:21 archimedes kernel: [    2.040152] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 18 20:02:21 archimedes kernel: [    2.040157] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Jun 18 20:02:21 archimedes kernel: [    2.040203] ata_piix 0000:00:1f.2: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    2.040271] scsi4 : ata_piix
Jun 18 20:02:21 archimedes kernel: [    2.040354] scsi5 : ata_piix
Jun 18 20:02:21 archimedes kernel: [    2.041184] ata5: SATA max UDMA/133 cmd 0xfa00 ctl 0xf900 bmdma 0xf600 irq 19
Jun 18 20:02:21 archimedes kernel: [    2.041188] ata6: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf608 irq 19
Jun 18 20:02:21 archimedes kernel: [    2.368393] ata6.00: ATA-7: ST3250310AS, 3.AAC, max UDMA/133
Jun 18 20:02:21 archimedes kernel: [    2.368398] ata6.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 18 20:02:21 archimedes kernel: [    2.384429] ata6.00: configured for UDMA/133
Jun 18 20:02:21 archimedes kernel: [    2.384585] scsi 5:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
Jun 18 20:02:21 archimedes kernel: [    2.384710] sd 5:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Jun 18 20:02:21 archimedes kernel: [    2.384735] sd 5:0:0:0: [sda] Write Protect is off
Jun 18 20:02:21 archimedes kernel: [    2.384738] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 18 20:02:21 archimedes kernel: [    2.384777] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 18 20:02:21 archimedes kernel: [    2.384857] sd 5:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Jun 18 20:02:21 archimedes kernel: [    2.384879] sd 5:0:0:0: [sda] Write Protect is off
Jun 18 20:02:21 archimedes kernel: [    2.384882] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 18 20:02:21 archimedes kernel: [    2.384920] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 18 20:02:21 archimedes kernel: [    2.384925]  sda: sda1 sda2 < sda5 sda6 >
Jun 18 20:02:21 archimedes kernel: [    2.434203] sd 5:0:0:0: [sda] Attached SCSI disk
Jun 18 20:02:21 archimedes kernel: [    2.434258] sd 5:0:0:0: Attached scsi generic sg0 type 0
Jun 18 20:02:21 archimedes kernel: [    2.434749] pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)
Jun 18 20:02:21 archimedes kernel: [    2.434757] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Jun 18 20:02:21 archimedes kernel: [    2.434798] pata_jmicron 0000:03:00.1: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    2.434898] scsi6 : pata_jmicron
Jun 18 20:02:21 archimedes kernel: [    2.435024] scsi7 : pata_jmicron
Jun 18 20:02:21 archimedes kernel: [    2.435110] ata7: PATA max UDMA/100 cmd 0xef00 ctl 0xee00 bmdma 0xeb00 irq 18
Jun 18 20:02:21 archimedes kernel: [    2.435115] ata8: PATA max UDMA/100 cmd 0xed00 ctl 0xec00 bmdma 0xeb08 irq 18
Jun 18 20:02:21 archimedes kernel: [    2.605014] ata7.01: ATAPI: _NEC CD-RW NR-9300A, 105B, max UDMA/33
Jun 18 20:02:21 archimedes kernel: [    2.621019] ata7.01: configured for UDMA/33
Jun 18 20:02:21 archimedes kernel: [    2.788692] scsi 6:0:1:0: CD-ROM            _NEC     CD-RW NR-9300A   105B PQ: 0 ANSI: 5
Jun 18 20:02:21 archimedes kernel: [    2.792036] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Jun 18 20:02:21 archimedes kernel: [    2.792041] Uniform CD-ROM driver Revision: 3.20
Jun 18 20:02:21 archimedes kernel: [    2.792165] sr 6:0:1:0: Attached scsi CD-ROM sr0
Jun 18 20:02:21 archimedes kernel: [    2.792213] sr 6:0:1:0: Attached scsi generic sg1 type 5
Jun 18 20:02:21 archimedes kernel: [    2.792608] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 18 20:02:21 archimedes kernel: [    2.792635] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 18 20:02:21 archimedes kernel: [    2.792651] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    2.792656] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 18 20:02:21 archimedes kernel: [    2.792723] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jun 18 20:02:21 archimedes kernel: [    2.796630] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
Jun 18 20:02:21 archimedes kernel: [    2.796646] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
Jun 18 20:02:21 archimedes kernel: [    2.812022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jun 18 20:02:21 archimedes kernel: [    2.812128] usb usb1: configuration #1 chosen from 1 choice
Jun 18 20:02:21 archimedes kernel: [    2.812164] hub 1-0:1.0: USB hub found
Jun 18 20:02:21 archimedes kernel: [    2.812174] hub 1-0:1.0: 8 ports detected
Jun 18 20:02:21 archimedes kernel: [    2.812321] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 18 20:02:21 archimedes kernel: [    2.812342] uhci_hcd: USB Universal Host Controller Interface driver
Jun 18 20:02:21 archimedes kernel: [    2.812369] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 18 20:02:21 archimedes kernel: [    2.812377] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    2.812381] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 18 20:02:21 archimedes kernel: [    2.812436] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jun 18 20:02:21 archimedes kernel: [    2.812463] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
Jun 18 20:02:21 archimedes kernel: [    2.812554] usb usb2: configuration #1 chosen from 1 choice
Jun 18 20:02:21 archimedes kernel: [    2.812588] hub 2-0:1.0: USB hub found
Jun 18 20:02:21 archimedes kernel: [    2.812597] hub 2-0:1.0: 2 ports detected
Jun 18 20:02:21 archimedes kernel: [    2.812705] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 18 20:02:21 archimedes kernel: [    2.812712] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    2.812716] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun 18 20:02:21 archimedes kernel: [    2.812768] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jun 18 20:02:21 archimedes kernel: [    2.812795] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
Jun 18 20:02:21 archimedes kernel: [    2.812884] usb usb3: configuration #1 chosen from 1 choice
Jun 18 20:02:21 archimedes kernel: [    2.812916] hub 3-0:1.0: USB hub found
Jun 18 20:02:21 archimedes kernel: [    2.812925] hub 3-0:1.0: 2 ports detected
Jun 18 20:02:21 archimedes kernel: [    2.813029] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 18 20:02:21 archimedes kernel: [    2.813036] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    2.813040] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 18 20:02:21 archimedes kernel: [    2.813096] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jun 18 20:02:21 archimedes kernel: [    2.813122] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
Jun 18 20:02:21 archimedes kernel: [    2.813214] usb usb4: configuration #1 chosen from 1 choice
Jun 18 20:02:21 archimedes kernel: [    2.813246] hub 4-0:1.0: USB hub found
Jun 18 20:02:21 archimedes kernel: [    2.813255] hub 4-0:1.0: 2 ports detected
Jun 18 20:02:21 archimedes kernel: [    2.813360] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Jun 18 20:02:21 archimedes kernel: [    2.813368] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    2.813371] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jun 18 20:02:21 archimedes kernel: [    2.813429] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jun 18 20:02:21 archimedes kernel: [    2.813463] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
Jun 18 20:02:21 archimedes kernel: [    2.813554] usb usb5: configuration #1 chosen from 1 choice
Jun 18 20:02:21 archimedes kernel: [    2.813587] hub 5-0:1.0: USB hub found
Jun 18 20:02:21 archimedes kernel: [    2.813596] hub 5-0:1.0: 2 ports detected
Jun 18 20:02:21 archimedes kernel: [    2.813758] usbcore: registered new interface driver libusual
Jun 18 20:02:21 archimedes kernel: [    2.813805] usbcore: registered new interface driver usbserial
Jun 18 20:02:21 archimedes kernel: [    2.813819] USB Serial support registered for generic
Jun 18 20:02:21 archimedes kernel: [    2.813840] usbcore: registered new interface driver usbserial_generic
Jun 18 20:02:21 archimedes kernel: [    2.813843] usbserial: USB Serial Driver core
Jun 18 20:02:21 archimedes kernel: [    2.813909] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 18 20:02:21 archimedes kernel: [    2.816557] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 18 20:02:21 archimedes kernel: [    2.816567] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 18 20:02:21 archimedes kernel: [    2.820075] mice: PS/2 mouse device common for all mice
Jun 18 20:02:21 archimedes kernel: [    2.832121] rtc_cmos 00:03: RTC can wake from S4
Jun 18 20:02:21 archimedes kernel: [    2.832162] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 18 20:02:21 archimedes kernel: [    2.832192] rtc0: alarms up to one month, 242 bytes nvram
Jun 18 20:02:21 archimedes kernel: [    2.832273] device-mapper: uevent: version 1.0.3
Jun 18 20:02:21 archimedes kernel: [    2.832385] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Jun 18 20:02:21 archimedes kernel: [    2.832506] device-mapper: multipath: version 1.0.5 loaded
Jun 18 20:02:21 archimedes kernel: [    2.832511] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 18 20:02:21 archimedes kernel: [    2.832618] EISA: Probing bus 0 at eisa.0
Jun 18 20:02:21 archimedes kernel: [    2.832655] EISA: Detected 0 cards.
Jun 18 20:02:21 archimedes kernel: [    2.832738] cpuidle: using governor ladder
Jun 18 20:02:21 archimedes kernel: [    2.832743] cpuidle: using governor menu
Jun 18 20:02:21 archimedes kernel: [    2.833381] TCP cubic registered
Jun 18 20:02:21 archimedes kernel: [    2.833471] NET: Registered protocol family 10
Jun 18 20:02:21 archimedes kernel: [    2.834062] lo: Disabled Privacy Extensions
Jun 18 20:02:21 archimedes kernel: [    2.834534] NET: Registered protocol family 17
Jun 18 20:02:21 archimedes kernel: [    2.834557] Bluetooth: L2CAP ver 2.11
Jun 18 20:02:21 archimedes kernel: [    2.834560] Bluetooth: L2CAP socket layer initialized
Jun 18 20:02:21 archimedes kernel: [    2.834564] Bluetooth: SCO (Voice Link) ver 0.6
Jun 18 20:02:21 archimedes kernel: [    2.834566] Bluetooth: SCO socket layer initialized
Jun 18 20:02:21 archimedes kernel: [    2.834609] Bluetooth: RFCOMM socket layer initialized
Jun 18 20:02:21 archimedes kernel: [    2.834616] Bluetooth: RFCOMM TTY layer initialized
Jun 18 20:02:21 archimedes kernel: [    2.834618] Bluetooth: RFCOMM ver 1.10
Jun 18 20:02:21 archimedes kernel: [    2.835515] Using IPI No-Shortcut mode
Jun 18 20:02:21 archimedes kernel: [    2.835602] registered taskstats version 1
Jun 18 20:02:21 archimedes kernel: [    2.835751]   Magic number: 13:236:1010
Jun 18 20:02:21 archimedes kernel: [    2.835831] rtc_cmos 00:03: setting system clock to 2009-06-18 23:59:03 UTC (1245369543)
Jun 18 20:02:21 archimedes kernel: [    2.835835] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 18 20:02:21 archimedes kernel: [    2.835837] EDD information not available.
Jun 18 20:02:21 archimedes kernel: [    2.836165] Freeing unused kernel memory: 532k freed
Jun 18 20:02:21 archimedes kernel: [    2.836322] Write protecting the kernel text: 4128k
Jun 18 20:02:21 archimedes kernel: [    2.836380] Write protecting the kernel read-only data: 1532k
Jun 18 20:02:21 archimedes kernel: [    2.850045] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jun 18 20:02:21 archimedes kernel: [    3.123245] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
Jun 18 20:02:21 archimedes kernel: [    3.123250] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Jun 18 20:02:21 archimedes kernel: [    3.123334] e1000e 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 18 20:02:21 archimedes kernel: [    3.123349] e1000e 0000:04:00.0: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    3.123585] e1000e 0000:04:00.0: irq 2299 for MSI/MSI-X
Jun 18 20:02:21 archimedes kernel: [    3.197715] FDC 0 is a post-1991 82077
Jun 18 20:02:21 archimedes kernel: [    3.236957] 0000:04:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:db:62:df:57
Jun 18 20:02:21 archimedes kernel: [    3.236962] 0000:04:00.0: eth0: Intel(R) PRO/1000 Network Connection
Jun 18 20:02:21 archimedes kernel: [    3.236979] 0000:04:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
Jun 18 20:02:21 archimedes kernel: [    3.260104] ohci1394 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 18 20:02:21 archimedes kernel: [    3.260115] ohci1394 0000:05:03.0: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    3.312931] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fd8ff000-fd8ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun 18 20:02:21 archimedes kernel: [    3.317184] usb 3-1: new low speed USB device using uhci_hcd and address 2
Jun 18 20:02:21 archimedes kernel: [    3.489028] usb 3-1: configuration #1 chosen from 1 choice
Jun 18 20:02:21 archimedes kernel: [    3.621432] usbcore: registered new interface driver hiddev
Jun 18 20:02:21 archimedes kernel: [    3.635356] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4
Jun 18 20:02:21 archimedes kernel: [    3.656772] generic-usb 0003:0461:4D15.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-1/input0
Jun 18 20:02:21 archimedes kernel: [    3.656799] usbcore: registered new interface driver usbhid
Jun 18 20:02:21 archimedes kernel: [    3.656805] usbhid: v2.6:USB HID core driver
Jun 18 20:02:21 archimedes kernel: [    3.752407] PM: Starting manual resume from disk
Jun 18 20:02:21 archimedes kernel: [    3.752412] PM: Resume from partition 8:6
Jun 18 20:02:21 archimedes kernel: [    3.752414] PM: Checking hibernation image.
Jun 18 20:02:21 archimedes kernel: [    3.752564] PM: Resume from disk failed.
Jun 18 20:02:21 archimedes kernel: [    3.792990] kjournald starting.  Commit interval 5 seconds
Jun 18 20:02:21 archimedes kernel: [    3.793008] EXT3-fs: mounted filesystem with ordered data mode.
Jun 18 20:02:21 archimedes kernel: [    4.592235] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00010811d0]
Jun 18 20:02:21 archimedes kernel: [    7.262857] udev: starting version 141
Jun 18 20:02:21 archimedes kernel: [    7.353029] EDAC MC: Ver: 2.1.0 Apr 17 2009
Jun 18 20:02:21 archimedes kernel: [    7.378846] EDAC i82975x: ECC disabled on both channels.
Jun 18 20:02:21 archimedes kernel: [    7.445637] parport_pc 00:08: reported by Plug and Play ACPI
Jun 18 20:02:21 archimedes kernel: [    7.445704] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 18 20:02:21 archimedes kernel: [    7.491586] iTCO_vendor_support: vendor-support=0
Jun 18 20:02:21 archimedes kernel: [    7.504647] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Jun 18 20:02:21 archimedes kernel: [    7.504912] iTCO_wdt: Found a ICH7DH TCO device (Version=2, TCOBASE=0x0460)
Jun 18 20:02:21 archimedes kernel: [    7.505046] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun 18 20:02:21 archimedes kernel: [    7.773905] input: PC Speaker as /devices/platform/pcspkr/input/input5
Jun 18 20:02:21 archimedes kernel: [    8.036741] ppdev: user-space parallel port driver
Jun 18 20:02:21 archimedes kernel: [    8.213928] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 18 20:02:21 archimedes kernel: [    8.214078] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun 18 20:02:21 archimedes kernel: [    8.245926] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jun 18 20:02:21 archimedes kernel: [    8.435343] lp0: using parport0 (interrupt-driven).
Jun 18 20:02:21 archimedes kernel: [    8.532991] Adding 1951856k swap on /dev/sda6.  Priority:-1 extents:1 across:1951856k
Jun 18 20:02:21 archimedes kernel: [    9.080196] EXT3 FS on sda1, internal journal
Jun 18 20:02:21 archimedes kernel: [  199.597419] kjournald starting.  Commit interval 5 seconds
Jun 18 20:02:21 archimedes kernel: [  199.597847] EXT3 FS on sda5, internal journal
Jun 18 20:02:21 archimedes kernel: [  199.597856] EXT3-fs: mounted filesystem with ordered data mode.
Jun 18 20:02:21 archimedes kernel: [  199.845325] type=1505 audit(1245369740.508:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3483
Jun 18 20:02:21 archimedes kernel: [  199.896148] type=1505 audit(1245369740.560:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=3487
Jun 18 20:02:21 archimedes kernel: [  199.896250] type=1505 audit(1245369740.560:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=3487
Jun 18 20:02:21 archimedes kernel: [  199.896300] type=1505 audit(1245369740.560:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=3487
Jun 18 20:02:21 archimedes kernel: [  199.896342] type=1505 audit(1245369740.560:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=3487
Jun 18 20:02:21 archimedes kernel: [  200.034734] type=1505 audit(1245369740.696:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3492
Jun 18 20:02:21 archimedes kernel: [  200.034904] type=1505 audit(1245369740.696:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3492
Jun 18 20:02:21 archimedes kernel: [  200.065750] type=1505 audit(1245369740.728:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=3496
Jun 18 20:02:23 archimedes kernel: [  202.349714] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 18 20:02:23 archimedes kernel: [  202.349720] Bluetooth: BNEP filters: protocol multicast
Jun 18 20:02:23 archimedes kernel: [  202.370802] Bridge firewalling registered
Jun 18 20:02:28 archimedes kernel: [  207.356373] e1000e 0000:04:00.0: irq 2299 for MSI/MSI-X
Jun 18 20:02:28 archimedes kernel: [  207.412151] e1000e 0000:04:00.0: irq 2299 for MSI/MSI-X
Jun 18 20:02:28 archimedes kernel: [  207.413329] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 18 20:02:29 archimedes kernel: [  208.994442] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:29 archimedes kernel: [  208.994447] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:29 archimedes kernel: [  208.994671] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 18 20:02:30 archimedes kernel: [  209.804142] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:32 archimedes kernel: [  211.554441] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:32 archimedes kernel: [  211.554445] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:33 archimedes kernel: [  212.424141] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:34 archimedes kernel: [  214.182440] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:34 archimedes kernel: [  214.182445] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:35 archimedes kernel: [  215.044140] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:37 archimedes kernel: [  216.750442] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:37 archimedes kernel: [  216.750446] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:38 archimedes kernel: [  217.664140] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:40 archimedes kernel: [  219.366444] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:40 archimedes kernel: [  219.366449] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:40 archimedes kernel: [  219.860022] eth0: no IPv6 routers present
Jun 18 20:02:40 archimedes kernel: [  220.288140] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:42 archimedes kernel: [  221.986444] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:42 archimedes kernel: [  221.986449] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:43 archimedes kernel: [  222.908142] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:45 archimedes kernel: [  224.606532] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:45 archimedes kernel: [  224.606538] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:46 archimedes kernel: [  225.528143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:47 archimedes kernel: [  227.218452] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:47 archimedes kernel: [  227.218457] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:48 archimedes kernel: [  228.148141] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:50 archimedes kernel: [  229.854463] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:50 archimedes kernel: [  229.854469] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:51 archimedes kernel: [  230.768158] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:53 archimedes kernel: [  232.546445] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:53 archimedes kernel: [  232.546450] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:54 archimedes kernel: [  233.392147] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:55 archimedes kernel: [  235.094469] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:55 archimedes kernel: [  235.094474] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:56 archimedes kernel: [  235.740315] 0000:04:00.0: eth0: Link is Down
Jun 18 20:02:58 archimedes kernel: [  237.494449] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:02:58 archimedes kernel: [  237.494454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:02:58 archimedes kernel: [  238.320153] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:00 archimedes kernel: [  240.022454] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:00 archimedes kernel: [  240.022459] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:01 archimedes kernel: [  240.940141] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:03 archimedes kernel: [  242.642451] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:03 archimedes kernel: [  242.642456] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:04 archimedes kernel: [  243.560143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:05 archimedes kernel: [  245.270444] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:05 archimedes kernel: [  245.270449] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:06 archimedes kernel: [  246.180145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:08 archimedes kernel: [  247.874457] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:08 archimedes kernel: [  247.874462] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:09 archimedes kernel: [  248.804143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:11 archimedes kernel: [  250.490460] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:11 archimedes kernel: [  250.490467] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:11 archimedes kernel: [  251.320144] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:13 archimedes kernel: [  253.046458] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:13 archimedes kernel: [  253.046463] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:14 archimedes kernel: [  253.940144] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:16 archimedes kernel: [  255.702445] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:16 archimedes kernel: [  255.702449] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:17 archimedes kernel: [  256.560142] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:18 archimedes kernel: [  258.294444] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:18 archimedes kernel: [  258.294449] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:19 archimedes kernel: [  259.180144] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:21 archimedes kernel: [  260.874447] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:21 archimedes kernel: [  260.874452] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:22 archimedes kernel: [  261.804212] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:24 archimedes kernel: [  263.494445] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:24 archimedes kernel: [  263.494450] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:25 archimedes kernel: [  264.424147] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:26 archimedes kernel: [  266.150446] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:26 archimedes kernel: [  266.150452] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:27 archimedes kernel: [  266.760145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:29 archimedes kernel: [  268.518448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:29 archimedes kernel: [  268.518454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:30 archimedes kernel: [  269.352145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:31 archimedes kernel: [  271.138454] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:31 archimedes kernel: [  271.138460] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:32 archimedes kernel: [  271.972144] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:34 archimedes kernel: [  273.666448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:34 archimedes kernel: [  273.666454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:34 archimedes kernel: [  274.180149] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:36 archimedes kernel: [  275.894449] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:36 archimedes kernel: [  275.894454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:37 archimedes kernel: [  276.792152] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:39 archimedes kernel: [  278.494448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:39 archimedes kernel: [  278.494454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:40 archimedes kernel: [  279.416149] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:41 archimedes kernel: [  281.166448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:41 archimedes kernel: [  281.166454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:42 archimedes kernel: [  282.036164] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:44 archimedes kernel: [  283.770447] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:44 archimedes kernel: [  283.770453] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:45 archimedes kernel: [  284.656146] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:47 archimedes kernel: [  286.362444] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:47 archimedes kernel: [  286.362449] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:47 archimedes kernel: [  287.276152] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:49 archimedes kernel: [  289.106451] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:49 archimedes kernel: [  289.106456] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:50 archimedes kernel: [  290.004203] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:52 archimedes kernel: [  291.702518] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:52 archimedes kernel: [  291.702528] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:53 archimedes kernel: [  292.624143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:54 archimedes kernel: [  294.318465] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:54 archimedes kernel: [  294.318471] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:55 archimedes kernel: [  295.244144] 0000:04:00.0: eth0: Link is Down
Jun 18 20:03:57 archimedes kernel: [  296.966451] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:03:57 archimedes kernel: [  296.966456] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:03:58 archimedes kernel: [  297.868154] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:00 archimedes kernel: [  299.662450] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:00 archimedes kernel: [  299.662455] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:01 archimedes kernel: [  300.488149] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:02 archimedes kernel: [  302.226450] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:02 archimedes kernel: [  302.226456] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:03 archimedes kernel: [  303.108153] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:05 archimedes kernel: [  304.806454] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:05 archimedes kernel: [  304.806459] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:06 archimedes kernel: [  305.728143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:08 archimedes kernel: [  307.454448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:08 archimedes kernel: [  307.454454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:09 archimedes kernel: [  308.348154] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:10 archimedes kernel: [  310.146454] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:10 archimedes kernel: [  310.146459] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:11 archimedes kernel: [  310.972144] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:13 archimedes kernel: [  312.674444] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:13 archimedes kernel: [  312.674449] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:14 archimedes kernel: [  313.384154] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:15 archimedes kernel: [  315.070456] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:15 archimedes kernel: [  315.070462] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:16 archimedes kernel: [  315.900155] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:18 archimedes kernel: [  317.586447] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:18 archimedes kernel: [  317.586452] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:19 archimedes kernel: [  318.416151] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:20 archimedes kernel: [  320.106448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:20 archimedes kernel: [  320.106453] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:21 archimedes kernel: [  320.932145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:23 archimedes kernel: [  322.678448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:23 archimedes kernel: [  322.678454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:23 archimedes kernel: [  323.328142] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:25 archimedes kernel: [  324.934448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:25 archimedes kernel: [  324.934454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:26 archimedes kernel: [  325.744147] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:28 archimedes kernel: [  327.366455] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:28 archimedes kernel: [  327.366460] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:28 archimedes kernel: [  328.268143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:30 archimedes kernel: [  329.958453] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:30 archimedes kernel: [  329.958458] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:31 archimedes kernel: [  330.888147] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:33 archimedes kernel: [  332.714447] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:33 archimedes kernel: [  332.714453] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:34 archimedes kernel: [  333.616146] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:35 archimedes kernel: [  335.306465] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:35 archimedes kernel: [  335.306471] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:36 archimedes kernel: [  336.236147] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:38 archimedes kernel: [  337.982448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:38 archimedes kernel: [  337.982453] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:39 archimedes kernel: [  338.856153] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:41 archimedes kernel: [  340.594447] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:41 archimedes kernel: [  340.594452] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:42 archimedes kernel: [  341.480143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:43 archimedes kernel: [  343.174448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:43 archimedes kernel: [  343.174454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:44 archimedes kernel: [  344.100156] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:46 archimedes kernel: [  345.794449] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:46 archimedes kernel: [  345.794455] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:46 archimedes kernel: [  346.112140] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:48 archimedes kernel: [  347.842453] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:48 archimedes kernel: [  347.842458] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:49 archimedes kernel: [  348.712143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:51 archimedes kernel: [  350.446446] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:51 archimedes kernel: [  350.446451] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:52 archimedes kernel: [  351.332143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:53 archimedes kernel: [  353.118447] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:53 archimedes kernel: [  353.118453] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:54 archimedes kernel: [  353.956143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:56 archimedes kernel: [  355.806451] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:56 archimedes kernel: [  355.806456] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:57 archimedes kernel: [  356.680147] 0000:04:00.0: eth0: Link is Down
Jun 18 20:04:59 archimedes kernel: [  358.378448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:04:59 archimedes kernel: [  358.378454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:04:59 archimedes kernel: [  359.300145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:01 archimedes kernel: [  360.998450] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:01 archimedes kernel: [  360.998455] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:02 archimedes kernel: [  361.920145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:04 archimedes kernel: [  363.774446] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:04 archimedes kernel: [  363.774452] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:05 archimedes kernel: [  364.648148] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:07 archimedes kernel: [  366.386447] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:07 archimedes kernel: [  366.386452] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:07 archimedes kernel: [  367.268143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:09 archimedes kernel: [  368.986450] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:09 archimedes kernel: [  368.986456] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:10 archimedes kernel: [  369.888145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:12 archimedes kernel: [  371.586448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:12 archimedes kernel: [  371.586454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:13 archimedes kernel: [  372.512144] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:14 archimedes kernel: [  374.214449] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:14 archimedes kernel: [  374.214454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:15 archimedes kernel: [  375.132154] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:17 archimedes kernel: [  376.854453] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:17 archimedes kernel: [  376.854459] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:18 archimedes kernel: [  377.752145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:20 archimedes kernel: [  379.454449] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:20 archimedes kernel: [  379.454454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:21 archimedes kernel: [  380.372143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:22 archimedes kernel: [  382.110452] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:22 archimedes kernel: [  382.110457] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:23 archimedes kernel: [  382.996142] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:25 archimedes kernel: [  384.814448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:25 archimedes kernel: [  384.814454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:26 archimedes kernel: [  385.616150] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:27 archimedes kernel: [  387.302456] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:27 archimedes kernel: [  387.302461] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:28 archimedes kernel: [  388.236145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:30 archimedes kernel: [  389.958456] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:30 archimedes kernel: [  389.958461] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:31 archimedes kernel: [  390.856177] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:33 archimedes kernel: [  392.578448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:33 archimedes kernel: [  392.578454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:34 archimedes kernel: [  393.480142] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:35 archimedes kernel: [  395.170471] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:35 archimedes kernel: [  395.170477] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:36 archimedes kernel: [  396.100146] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:38 archimedes kernel: [  397.790450] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:38 archimedes kernel: [  397.790456] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:39 archimedes kernel: [  398.616146] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:40 archimedes kernel: [  400.306453] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:40 archimedes kernel: [  400.306459] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:41 archimedes kernel: [  401.236143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:43 archimedes kernel: [  402.926448] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:43 archimedes kernel: [  402.926454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:44 archimedes kernel: [  403.713995] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:46 archimedes kernel: [  405.370543] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:46 archimedes kernel: [  405.370551] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:46 archimedes kernel: [  406.268154] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:48 archimedes kernel: [  407.962571] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:48 archimedes kernel: [  407.962579] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:49 archimedes kernel: [  408.888144] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:51 archimedes kernel: [  410.634449] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:51 archimedes kernel: [  410.634454] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:52 archimedes kernel: [  411.512143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:53 archimedes kernel: [  413.298454] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:53 archimedes kernel: [  413.298459] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:54 archimedes kernel: [  414.132143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:55 archimedes kernel: [  414.556027] usb 5-2: new full speed USB device using uhci_hcd and address 2
Jun 18 20:05:55 archimedes kernel: [  414.714201] usb 5-2: configuration #1 chosen from 1 choice
Jun 18 20:05:55 archimedes kernel: [  414.759037] Initializing USB Mass Storage driver...
Jun 18 20:05:55 archimedes kernel: [  414.759230] scsi8 : SCSI emulation for USB Mass Storage devices
Jun 18 20:05:55 archimedes kernel: [  414.759917] usb-storage: device found at 2
Jun 18 20:05:55 archimedes kernel: [  414.759923] usb-storage: waiting for device to settle before scanning
Jun 18 20:05:55 archimedes kernel: [  414.759952] usbcore: registered new interface driver usb-storage
Jun 18 20:05:55 archimedes kernel: [  414.759961] USB Mass Storage support registered.
Jun 18 20:05:56 archimedes kernel: [  415.882469] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:56 archimedes kernel: [  415.882474] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:05:57 archimedes kernel: [  416.752145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:05:59 archimedes kernel: [  418.446452] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:05:59 archimedes kernel: [  418.446458] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:00 archimedes kernel: [  419.372143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:00 archimedes kernel: [  419.756865] usb-storage: device scan complete
Jun 18 20:06:00 archimedes kernel: [  419.762829] scsi 8:0:0:0: Direct-Access     USB NAND FLASH DISK       0.30 PQ: 0 ANSI: 2
Jun 18 20:06:00 archimedes kernel: [  419.826622] sd 8:0:0:0: [sdb] 64000 512-byte hardware sectors: (32.7 MB/31.2 MiB)
Jun 18 20:06:00 archimedes kernel: [  419.829591] sd 8:0:0:0: [sdb] Write Protect is off
Jun 18 20:06:00 archimedes kernel: [  419.829596] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
Jun 18 20:06:00 archimedes kernel: [  419.829600] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jun 18 20:06:00 archimedes kernel: [  419.841590] sd 8:0:0:0: [sdb] 64000 512-byte hardware sectors: (32.7 MB/31.2 MiB)
Jun 18 20:06:00 archimedes kernel: [  419.846604] sd 8:0:0:0: [sdb] Write Protect is off
Jun 18 20:06:00 archimedes kernel: [  419.846611] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
Jun 18 20:06:00 archimedes kernel: [  419.846614] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Jun 18 20:06:00 archimedes kernel: [  419.846622]  sdb: sdb1
Jun 18 20:06:00 archimedes kernel: [  419.853879] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Jun 18 20:06:00 archimedes kernel: [  419.854023] sd 8:0:0:0: Attached scsi generic sg2 type 0
Jun 18 20:06:01 archimedes kernel: [  421.066619] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:01 archimedes kernel: [  421.066626] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:02 archimedes kernel: [  421.456148] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:03 archimedes kernel: [  423.070449] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:03 archimedes kernel: [  423.070455] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:04 archimedes kernel: [  423.984143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:06 archimedes kernel: [  425.770454] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:06 archimedes kernel: [  425.770460] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:07 archimedes kernel: [  426.608154] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:09 archimedes kernel: [  428.458668] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:09 archimedes kernel: [  428.458677] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:10 archimedes kernel: [  429.332143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:11 archimedes kernel: [  431.122445] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:11 archimedes kernel: [  431.122450] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:12 archimedes kernel: [  431.952143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:14 archimedes kernel: [  433.722447] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:14 archimedes kernel: [  433.722452] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:15 archimedes kernel: [  434.576143] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:16 archimedes kernel: [  436.152065] usb 5-2: USB disconnect, address 2
Jun 18 20:06:16 archimedes kernel: [  436.152688] Buffer I/O error on device sdb1, logical block 501
Jun 18 20:06:16 archimedes kernel: [  436.152696] lost page write due to I/O error on sdb1
Jun 18 20:06:16 archimedes kernel: [  436.278536] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:16 archimedes kernel: [  436.278545] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:17 archimedes kernel: [  437.196150] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:19 archimedes kernel: [  438.914461] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:19 archimedes kernel: [  438.914470] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:20 archimedes kernel: [  439.816145] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:21 archimedes kernel: [  440.756027] usb 5-2: new full speed USB device using uhci_hcd and address 3
Jun 18 20:06:21 archimedes kernel: [  440.914206] usb 5-2: configuration #1 chosen from 1 choice
Jun 18 20:06:21 archimedes kernel: [  440.918842] scsi9 : SCSI emulation for USB Mass Storage devices
Jun 18 20:06:21 archimedes kernel: [  440.919240] usb-storage: device found at 3
Jun 18 20:06:21 archimedes kernel: [  440.919245] usb-storage: waiting for device to settle before scanning
Jun 18 20:06:22 archimedes kernel: [  441.518509] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:22 archimedes kernel: [  441.518515] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:23 archimedes kernel: [  442.436141] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:24 archimedes kernel: [  444.134468] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:24 archimedes kernel: [  444.134474] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
Jun 18 20:06:25 archimedes kernel: [  445.060146] 0000:04:00.0: eth0: Link is Down
Jun 18 20:06:26 archimedes kernel: [  445.916087] usb-storage: device scan complete
Jun 18 20:06:26 archimedes kernel: [  445.922615] scsi 9:0:0:0: Direct-Access     USB NAND FLASH DISK       0.30 PQ: 0 ANSI: 2
Jun 18 20:06:26 archimedes kernel: [  445.986611] sd 9:0:0:0: [sdb] 64000 512-byte hardware sectors: (32.7 MB/31.2 MiB)
Jun 18 20:06:26 archimedes kernel: [  445.989590] sd 9:0:0:0: [sdb] Write Protect is off
Jun 18 20:06:26 archimedes kernel: [  445.989596] sd 9:0:0:0: [sdb] Mode Sense: 0b 00 00 08
Jun 18 20:06:26 archimedes kernel: [  445.989599] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun 18 20:06:26 archimedes kernel: [  446.001593] sd 9:0:0:0: [sdb] 64000 512-byte hardware sectors: (32.7 MB/31.2 MiB)
Jun 18 20:06:26 archimedes kernel: [  446.004590] sd 9:0:0:0: [sdb] Write Protect is off
Jun 18 20:06:26 archimedes kernel: [  446.004595] sd 9:0:0:0: [sdb] Mode Sense: 0b 00 00 08
Jun 18 20:06:26 archimedes kernel: [  446.004598] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun 18 20:06:26 archimedes kernel: [  446.004604]  sdb: sdb1
Jun 18 20:06:26 archimedes kernel: [  446.010848] sd 9:0:0:0: [sdb] Attached SCSI removable disk
Jun 18 20:06:26 archimedes kernel: [  446.010986] sd 9:0:0:0: Attached scsi generic sg2 type 0
Jun 18 20:06:27 archimedes kernel: [  446.754472] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun 18 20:06:27 archimedes kernel: [  446.754478] 0000:04:00.0: eth0: 10/100 speed: disabling TSO
```

I'm pretty sure the USB stuff at the bottom was me plugging in my flash drive to transfer this data from my desktop to my laptop.

---

### Post by MaindotC on 2009-06-20
I don't see anything stating you have a wireless card so you shouldn't be connecting to any wireless network.  As for your wired interface, you don't seem to have an IP address configuration.  

This:
```

*-network DISABLED

```
means one of the interfaces is disabled and as you can see it is associated w/ pan0.  Pan usually stands for Personal Area Network and that refers to bluetooth.  I don't see anything in your lspci output that states you are using bluetooth, so it could be that your firewire interface is being named pan0.  And if you're not using firewire then that's fine - leave it disabled.  The wired interface you ARE using seems to be correctly deteced and named eth0.  If your router is set to issue DHCP then you should be able to get an address for this interface with the command:
```

sudo dhclient eth0

```
As for your laptop - check the configuration of your access point and see if you have MAC filtering on.  Also try connecting via open, wep, and finally wpa2.  If you can connect with no encryption, but not with wep or wpa2, or if you can use wep but not wpa2, then the driver for your card (or the chipset for the card) may not support encryption or a specific standard of encryption.

---

### Post by Veteropinguis on 2009-06-22
Firstly, thank you all for being so patient, and sorry I haven't been able to respond for two days.

> As for your laptop - check the configuration of your access point and see if you have MAC filtering on. Um...how do I do that? >_>

Here's what I get from dhclient eth0:

```
There is already a pid file /var/run/dhclient.pid with pid 19612
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:19:db:62:df:57
Sending on   LPF/eth0/00:19:db:62:df:57
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I don't really understand what to do about that...

EDIT: I tried pinging my router and that didn't seem to work. Should I post the output of that?

---

### Post by Veteropinguis on 2009-06-23
Bump.

---

### Post by MaindotC on 2009-06-23
Directions for logging into your AP should be in your AP's documentation.  Typically you can do this by opening a web browswer and entering the address [http://192.168.1.1](http://192.168.1.1) but it depends on what type of AP you have.

In order for dhclient to work, there must be a dhcp server that will issue your machine an ip address.  Typically, there's one running on your AP.  When you log into your AP, check to see if it has dhcp running.

---

### Post by Veteropinguis on 2009-06-25
I can enable or disable a local DHCP server. 'Enable' was selected when I connected to my router.

I found a button that lets me 'Edit MAC Filter Setting'. In the menu it takes me to, every value (i.e MAC 1, MAC 2) is set to 0.

---

### Post by MaindotC on 2009-06-25
Ok well let's see if there's visual activity.  On your network card interface and on the AP interface there should be green and amber lights.  Green means they're connected and there's power, amber (blinking) means there's activity.  Do you have green & amber lights?

---

### Post by Veteropinguis on 2009-06-25
Green and amber lights on my end, and on the modem.

But here's something strange on the router...none of the 'Ethernet' lights are on, even though both ends of the Ethernet cable are fully plugged in. I checked this before, but I guess I have no memory.

Okay, I fixed it. I'd power-cycled the router and modem before, and that didn't help. I'd tried unplugging and replugging my Ethernet cable several times before.

So, I figured I'd try plugging everything in to different ports. My Ethernet cable was plugged in to port 1, and this other Ethernet cable I didn't recognize was plugged in to port 3. Disconnecting and reconnecting that other Ethernet cable fixed my problem.

I guess in the future I'll try that after power-cycling.

---

### Post by MaindotC on 2009-06-25
So you're good?

---

### Post by Veteropinguis on 2009-06-25
Yeah, I'm set. Sorry this became such a PEBKAC problem.

---

### Post by MaindotC on 2009-06-25
Np - hope I gave you some information and troubleshooting steps that will be helpful in the future :D

---

