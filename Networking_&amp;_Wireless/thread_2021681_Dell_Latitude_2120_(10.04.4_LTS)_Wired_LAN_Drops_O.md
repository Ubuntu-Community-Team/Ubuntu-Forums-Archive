---
title: "Dell Latitude 2120 (10.04.4 LTS) Wired LAN Drops Out After Awhile"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by computer13137 on 2012-07-09
This feels like a power saving preferences thing to me, but I have checked the Latitude 2120 BIOS and I see no power saving options for the Integrated Networking.

It only happens to the LAN Interface, which is 
Broadcom Corporation NetXtreme BCM57760 Gigabit Ethernet PCIe

For awhile, everything works just great.  Then the networking just blows up, and I get a bunch of errors in my ifconfig eth0:

> eth0      Link encap:Ethernet  HWaddr 5c:f9:dd:3d:73:46  
          inet6 addr: fe80::5ef9:ddff:fe3d:7346/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:15700 errors:4294967294 dropped:4294967294 overruns:0 frame:4294967286
          TX packets:4386 errors:4294967294 dropped:0 overruns:0 carrier:0
          collisions:4294967294 txqueuelen:1000 
          RX bytes:3199778 (3.1 MB)  TX bytes:2402098 (2.4 MB)
          Interrupt:19 

At this time, it stops showing the interface in Network Manager Gnome as well.

Broken:
[IMG]https://goput.it/4qf.png[/IMG]

Working: (after a reboot)
[IMG]https://goput.it/vaw.png[/IMG]

I am running kernel:
2.6.32-41-generic

Here is my lspci:
> 00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
**09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57760 Gigabit Ethernet PCIe (rev ff)**
0c:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
0d:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5208 (rev 01)

Here are the modules I have loaded up:
> Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
nf_conntrack_ipv4      10672  1 
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
xt_state                1098  1 
nf_conntrack           61615  2 nf_conntrack_ipv4,xt_state
xt_tcpudp               2011  2 
iptable_filter          2271  1 
ip_tables               9991  1 iptable_filter
x_tables               14299  3 xt_state,xt_tcpudp,ip_tables
snd_hda_codec_realtek   203472  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
joydev                  8740  0 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
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
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0 
lib80211_crypt_tkip     7596  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  290035  3 
dell_laptop             6888  0 
uvcvideo               57438  0 
drm_kms_helper         29329  1 i915
wl                   1959598  0 
psmouse                63677  0 
dcdbas                  5422  1 dell_laptop
soundcore               6620  1 snd
intel_agp              24375  2 i915
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
drm                   163779  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32680  2 
tg3                   109324  0 

After rebooting the netbook, the problem goes away for awhile, but it will always return.

Any suggestions anyone may have would be greatly appreciated.... Thanks!

---

### Post by computer13137 on 2012-07-10
Update:

Last night, I left 3 of these netbooks turned on.  All 3 of them are plugged into an unmanaged 8 port Netgear Prosafe switch connected back into our Cisco network architecture.

Of the 3, 2 of them exhibited this network issue.  1 of them still was working this morning when I came back in to work.

I thought about this, and consulted IRC, and we determined that it could be an unreliable driver.

I went to Broadcom's website and downloaded the latest Linux drivers, which I compiled and loaded.
[http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php](http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php)

After doing so, I went out of the office for a half hour to do other things, and when I returned, the network interface on the computer had disappeared, exhibiting the same problem as before.


I have tried:
```
rmmod tg3.ko
insmod tg3.ko
```


Before, when compiling the driver, doing so caused the network to disconnect, then caused it to connect.  After this "problem" starts, rebooting the computer fixes it, but doing those two commands seems to have NO effect.

I'm at a bit of a loss. Unfortunately, I need these computers in perfect working condition this month as we are deploying them next month.  I am going to continue exploring IRC and see if I can come up with a solution, as well as planning on testing some newer kernels to see if the problem persists.

Does anyone have any other suggestions?

Thanks

---

### Post by computer13137 on 2012-07-10
I have created a dump of the syslog, removing some information which I know for sure is irrelevant to this situation.

(specifically, I used)
```
cat /var/log/syslog | grep puppet-agent -v | grep CRON -v | grep crontab -v | grep AptDaemon -v
```

While I was uploading the first syslog (posted below), I encountered the network issue.  I immediately looked in the syslog, and pulled out this excerpt before rebooting. I feel this is likely the relevant information.
[http://paste.ubuntu.com/1084705/](http://paste.ubuntu.com/1084705/)
```
Jul 10 10:48:34 160096 kernel: [  661.788172] tg3: eth0: Link is down.
Jul 10 10:48:34 160096 NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jul 10 10:48:39 160096 NetworkManager: <info>  (eth0): device state change: 8 -> 2 (reason 40)
Jul 10 10:48:39 160096 NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Jul 10 10:48:39 160096 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1425
Jul 10 10:48:39 160096 NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Jul 10 10:48:39 160096 avahi-daemon[742]: Withdrawing address record for 10.9.6.77 on eth0.
Jul 10 10:48:39 160096 avahi-daemon[742]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.9.6.77.
Jul 10 10:48:39 160096 avahi-daemon[742]: Interface eth0.IPv4 no longer relevant for mDNS.
```

Here is my first COMPLETE syslog after removing the definitely irrelevant clutter.
(also on: [http://paste.ubuntu.com/1084692/](http://paste.ubuntu.com/1084692/))
```
Jul 10 08:01:39 160096 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="693" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul 10 08:02:01 160096 anacron[10254]: Job `cron.daily' terminated
Jul 10 08:02:01 160096 anacron[10254]: Normal exit (1 job run)
Jul 10 08:40:47 160096 kernel: [62501.861222] [drm] Big FIFO is enabled
Jul 10 08:47:55 160096 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 10 08:47:55 160096 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="689" x-info="http://www.rsyslog.com"] (re)start
Jul 10 08:47:55 160096 rsyslogd: rsyslogd's groupid changed to 103
Jul 10 08:47:55 160096 rsyslogd: rsyslogd's userid changed to 101
Jul 10 08:47:55 160096 rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul 10 08:47:55 160096 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 10 08:47:55 160096 kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 10 08:47:55 160096 kernel: [    0.000000] Linux version 2.6.32-41-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #90-Ubuntu SMP Tue May 22 11:31:25 UTC 2012 (Ubuntu 2.6.32-41.90-generic 2.6.32.59+drm33.24)
Jul 10 08:47:55 160096 kernel: [    0.000000] KERNEL supported cpus:
Jul 10 08:47:55 160096 kernel: [    0.000000]   Intel GenuineIntel
Jul 10 08:47:55 160096 kernel: [    0.000000]   AMD AuthenticAMD
Jul 10 08:47:55 160096 kernel: [    0.000000]   NSC Geode by NSC
Jul 10 08:47:55 160096 kernel: [    0.000000]   Cyrix CyrixInstead
Jul 10 08:47:55 160096 kernel: [    0.000000]   Centaur CentaurHauls
Jul 10 08:47:55 160096 kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 10 08:47:55 160096 kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 10 08:47:55 160096 kernel: [    0.000000]   UMC UMC UMC UMC
Jul 10 08:47:55 160096 kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5bf400 (usable)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 000000007f5bf400 - 000000007f5c1400 (ACPI NVS)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 000000007f5c1400 - 0000000080000000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda7000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000] DMI 2.4 present.
Jul 10 08:47:55 160096 kernel: [    0.000000] last_pfn = 0x7f5bf max_arch_pfn = 0x100000
Jul 10 08:47:55 160096 kernel: [    0.000000] MTRR default type: uncachable
Jul 10 08:47:55 160096 kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 10 08:47:55 160096 kernel: [    0.000000]   00000-9FFFF write-back
Jul 10 08:47:55 160096 kernel: [    0.000000]   A0000-BFFFF uncachable
Jul 10 08:47:55 160096 kernel: [    0.000000]   C0000-CFFFF write-protect
Jul 10 08:47:55 160096 kernel: [    0.000000]   D0000-EFFFF uncachable
Jul 10 08:47:55 160096 kernel: [    0.000000]   F0000-FFFFF write-protect
Jul 10 08:47:55 160096 kernel: [    0.000000] MTRR variable ranges enabled:
Jul 10 08:47:55 160096 kernel: [    0.000000]   0 base 000000000 mask 000000000 write-back
Jul 10 08:47:55 160096 kernel: [    0.000000]   1 base 0E0000000 mask 0E0000000 uncachable
Jul 10 08:47:55 160096 kernel: [    0.000000]   2 base 07F700000 mask 0FFF00000 uncachable
Jul 10 08:47:55 160096 kernel: [    0.000000]   3 base 07F800000 mask 0FF800000 uncachable
Jul 10 08:47:55 160096 kernel: [    0.000000]   4 base 07F600000 mask FFFF00000 write-through
Jul 10 08:47:55 160096 kernel: [    0.000000]   5 base 07F600000 mask FFFF00000 write-through
Jul 10 08:47:55 160096 kernel: [    0.000000]   6 base 07F600000 mask FFFF00000 write-through
Jul 10 08:47:55 160096 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 10 08:47:55 160096 kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 10 08:47:55 160096 kernel: [    0.000000] modified physical RAM map:
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 0000000000100000 - 000000007f5bf400 (usable)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 000000007f5bf400 - 000000007f5c1400 (ACPI NVS)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 000000007f5c1400 - 0000000080000000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 00000000feda0000 - 00000000feda7000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Jul 10 08:47:55 160096 kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Jul 10 08:47:55 160096 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul 10 08:47:55 160096 kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jul 10 08:47:55 160096 kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jul 10 08:47:55 160096 kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jul 10 08:47:55 160096 kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jul 10 08:47:55 160096 kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Jul 10 08:47:55 160096 kernel: [    0.000000] RAMDISK: 3784e000 - 37feff9b
Jul 10 08:47:55 160096 kernel: [    0.000000] Allocated new RAMDISK: 008ea000 - 0108bf9b
Jul 10 08:47:55 160096 kernel: [    0.000000] Move RAMDISK from 000000003784e000 - 0000000037feff9a to 008ea000 - 0108bf9a
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: RSDP 000fbe70 00024 (v02 DELL  )
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: XSDT 7f5c3e00 0005C (v01 DELL    M09     27DB0A1F ASL  00000061)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: FACP 7f5c3c9c 000F4 (v04 DELL    M09     27DB0A1F ASL  00000061)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: DSDT 7f5c4400 05A7D (v02 INT430 SYSFexxx 00001001 INTL 20050624)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: FACS 7f5d2c00 00040
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: HPET 7f5c3f00 00038 (v01 DELL    M09     00000001 ASL  00000061)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: APIC 7f5c4000 00078 (v01 DELL    M09     27DB0A1F ASL  00000047)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: ASF! 7f5c3c00 00076 (v32 DELL    M09     27DB0A1F ASL  00000061)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: MCFG 7f5c3fc0 0003C (v16 DELL    M09     27DB0A1F ASL  00000061)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: SLIC 7f5c409c 00176 (v01 DELL    M09     27DB0A1F ASL  00000061)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: SSDT 7f5c2367 0066C (v01  PmRef    CpuPm 00003000 INTL 20050624)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 10 08:47:55 160096 kernel: [    0.000000] 1149MB HIGHMEM available.
Jul 10 08:47:55 160096 kernel: [    0.000000] 887MB LOWMEM available.
Jul 10 08:47:55 160096 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul 10 08:47:55 160096 kernel: [    0.000000]   low ram: 0 - 377fe000
Jul 10 08:47:55 160096 kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jul 10 08:47:55 160096 kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Jul 10 08:47:55 160096 kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jul 10 08:47:55 160096 kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 10 08:47:55 160096 kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jul 10 08:47:55 160096 kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jul 10 08:47:55 160096 kernel: [    0.000000]   #3 [0000100000 - 00008e5f18]    TEXT DATA BSS ==> [0000100000 - 00008e5f18]
Jul 10 08:47:55 160096 kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Jul 10 08:47:55 160096 kernel: [    0.000000]   #5 [00008e6000 - 00008e9184]              BRK ==> [00008e6000 - 00008e9184]
Jul 10 08:47:55 160096 kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Jul 10 08:47:55 160096 kernel: [    0.000000]   #7 [00008ea000 - 000108bf9b]      NEW RAMDISK ==> [00008ea000 - 000108bf9b]
Jul 10 08:47:55 160096 kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Jul 10 08:47:55 160096 kernel: [    0.000000] Zone PFN ranges:
Jul 10 08:47:55 160096 kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jul 10 08:47:55 160096 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul 10 08:47:55 160096 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007f5bf
Jul 10 08:47:55 160096 kernel: [    0.000000] Movable zone start PFN for each node
Jul 10 08:47:55 160096 kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul 10 08:47:55 160096 kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Jul 10 08:47:55 160096 kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Jul 10 08:47:55 160096 kernel: [    0.000000]     0: 0x00000100 -> 0x0007f5bf
Jul 10 08:47:55 160096 kernel: [    0.000000] On node 0 totalpages: 521562
Jul 10 08:47:55 160096 kernel: [    0.000000] free_area_init_node: node 0, pgdat c07a0a20, node_mem_map c108d000
Jul 10 08:47:55 160096 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 10 08:47:55 160096 kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 10 08:47:55 160096 kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Jul 10 08:47:55 160096 kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jul 10 08:47:55 160096 kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jul 10 08:47:55 160096 kernel: [    0.000000]   HighMem zone: 2300 pages used for memmap
Jul 10 08:47:55 160096 kernel: [    0.000000]   HighMem zone: 292037 pages, LIFO batch:31
Jul 10 08:47:55 160096 kernel: [    0.000000] Using APIC driver default
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 10 08:47:55 160096 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 10 08:47:55 160096 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 10 08:47:55 160096 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jul 10 08:47:55 160096 kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul 10 08:47:55 160096 kernel: [    0.000000] nr_irqs_gsi: 24
Jul 10 08:47:55 160096 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 10 08:47:55 160096 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 10 08:47:55 160096 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Jul 10 08:47:55 160096 kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
Jul 10 08:47:55 160096 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 10 08:47:55 160096 kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jul 10 08:47:55 160096 kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u1048576
Jul 10 08:47:55 160096 kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
Jul 10 08:47:55 160096 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 10 08:47:55 160096 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517486
Jul 10 08:47:55 160096 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-41-generic root=UUID=dab19fca-2dbe-4769-af3e-61a711b51c94 ro quiet splash
Jul 10 08:47:55 160096 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 10 08:47:55 160096 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 10 08:47:55 160096 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 10 08:47:55 160096 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul 10 08:47:55 160096 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul 10 08:47:55 160096 kernel: [    0.000000] Initializing CPU#0
Jul 10 08:47:55 160096 kernel: [    0.000000] allocated 10433260 bytes of page_cgroup
Jul 10 08:47:55 160096 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 10 08:47:55 160096 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007f5bf)
Jul 10 08:47:55 160096 kernel: [    0.000000] Memory: 2041480k/2086652k available (4699k kernel code, 43524k reserved, 2128k data, 664k init, 1177348k highmem)
Jul 10 08:47:55 160096 kernel: [    0.000000] virtual kernel memory layout:
Jul 10 08:47:55 160096 kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jul 10 08:47:55 160096 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 10 08:47:55 160096 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul 10 08:47:55 160096 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul 10 08:47:55 160096 kernel: [    0.000000]       .init : 0xc07ab000 - 0xc0851000   ( 664 kB)
Jul 10 08:47:55 160096 kernel: [    0.000000]       .data : 0xc0596c47 - 0xc07aafc8   (2128 kB)
Jul 10 08:47:55 160096 kernel: [    0.000000]       .text : 0xc0100000 - 0xc0596c47   (4699 kB)
Jul 10 08:47:55 160096 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 10 08:47:55 160096 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 10 08:47:55 160096 kernel: [    0.000000] Hierarchical RCU implementation.
Jul 10 08:47:55 160096 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Jul 10 08:47:55 160096 kernel: [    0.000000] Extended CMOS year: 2000
Jul 10 08:47:55 160096 kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 10 08:47:55 160096 kernel: [    0.000000] console [tty0] enabled
Jul 10 08:47:55 160096 kernel: [    0.000000] hpet clockevent registered
Jul 10 08:47:55 160096 kernel: [    0.000000] Fast TSC calibration using PIT
Jul 10 08:47:55 160096 kernel: [    0.000000] Detected 1662.336 MHz processor.
Jul 10 08:47:55 160096 kernel: [    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.67 BogoMIPS (lpj=6649344)
Jul 10 08:47:55 160096 kernel: [    0.004044] Security Framework initialized
Jul 10 08:47:55 160096 kernel: [    0.004083] AppArmor: AppArmor initialized
Jul 10 08:47:55 160096 kernel: [    0.004098] Mount-cache hash table entries: 512
Jul 10 08:47:55 160096 kernel: [    0.004332] Initializing cgroup subsys ns
Jul 10 08:47:55 160096 kernel: [    0.004341] Initializing cgroup subsys cpuacct
Jul 10 08:47:55 160096 kernel: [    0.004351] Initializing cgroup subsys memory
Jul 10 08:47:55 160096 kernel: [    0.004365] Initializing cgroup subsys devices
Jul 10 08:47:55 160096 kernel: [    0.004370] Initializing cgroup subsys freezer
Jul 10 08:47:55 160096 kernel: [    0.004376] Initializing cgroup subsys net_cls
Jul 10 08:47:55 160096 kernel: [    0.004414] CPU: L1 I cache: 32K, L1 D cache: 24K
Jul 10 08:47:55 160096 kernel: [    0.004421] CPU: L2 cache: 512K
Jul 10 08:47:55 160096 kernel: [    0.004426] CPU: Physical Processor ID: 0
Jul 10 08:47:55 160096 kernel: [    0.004431] CPU: Processor Core ID: 0
Jul 10 08:47:55 160096 kernel: [    0.004438] mce: CPU supports 5 MCE banks
Jul 10 08:47:55 160096 kernel: [    0.004451] CPU0: Thermal monitoring enabled (TM2)
Jul 10 08:47:55 160096 kernel: [    0.004459] using mwait in idle threads.
Jul 10 08:47:55 160096 kernel: [    0.004470] Performance Events: Atom events, Intel PMU driver.
Jul 10 08:47:55 160096 kernel: [    0.004486] ... version:                3
Jul 10 08:47:55 160096 kernel: [    0.004491] ... bit width:              40
Jul 10 08:47:55 160096 kernel: [    0.004495] ... generic registers:      2
Jul 10 08:47:55 160096 kernel: [    0.004500] ... value mask:             000000ffffffffff
Jul 10 08:47:55 160096 kernel: [    0.004505] ... max period:             000000007fffffff
Jul 10 08:47:55 160096 kernel: [    0.004510] ... fixed-purpose events:   3
Jul 10 08:47:55 160096 kernel: [    0.004514] ... event mask:             0000000700000003
Jul 10 08:47:55 160096 kernel: [    0.004523] Checking 'hlt' instruction... OK.
Jul 10 08:47:55 160096 kernel: [    0.020008] Disabling 4MB page tables to avoid TLB bug
Jul 10 08:47:55 160096 kernel: [    0.024299] ACPI: Core revision 20090903
Jul 10 08:47:55 160096 kernel: [    0.040018] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul 10 08:47:55 160096 kernel: [    0.040029] ftrace: allocating 21840 entries in 43 pages
Jul 10 08:47:55 160096 kernel: [    0.044114] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 10 08:47:55 160096 kernel: [    0.044516] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 10 08:47:55 160096 kernel: [    0.084525] CPU0: Intel(R) Atom(TM) CPU N455   @ 1.66GHz stepping 0a
Jul 10 08:47:55 160096 kernel: [    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
Jul 10 08:47:55 160096 kernel: [    0.008000] Initializing CPU#1
Jul 10 08:47:55 160096 kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
Jul 10 08:47:55 160096 kernel: [    0.008000] CPU: L2 cache: 512K
Jul 10 08:47:55 160096 kernel: [    0.008000] CPU: Physical Processor ID: 0
Jul 10 08:47:55 160096 kernel: [    0.008000] CPU: Processor Core ID: 0
Jul 10 08:47:55 160096 kernel: [    0.008000] CPU1: Thermal monitoring enabled (TM2)
Jul 10 08:47:55 160096 kernel: [    0.172121] CPU1: Intel(R) Atom(TM) CPU N455   @ 1.66GHz stepping 0a
Jul 10 08:47:55 160096 kernel: [    0.172136] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul 10 08:47:55 160096 kernel: [    0.176042] Brought up 2 CPUs
Jul 10 08:47:55 160096 kernel: [    0.176049] Total of 2 processors activated (6649.67 BogoMIPS).
Jul 10 08:47:55 160096 kernel: [    0.176463] CPU0 attaching sched-domain:
Jul 10 08:47:55 160096 kernel: [    0.176470]  domain 0: span 0-1 level SIBLING
Jul 10 08:47:55 160096 kernel: [    0.176476]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Jul 10 08:47:55 160096 kernel: [    0.176488]   domain 1: span 0-1 level MC
Jul 10 08:47:55 160096 kernel: [    0.176493]    groups: 0-1 (cpu_power = 1178)
Jul 10 08:47:55 160096 kernel: [    0.176504] CPU1 attaching sched-domain:
Jul 10 08:47:55 160096 kernel: [    0.176509]  domain 0: span 0-1 level SIBLING
Jul 10 08:47:55 160096 kernel: [    0.176514]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Jul 10 08:47:55 160096 kernel: [    0.176525]   domain 1: span 0-1 level MC
Jul 10 08:47:55 160096 kernel: [    0.176530]    groups: 0-1 (cpu_power = 1178)
Jul 10 08:47:55 160096 kernel: [    0.176700] devtmpfs: initialized
Jul 10 08:47:55 160096 kernel: [    0.176700] regulator: core version 0.5
Jul 10 08:47:55 160096 kernel: [    0.176700] Time: 13:47:32  Date: 07/10/12
Jul 10 08:47:55 160096 kernel: [    0.176700] NET: Registered protocol family 16
Jul 10 08:47:55 160096 kernel: [    0.176700] Trying to unpack rootfs image as initramfs...
Jul 10 08:47:55 160096 kernel: [    0.176700] EISA bus registered
Jul 10 08:47:55 160096 kernel: [    0.176700] ACPI: bus type pci registered
Jul 10 08:47:55 160096 kernel: [    0.176740] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Jul 10 08:47:55 160096 kernel: [    0.176749] PCI: MCFG area at f8000000 reserved in E820
Jul 10 08:47:55 160096 kernel: [    0.176755] PCI: Using MMCONFIG for extended config space
Jul 10 08:47:55 160096 kernel: [    0.176761] PCI: Using configuration type 1 for base access
Jul 10 08:47:55 160096 kernel: [    0.181995] bio: create slab <bio-0> at 0
Jul 10 08:47:55 160096 kernel: [    0.184118] ACPI: EC: Look up EC in DSDT
Jul 10 08:47:55 160096 kernel: [    0.184703] ACPI: BIOS _OSI(Linux) query ignored
Jul 10 08:47:55 160096 kernel: [    0.228437] ACPI: Interpreter enabled
Jul 10 08:47:55 160096 kernel: [    0.228450] ACPI: (supports S0 S3 S4 S5)
Jul 10 08:47:55 160096 kernel: [    0.228511] ACPI: Using IOAPIC for interrupt routing
Jul 10 08:47:55 160096 kernel: [    0.308503] ACPI: EC: GPE = 0x19, I/O: command/status = 0x934, data = 0x930
Jul 10 08:47:55 160096 kernel: [    0.309155] ACPI: No dock devices found.
Jul 10 08:47:55 160096 kernel: [    0.356898] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 10 08:47:55 160096 kernel: [    0.357102] pci 0000:00:02.0: reg 10 32bit mmio: [0xf6e00000-0xf6e7ffff]
Jul 10 08:47:55 160096 kernel: [    0.357115] pci 0000:00:02.0: reg 14 io port: [0xeff8-0xefff]
Jul 10 08:47:55 160096 kernel: [    0.357127] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xe0000000-0xefffffff]
Jul 10 08:47:55 160096 kernel: [    0.357138] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf6f00000-0xf6ffffff]
Jul 10 08:47:55 160096 kernel: [    0.357209] pci 0000:00:02.1: reg 10 32bit mmio: [0xf6e80000-0xf6efffff]
Jul 10 08:47:55 160096 kernel: [    0.357379] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6dfc000-0xf6dfffff]
Jul 10 08:47:55 160096 kernel: [    0.357503] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul 10 08:47:55 160096 kernel: [    0.357516] pci 0000:00:1b.0: PME# disabled
Jul 10 08:47:55 160096 kernel: [    0.357681] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul 10 08:47:55 160096 kernel: [    0.357692] pci 0000:00:1c.0: PME# disabled
Jul 10 08:47:55 160096 kernel: [    0.357860] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jul 10 08:47:55 160096 kernel: [    0.357870] pci 0000:00:1c.1: PME# disabled
Jul 10 08:47:55 160096 kernel: [    0.358036] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jul 10 08:47:55 160096 kernel: [    0.358047] pci 0000:00:1c.2: PME# disabled
Jul 10 08:47:55 160096 kernel: [    0.358215] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jul 10 08:47:55 160096 kernel: [    0.358228] pci 0000:00:1c.3: PME# disabled
Jul 10 08:47:55 160096 kernel: [    0.358334] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
Jul 10 08:47:55 160096 kernel: [    0.358441] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
Jul 10 08:47:55 160096 kernel: [    0.358544] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
Jul 10 08:47:55 160096 kernel: [    0.358646] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
Jul 10 08:47:55 160096 kernel: [    0.358763] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
Jul 10 08:47:55 160096 kernel: [    0.358881] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul 10 08:47:55 160096 kernel: [    0.358892] pci 0000:00:1d.7: PME# disabled
Jul 10 08:47:55 160096 kernel: [    0.359252] pci 0000:00:1f.2: reg 10 io port: [0x6e70-0x6e77]
Jul 10 08:47:55 160096 kernel: [    0.359269] pci 0000:00:1f.2: reg 14 io port: [0x6e78-0x6e7b]
Jul 10 08:47:55 160096 kernel: [    0.359284] pci 0000:00:1f.2: reg 18 io port: [0x6e80-0x6e87]
Jul 10 08:47:55 160096 kernel: [    0.359299] pci 0000:00:1f.2: reg 1c io port: [0x6e88-0x6e8b]
Jul 10 08:47:55 160096 kernel: [    0.359314] pci 0000:00:1f.2: reg 20 io port: [0x6ea0-0x6ebf]
Jul 10 08:47:55 160096 kernel: [    0.359329] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfed1c800-0xfed1cbff]
Jul 10 08:47:55 160096 kernel: [    0.359414] pci 0000:00:1f.2: PME# supported from D3hot
Jul 10 08:47:55 160096 kernel: [    0.359424] pci 0000:00:1f.2: PME# disabled
Jul 10 08:47:55 160096 kernel: [    0.359509] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
Jul 10 08:47:55 160096 kernel: [    0.359788] pci 0000:0c:00.0: reg 10 64bit mmio: [0xf6cfc000-0xf6cfffff]
Jul 10 08:47:55 160096 kernel: [    0.360032] pci 0000:0c:00.0: supports D1 D2
Jul 10 08:47:55 160096 kernel: [    0.360040] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
Jul 10 08:47:55 160096 kernel: [    0.360053] pci 0000:0c:00.0: PME# disabled
Jul 10 08:47:55 160096 kernel: [    0.360188] pci 0000:00:1c.1: bridge 32bit mmio: [0xf6c00000-0xf6cfffff]
Jul 10 08:47:55 160096 kernel: [    0.360392] pci 0000:0d:00.0: reg 10 32bit mmio: [0xf6bf0000-0xf6bfffff]
Jul 10 08:47:55 160096 kernel: [    0.360809] pci 0000:0d:00.0: supports D1 D2
Jul 10 08:47:55 160096 kernel: [    0.360818] pci 0000:0d:00.0: PME# supported from D1 D2 D3hot
Jul 10 08:47:55 160096 kernel: [    0.360834] pci 0000:0d:00.0: PME# disabled
Jul 10 08:47:55 160096 kernel: [    0.361002] pci 0000:00:1c.2: bridge 32bit mmio: [0xf6b00000-0xf6bfffff]
Jul 10 08:47:55 160096 kernel: [    0.361175] pci 0000:09:00.0: reg 10 64bit mmio: [0xf6af0000-0xf6afffff]
Jul 10 08:47:55 160096 kernel: [    0.361397] pci 0000:09:00.0: PME# supported from D3hot D3cold
Jul 10 08:47:55 160096 kernel: [    0.361411] pci 0000:09:00.0: PME# disabled
Jul 10 08:47:55 160096 kernel: [    0.361544] pci 0000:00:1c.3: bridge 32bit mmio: [0xf6a00000-0xf6afffff]
Jul 10 08:47:55 160096 kernel: [    0.361641] pci 0000:00:1e.0: transparent bridge
Jul 10 08:47:55 160096 kernel: [    0.361703] pci_bus 0000:00: on NUMA node 0
Jul 10 08:47:55 160096 kernel: [    0.361725] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 10 08:47:55 160096 kernel: [    0.362426] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Jul 10 08:47:55 160096 kernel: [    0.362786] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jul 10 08:47:55 160096 kernel: [    0.363015] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Jul 10 08:47:55 160096 kernel: [    0.363225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Jul 10 08:47:55 160096 kernel: [    0.363433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Jul 10 08:47:55 160096 kernel: [    0.397084] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
Jul 10 08:47:55 160096 kernel: [    0.397407] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Jul 10 08:47:55 160096 kernel: [    0.397740] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *3
Jul 10 08:47:55 160096 kernel: [    0.398062] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *10 11)
Jul 10 08:47:55 160096 kernel: [    0.398348] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul 10 08:47:55 160096 kernel: [    0.398687] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jul 10 08:47:55 160096 kernel: [    0.399015] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Jul 10 08:47:55 160096 kernel: [    0.399363] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jul 10 08:47:55 160096 kernel: [    0.399732] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jul 10 08:47:55 160096 kernel: [    0.399767] vgaarb: loaded
Jul 10 08:47:55 160096 kernel: [    0.400135] SCSI subsystem initialized
Jul 10 08:47:55 160096 kernel: [    0.400365] libata version 3.00 loaded.
Jul 10 08:47:55 160096 kernel: [    0.400607] usbcore: registered new interface driver usbfs
Jul 10 08:47:55 160096 kernel: [    0.400651] usbcore: registered new interface driver hub
Jul 10 08:47:55 160096 kernel: [    0.400736] usbcore: registered new device driver usb
Jul 10 08:47:55 160096 kernel: [    0.401261] ACPI: WMI: Mapper loaded
Jul 10 08:47:55 160096 kernel: [    0.401269] PCI: Using ACPI for IRQ routing
Jul 10 08:47:55 160096 kernel: [    0.401738] NetLabel: Initializing
Jul 10 08:47:55 160096 kernel: [    0.401745] NetLabel:  domain hash size = 128
Jul 10 08:47:55 160096 kernel: [    0.401751] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 10 08:47:55 160096 kernel: [    0.401782] NetLabel:  unlabeled traffic allowed by default
Jul 10 08:47:55 160096 kernel: [    0.401889] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul 10 08:47:55 160096 kernel: [    0.401903] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 10 08:47:55 160096 kernel: [    0.401918] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jul 10 08:47:55 160096 kernel: [    0.404244] Switching to clocksource tsc
Jul 10 08:47:55 160096 kernel: [    0.408908] AppArmor: AppArmor Filesystem Enabled
Jul 10 08:47:55 160096 kernel: [    0.408943] pnp: PnP ACPI init
Jul 10 08:47:55 160096 kernel: [    0.408980] ACPI: bus type pnp registered
Jul 10 08:47:55 160096 kernel: [    0.458336]   alloc irq_desc for 20 on node -1
Jul 10 08:47:55 160096 kernel: [    0.458346]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.514149] pnp: PnP ACPI: found 13 devices
Jul 10 08:47:55 160096 kernel: [    0.514158] ACPI: ACPI bus type pnp unregistered
Jul 10 08:47:55 160096 kernel: [    0.514168] PnPBIOS: Disabled by ACPI PNP
Jul 10 08:47:55 160096 kernel: [    0.514209] system 00:05: ioport range 0xc80-0xcff could not be reserved
Jul 10 08:47:55 160096 kernel: [    0.514233] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514255] system 00:0a: ioport range 0x900-0x92f has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514265] system 00:0a: ioport range 0x931-0x933 has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514274] system 00:0a: ioport range 0x935-0x97f has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514284] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514295] system 00:0a: ioport range 0x1000-0x1005 has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514304] system 00:0a: ioport range 0x1008-0x100f has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514327] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514337] system 00:0b: ioport range 0x1006-0x1007 has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514347] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
Jul 10 08:47:55 160096 kernel: [    0.514356] system 00:0b: ioport range 0x1060-0x107f has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514366] system 00:0b: ioport range 0x1080-0x10bf has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514376] system 00:0b: ioport range 0x10c0-0x10df has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514385] system 00:0b: ioport range 0x1010-0x102f has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514394] system 00:0b: ioport range 0x809-0x809 has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514415] system 00:0c: iomem range 0x0-0x9efff could not be reserved
Jul 10 08:47:55 160096 kernel: [    0.514425] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
Jul 10 08:47:55 160096 kernel: [    0.514435] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Jul 10 08:47:55 160096 kernel: [    0.514444] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Jul 10 08:47:55 160096 kernel: [    0.514454] system 00:0c: iomem range 0x100000-0x7f5bf3ff could not be reserved
Jul 10 08:47:55 160096 kernel: [    0.514464] system 00:0c: iomem range 0x7f5bf400-0x7f5fffff could not be reserved
Jul 10 08:47:55 160096 kernel: [    0.514474] system 00:0c: iomem range 0x7f600000-0x7f6fffff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514484] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514494] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514504] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
Jul 10 08:47:55 160096 kernel: [    0.514514] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514524] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514534] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514544] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514554] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514564] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514575] system 00:0c: iomem range 0xfed1c800-0xfed1cfff could not be reserved
Jul 10 08:47:55 160096 kernel: [    0.514585] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.514595] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
Jul 10 08:47:55 160096 kernel: [    0.549810] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
Jul 10 08:47:55 160096 kernel: [    0.549823] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
Jul 10 08:47:55 160096 kernel: [    0.549837] pci 0000:00:1c.0:   MEM window: 0x80000000-0x801fffff
Jul 10 08:47:55 160096 kernel: [    0.549850] pci 0000:00:1c.0:   PREFETCH window: 0x00000080200000-0x000000803fffff
Jul 10 08:47:55 160096 kernel: [    0.549868] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
Jul 10 08:47:55 160096 kernel: [    0.549878] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
Jul 10 08:47:55 160096 kernel: [    0.549892] pci 0000:00:1c.1:   MEM window: 0xf6c00000-0xf6cfffff
Jul 10 08:47:55 160096 kernel: [    0.549904] pci 0000:00:1c.1:   PREFETCH window: 0x00000080400000-0x000000805fffff
Jul 10 08:47:55 160096 kernel: [    0.549922] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:0d
Jul 10 08:47:55 160096 kernel: [    0.549932] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
Jul 10 08:47:55 160096 kernel: [    0.549946] pci 0000:00:1c.2:   MEM window: 0xf6b00000-0xf6bfffff
Jul 10 08:47:55 160096 kernel: [    0.549959] pci 0000:00:1c.2:   PREFETCH window: 0x00000080600000-0x000000807fffff
Jul 10 08:47:55 160096 kernel: [    0.549975] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:09
Jul 10 08:47:55 160096 kernel: [    0.549985] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
Jul 10 08:47:55 160096 kernel: [    0.549997] pci 0000:00:1c.3:   MEM window: 0xf6a00000-0xf6afffff
Jul 10 08:47:55 160096 kernel: [    0.550009] pci 0000:00:1c.3:   PREFETCH window: 0x00000080800000-0x000000809fffff
Jul 10 08:47:55 160096 kernel: [    0.550024] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Jul 10 08:47:55 160096 kernel: [    0.550030] pci 0000:00:1e.0:   IO window: disabled
Jul 10 08:47:55 160096 kernel: [    0.550042] pci 0000:00:1e.0:   MEM window: disabled
Jul 10 08:47:55 160096 kernel: [    0.550051] pci 0000:00:1e.0:   PREFETCH window: disabled
Jul 10 08:47:55 160096 kernel: [    0.550089]   alloc irq_desc for 16 on node -1
Jul 10 08:47:55 160096 kernel: [    0.550096]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.550114] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 10 08:47:55 160096 kernel: [    0.550126] pci 0000:00:1c.0: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.550148]   alloc irq_desc for 17 on node -1
Jul 10 08:47:55 160096 kernel: [    0.550154]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.550165] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 10 08:47:55 160096 kernel: [    0.550176] pci 0000:00:1c.1: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.550197]   alloc irq_desc for 18 on node -1
Jul 10 08:47:55 160096 kernel: [    0.550203]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.550214] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 10 08:47:55 160096 kernel: [    0.550225] pci 0000:00:1c.2: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.550246]   alloc irq_desc for 19 on node -1
Jul 10 08:47:55 160096 kernel: [    0.550252]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.550263] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jul 10 08:47:55 160096 kernel: [    0.550274] pci 0000:00:1c.3: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.550291] pci 0000:00:1e.0: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.550303] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jul 10 08:47:55 160096 kernel: [    0.550311] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Jul 10 08:47:55 160096 kernel: [    0.550320] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
Jul 10 08:47:55 160096 kernel: [    0.550328] pci_bus 0000:0b: resource 1 mem: [0x80000000-0x801fffff]
Jul 10 08:47:55 160096 kernel: [    0.550337] pci_bus 0000:0b: resource 2 pref mem [0x80200000-0x803fffff]
Jul 10 08:47:55 160096 kernel: [    0.550345] pci_bus 0000:0c: resource 0 io:  [0x3000-0x3fff]
Jul 10 08:47:55 160096 kernel: [    0.550353] pci_bus 0000:0c: resource 1 mem: [0xf6c00000-0xf6cfffff]
Jul 10 08:47:55 160096 kernel: [    0.550361] pci_bus 0000:0c: resource 2 pref mem [0x80400000-0x805fffff]
Jul 10 08:47:55 160096 kernel: [    0.550370] pci_bus 0000:0d: resource 0 io:  [0x4000-0x4fff]
Jul 10 08:47:55 160096 kernel: [    0.550378] pci_bus 0000:0d: resource 1 mem: [0xf6b00000-0xf6bfffff]
Jul 10 08:47:55 160096 kernel: [    0.550387] pci_bus 0000:0d: resource 2 pref mem [0x80600000-0x807fffff]
Jul 10 08:47:55 160096 kernel: [    0.550395] pci_bus 0000:09: resource 0 io:  [0x5000-0x5fff]
Jul 10 08:47:55 160096 kernel: [    0.550403] pci_bus 0000:09: resource 1 mem: [0xf6a00000-0xf6afffff]
Jul 10 08:47:55 160096 kernel: [    0.550411] pci_bus 0000:09: resource 2 pref mem [0x80800000-0x809fffff]
Jul 10 08:47:55 160096 kernel: [    0.550420] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
Jul 10 08:47:55 160096 kernel: [    0.550428] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
Jul 10 08:47:55 160096 kernel: [    0.550525] NET: Registered protocol family 2
Jul 10 08:47:55 160096 kernel: [    0.550812] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 10 08:47:55 160096 kernel: [    0.551728] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 10 08:47:55 160096 kernel: [    0.552807] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 10 08:47:55 160096 kernel: [    0.553334] TCP: Hash tables configured (established 131072 bind 65536)
Jul 10 08:47:55 160096 kernel: [    0.553346] TCP reno registered
Jul 10 08:47:55 160096 kernel: [    0.553629] NET: Registered protocol family 1
Jul 10 08:47:55 160096 kernel: [    0.553681] pci 0000:00:02.0: Boot video device
Jul 10 08:47:55 160096 kernel: [    0.553726]   alloc irq_desc for 22 on node -1
Jul 10 08:47:55 160096 kernel: [    0.553734]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.553750] pci 0000:00:1d.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 10 08:47:55 160096 kernel: [    0.553784] pci 0000:00:1d.0: PCI INT A disabled
Jul 10 08:47:55 160096 kernel: [    0.553801]   alloc irq_desc for 21 on node -1
Jul 10 08:47:55 160096 kernel: [    0.553807]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.553818] pci 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jul 10 08:47:55 160096 kernel: [    0.553848] pci 0000:00:1d.1: PCI INT B disabled
Jul 10 08:47:55 160096 kernel: [    0.553866] pci 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jul 10 08:47:55 160096 kernel: [    0.553895] pci 0000:00:1d.2: PCI INT C disabled
Jul 10 08:47:55 160096 kernel: [    0.553912]   alloc irq_desc for 23 on node -1
Jul 10 08:47:55 160096 kernel: [    0.553918]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.553928] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jul 10 08:47:55 160096 kernel: [    0.553958] pci 0000:00:1d.3: PCI INT D disabled
Jul 10 08:47:55 160096 kernel: [    0.553984] pci 0000:00:1d.7: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 10 08:47:55 160096 kernel: [    0.554039] pci 0000:00:1d.7: PCI INT A disabled
Jul 10 08:47:55 160096 kernel: [    0.554589] cpufreq-nforce2: No nForce2 chipset.
Jul 10 08:47:55 160096 kernel: [    0.554667] Scanning for low memory corruption every 60 seconds
Jul 10 08:47:55 160096 kernel: [    0.554980] audit: initializing netlink socket (disabled)
Jul 10 08:47:55 160096 kernel: [    0.555007] type=2000 audit(1341928052.551:1): initialized
Jul 10 08:47:55 160096 kernel: [    0.575983] highmem bounce pool size: 64 pages
Jul 10 08:47:55 160096 kernel: [    0.575998] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 10 08:47:55 160096 kernel: [    0.581163] VFS: Disk quotas dquot_6.5.2
Jul 10 08:47:55 160096 kernel: [    0.581358] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 10 08:47:55 160096 kernel: [    0.583378] fuse init (API version 7.13)
Jul 10 08:47:55 160096 kernel: [    0.583683] msgmni has been set to 1690
Jul 10 08:47:55 160096 kernel: [    0.584366] alg: No test for stdrng (krng)
Jul 10 08:47:55 160096 kernel: [    0.584555] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 10 08:47:55 160096 kernel: [    0.584565] io scheduler noop registered
Jul 10 08:47:55 160096 kernel: [    0.584571] io scheduler anticipatory registered
Jul 10 08:47:55 160096 kernel: [    0.584576] io scheduler deadline registered
Jul 10 08:47:55 160096 kernel: [    0.584711] io scheduler cfq registered (default)
Jul 10 08:47:55 160096 kernel: [    0.585070]   alloc irq_desc for 24 on node -1
Jul 10 08:47:55 160096 kernel: [    0.585079]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.585105] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Jul 10 08:47:55 160096 kernel: [    0.585126] pcieport 0000:00:1c.0: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.585407]   alloc irq_desc for 25 on node -1
Jul 10 08:47:55 160096 kernel: [    0.585414]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.585432] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
Jul 10 08:47:55 160096 kernel: [    0.585451] pcieport 0000:00:1c.1: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.585719]   alloc irq_desc for 26 on node -1
Jul 10 08:47:55 160096 kernel: [    0.585726]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.585745] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
Jul 10 08:47:55 160096 kernel: [    0.585766] pcieport 0000:00:1c.2: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.586043]   alloc irq_desc for 27 on node -1
Jul 10 08:47:55 160096 kernel: [    0.586050]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    0.586068] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
Jul 10 08:47:55 160096 kernel: [    0.586086] pcieport 0000:00:1c.3: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.586334] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 10 08:47:55 160096 kernel: [    0.586670] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 10 08:47:55 160096 kernel: [    0.586956] ACPI: AC Adapter [AC] (on-line)
Jul 10 08:47:55 160096 kernel: [    0.587243] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Jul 10 08:47:55 160096 kernel: [    0.590259] ACPI: Lid Switch [LID]
Jul 10 08:47:55 160096 kernel: [    0.590428] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Jul 10 08:47:55 160096 kernel: [    0.590443] ACPI: Power Button [PBTN]
Jul 10 08:47:55 160096 kernel: [    0.590581] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jul 10 08:47:55 160096 kernel: [    0.590590] ACPI: Sleep Button [SBTN]
Jul 10 08:47:55 160096 kernel: [    0.592536] ACPI: SSDT 7f5c29d3 0023F (v01  PmRef   BspIst 00003000 INTL 20050624)
Jul 10 08:47:55 160096 kernel: [    0.593708] ACPI: SSDT 7f5c2de9 005C6 (v01  PmRef   BspCst 00003001 INTL 20050624)
Jul 10 08:47:55 160096 kernel: [    0.594660] Monitor-Mwait will be used to enter C-1 state
Jul 10 08:47:55 160096 kernel: [    0.594761] Monitor-Mwait will be used to enter C-2 state
Jul 10 08:47:55 160096 kernel: [    0.594859] Monitor-Mwait will be used to enter C-3 state
Jul 10 08:47:55 160096 kernel: [    0.594880] Marking TSC unstable due to TSC halts in idle
Jul 10 08:47:55 160096 kernel: [    0.595037] processor LNXCPU:00: registered as cooling_device0
Jul 10 08:47:55 160096 kernel: [    0.596242] ACPI: SSDT 7f5c2c12 001D7 (v01  PmRef    ApIst 00003000 INTL 20050624)
Jul 10 08:47:55 160096 kernel: [    0.597173] ACPI: SSDT 7f5c33af 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
Jul 10 08:47:55 160096 kernel: [    0.597937] Switching to clocksource hpet
Jul 10 08:47:55 160096 kernel: [    0.605277] processor LNXCPU:01: registered as cooling_device1
Jul 10 08:47:55 160096 kernel: [    0.618333] thermal LNXTHERM:01: registered as thermal_zone0
Jul 10 08:47:55 160096 kernel: [    0.618360] ACPI: Thermal Zone [THM] (39 C)
Jul 10 08:47:55 160096 kernel: [    0.623411] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul 10 08:47:55 160096 kernel: [    0.627628] brd: module loaded
Jul 10 08:47:55 160096 kernel: [    0.629273] loop: module loaded
Jul 10 08:47:55 160096 kernel: [    0.629555] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Jul 10 08:47:55 160096 kernel: [    0.630982] Fixed MDIO Bus: probed
Jul 10 08:47:55 160096 kernel: [    0.631097] PPP generic driver version 2.4.2
Jul 10 08:47:55 160096 kernel: [    0.631224] tun: Universal TUN/TAP device driver, 1.6
Jul 10 08:47:55 160096 kernel: [    0.631231] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 10 08:47:55 160096 kernel: [    0.631509] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 10 08:47:55 160096 kernel: [    0.631613] isapnp: Scanning for PnP cards...
Jul 10 08:47:55 160096 kernel: [    0.673464] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 10 08:47:55 160096 kernel: [    0.673513] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.673523] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 10 08:47:55 160096 kernel: [    0.673679] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul 10 08:47:55 160096 kernel: [    0.673737] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Jul 10 08:47:55 160096 kernel: [    0.673759] ehci_hcd 0000:00:1d.7: debug port 1
Jul 10 08:47:55 160096 kernel: [    0.677646] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jul 10 08:47:55 160096 kernel: [    0.677682] ehci_hcd 0000:00:1d.7: irq 22, io mem 0xfed1c000
Jul 10 08:47:55 160096 kernel: [    0.700938] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul 10 08:47:55 160096 kernel: [    0.701215] usb usb1: configuration #1 chosen from 1 choice
Jul 10 08:47:55 160096 kernel: [    0.701304] hub 1-0:1.0: USB hub found
Jul 10 08:47:55 160096 kernel: [    0.701327] hub 1-0:1.0: 8 ports detected
Jul 10 08:47:55 160096 kernel: [    0.701492] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 10 08:47:55 160096 kernel: [    0.701537] uhci_hcd: USB Universal Host Controller Interface driver
Jul 10 08:47:55 160096 kernel: [    0.701617] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 10 08:47:55 160096 kernel: [    0.701639] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.701647] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 10 08:47:55 160096 kernel: [    0.701749] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul 10 08:47:55 160096 kernel: [    0.701796] uhci_hcd 0000:00:1d.0: irq 22, io base 0x0000bf80
Jul 10 08:47:55 160096 kernel: [    0.702047] usb usb2: configuration #1 chosen from 1 choice
Jul 10 08:47:55 160096 kernel: [    0.702123] hub 2-0:1.0: USB hub found
Jul 10 08:47:55 160096 kernel: [    0.702143] hub 2-0:1.0: 2 ports detected
Jul 10 08:47:55 160096 kernel: [    0.702257] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jul 10 08:47:55 160096 kernel: [    0.702274] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.702282] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 10 08:47:55 160096 kernel: [    0.702389] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul 10 08:47:55 160096 kernel: [    0.702447] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
Jul 10 08:47:55 160096 kernel: [    0.702690] usb usb3: configuration #1 chosen from 1 choice
Jul 10 08:47:55 160096 kernel: [    0.702765] hub 3-0:1.0: USB hub found
Jul 10 08:47:55 160096 kernel: [    0.702784] hub 3-0:1.0: 2 ports detected
Jul 10 08:47:55 160096 kernel: [    0.702892] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jul 10 08:47:55 160096 kernel: [    0.702909] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.702917] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 10 08:47:55 160096 kernel: [    0.703009] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jul 10 08:47:55 160096 kernel: [    0.703052] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
Jul 10 08:47:55 160096 kernel: [    0.703297] usb usb4: configuration #1 chosen from 1 choice
Jul 10 08:47:55 160096 kernel: [    0.703373] hub 4-0:1.0: USB hub found
Jul 10 08:47:55 160096 kernel: [    0.703391] hub 4-0:1.0: 2 ports detected
Jul 10 08:47:55 160096 kernel: [    0.703500] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jul 10 08:47:55 160096 kernel: [    0.703517] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    0.703525] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jul 10 08:47:55 160096 kernel: [    0.703611] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jul 10 08:47:55 160096 kernel: [    0.703667] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
Jul 10 08:47:55 160096 kernel: [    0.703922] usb usb5: configuration #1 chosen from 1 choice
Jul 10 08:47:55 160096 kernel: [    0.703998] hub 5-0:1.0: USB hub found
Jul 10 08:47:55 160096 kernel: [    0.704018] hub 5-0:1.0: 2 ports detected
Jul 10 08:47:55 160096 kernel: [    0.704265] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 10 08:47:55 160096 kernel: [    0.704928] i8042.c: Warning: Keylock active.
Jul 10 08:47:55 160096 kernel: [    0.717046] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 10 08:47:55 160096 kernel: [    0.717072] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 10 08:47:55 160096 kernel: [    0.717342] mice: PS/2 mouse device common for all mice
Jul 10 08:47:55 160096 kernel: [    0.717670] rtc_cmos 00:03: RTC can wake from S4
Jul 10 08:47:55 160096 kernel: [    0.717769] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul 10 08:47:55 160096 kernel: [    0.717813] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jul 10 08:47:55 160096 kernel: [    0.718137] device-mapper: uevent: version 1.0.3
Jul 10 08:47:55 160096 kernel: [    0.718428] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jul 10 08:47:55 160096 kernel: [    0.734573] device-mapper: multipath: version 1.1.0 loaded
Jul 10 08:47:55 160096 kernel: [    0.734584] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 10 08:47:55 160096 kernel: [    0.739586] EISA: Probing bus 0 at eisa.0
Jul 10 08:47:55 160096 kernel: [    0.739601] Cannot allocate resource for EISA slot 1
Jul 10 08:47:55 160096 kernel: [    0.739608] Cannot allocate resource for EISA slot 2
Jul 10 08:47:55 160096 kernel: [    0.739614] Cannot allocate resource for EISA slot 3
Jul 10 08:47:55 160096 kernel: [    0.739620] Cannot allocate resource for EISA slot 4
Jul 10 08:47:55 160096 kernel: [    0.739626] Cannot allocate resource for EISA slot 5
Jul 10 08:47:55 160096 kernel: [    0.739648] EISA: Detected 0 cards.
Jul 10 08:47:55 160096 kernel: [    0.760680] cpuidle: using governor ladder
Jul 10 08:47:55 160096 kernel: [    0.761034] cpuidle: using governor menu
Jul 10 08:47:55 160096 kernel: [    0.762206] TCP cubic registered
Jul 10 08:47:55 160096 kernel: [    0.762711] NET: Registered protocol family 10
Jul 10 08:47:55 160096 kernel: [    0.766297] NET: Registered protocol family 17
Jul 10 08:47:55 160096 kernel: [    0.772894] Using IPI No-Shortcut mode
Jul 10 08:47:55 160096 kernel: [    0.773135] PM: Resume from disk failed.
Jul 10 08:47:55 160096 kernel: [    0.773162] registered taskstats version 1
Jul 10 08:47:55 160096 kernel: [    0.777386]   Magic number: 4:371:786
Jul 10 08:47:55 160096 kernel: [    0.777533] rtc_cmos 00:03: setting system clock to 2012-07-10 13:47:32 UTC (1341928052)
Jul 10 08:47:55 160096 kernel: [    0.777543] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 10 08:47:55 160096 kernel: [    0.777548] EDD information not available.
Jul 10 08:47:55 160096 kernel: [    0.785908] Freeing initrd memory: 7815k freed
Jul 10 08:47:55 160096 kernel: [    0.794560] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jul 10 08:47:55 160096 kernel: [    0.822821] ACPI: Battery Slot [BAT0] (battery present)
Jul 10 08:47:55 160096 kernel: [    0.987829] isapnp: No Plug & Play device found
Jul 10 08:47:55 160096 kernel: [    0.987869] Freeing unused kernel memory: 664k freed
Jul 10 08:47:55 160096 kernel: [    0.988441] Write protecting the kernel text: 4700k
Jul 10 08:47:55 160096 kernel: [    0.988573] Write protecting the kernel read-only data: 1848k
Jul 10 08:47:55 160096 kernel: [    1.012571] usb 1-5: new high speed USB device using ehci_hcd and address 2
Jul 10 08:47:55 160096 kernel: [    1.025569] udev: starting version 151
Jul 10 08:47:55 160096 kernel: [    1.275868] usb 1-5: configuration #1 chosen from 1 choice
Jul 10 08:47:55 160096 kernel: [    1.361747] tg3.c:v3.102 (September 1, 2009)
Jul 10 08:47:55 160096 kernel: [    1.361821] tg3 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul 10 08:47:55 160096 kernel: [    1.361843] tg3 0000:09:00.0: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    1.362259] ahci 0000:00:1f.2: version 3.0
Jul 10 08:47:55 160096 kernel: [    1.362290] ahci 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jul 10 08:47:55 160096 kernel: [    1.362359]   alloc irq_desc for 28 on node -1
Jul 10 08:47:55 160096 kernel: [    1.362366]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [    1.362391] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
Jul 10 08:47:55 160096 kernel: [    1.362474] ahci: SSS flag set, parallel bus scan disabled
Jul 10 08:47:55 160096 kernel: [    1.362526] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
Jul 10 08:47:55 160096 kernel: [    1.362537] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part 
Jul 10 08:47:55 160096 kernel: [    1.362550] ahci 0000:00:1f.2: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [    1.362849] scsi0 : ahci
Jul 10 08:47:55 160096 kernel: [    1.363211] scsi1 : ahci
Jul 10 08:47:55 160096 kernel: [    1.363425] scsi2 : ahci
Jul 10 08:47:55 160096 kernel: [    1.363640] scsi3 : ahci
Jul 10 08:47:55 160096 kernel: [    1.364196] ata1: SATA max UDMA/133 abar m1024@0xfed1c800 port 0xfed1c900 irq 28
Jul 10 08:47:55 160096 kernel: [    1.364207] ata2: DUMMY
Jul 10 08:47:55 160096 kernel: [    1.364213] ata3: DUMMY
Jul 10 08:47:55 160096 kernel: [    1.364218] ata4: DUMMY
Jul 10 08:47:55 160096 kernel: [    1.369413] tg3 mdio bus: probed
Jul 10 08:47:55 160096 kernel: [    1.418620] eth0: Tigon3 [partno(BCM957760) rev 57780001] (PCI Express) MAC address 5c:f9:dd:3d:74:0a
Jul 10 08:47:55 160096 kernel: [    1.418628] eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=900:01)
Jul 10 08:47:55 160096 kernel: [    1.418636] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Jul 10 08:47:55 160096 kernel: [    1.418641] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Jul 10 08:47:55 160096 kernel: [    1.684150] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 10 08:47:55 160096 kernel: [    1.686368] ata1.00: ATA-8: ST250LT003-9YG14C, 0003DEM1, max UDMA/133
Jul 10 08:47:55 160096 kernel: [    1.686381] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
Jul 10 08:47:55 160096 kernel: [    1.689206] ata1.00: configured for UDMA/133
Jul 10 08:47:55 160096 kernel: [    1.704401] scsi 0:0:0:0: Direct-Access     ATA      ST250LT003-9YG14 0003 PQ: 0 ANSI: 5
Jul 10 08:47:55 160096 kernel: [    1.704848] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 10 08:47:55 160096 kernel: [    1.705217] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Jul 10 08:47:55 160096 kernel: [    1.705227] sd 0:0:0:0: [sda] 4096-byte physical blocks
Jul 10 08:47:55 160096 kernel: [    1.705429] sd 0:0:0:0: [sda] Write Protect is off
Jul 10 08:47:55 160096 kernel: [    1.705436] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 10 08:47:55 160096 kernel: [    1.705533] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 10 08:47:55 160096 kernel: [    1.706005]  sda: sda1 sda2
Jul 10 08:47:55 160096 kernel: [    1.769036] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 10 08:47:55 160096 kernel: [    7.240151] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jul 10 08:47:55 160096 kernel: [   21.965344] Adding 4882424k swap on /dev/sda2.  Priority:-1 extents:1 across:4882424k 
Jul 10 08:47:55 160096 kernel: [   22.010116] udev: starting version 151
Jul 10 08:47:55 160096 kernel: [   22.182331] lp: driver loaded but no devices found
Jul 10 08:47:55 160096 kernel: [   22.532274] Linux agpgart interface v0.103
Jul 10 08:47:55 160096 kernel: [   22.538675] lib80211: common routines for IEEE802.11 drivers
Jul 10 08:47:55 160096 kernel: [   22.538686] lib80211_crypt: registered algorithm 'NULL'
Jul 10 08:47:55 160096 kernel: [   22.585744] wl: module license 'MIXED/Proprietary' taints kernel.
Jul 10 08:47:55 160096 kernel: [   22.585756] Disabling lock debugging due to kernel taint
Jul 10 08:47:55 160096 kernel: [   22.778296] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 10 08:47:55 160096 kernel: [   22.778315] wl 0000:0c:00.0: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [   22.796489] agpgart-intel 0000:00:00.0: Intel IGD Chipset
Jul 10 08:47:55 160096 kernel: [   22.796835] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
Jul 10 08:47:55 160096 kernel: [   22.849774] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Jul 10 08:47:55 160096 kernel: [   22.901176] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jul 10 08:47:55 160096 kernel: [   22.932958] [drm] Initialized drm 1.1.0 20060810
Jul 10 08:47:55 160096 kernel: [   22.943028] Linux video capture interface: v2.00
Jul 10 08:47:55 160096 kernel: [   22.977495] lib80211_crypt: registered algorithm 'TKIP'
Jul 10 08:47:55 160096 kernel: [   23.012610] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
Jul 10 08:47:55 160096 kernel: [   23.015135] input: Dell WMI hotkeys as /devices/virtual/input/input5
Jul 10 08:47:55 160096 kernel: [   23.020084] type=1505 audit(1341928074.742:2):  operation="profile_load" pid=574 name="/sbin/dhclient3"
Jul 10 08:47:55 160096 kernel: [   23.026410] type=1505 audit(1341928074.746:3):  operation="profile_load" pid=574 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 10 08:47:55 160096 kernel: [   23.026883] type=1505 audit(1341928074.746:4):  operation="profile_load" pid=574 name="/usr/lib/connman/scripts/dhclient-script"
Jul 10 08:47:55 160096 kernel: [   23.027775] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:6426)
Jul 10 08:47:55 160096 kernel: [   23.070187] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input6
Jul 10 08:47:55 160096 kernel: [   23.070365] usbcore: registered new interface driver uvcvideo
Jul 10 08:47:55 160096 kernel: [   23.070376] USB Video Class driver (v0.1.0)
Jul 10 08:47:55 160096 kernel: [   23.173222] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 10 08:47:55 160096 kernel: [   23.173237] i915 0000:00:02.0: setting latency timer to 64
Jul 10 08:47:55 160096 kernel: [   23.186128] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Jul 10 08:47:55 160096 kernel: [   23.186138] [drm] MTRR allocation failed.  Graphics performance may suffer.
Jul 10 08:47:55 160096 kernel: [   23.190414]   alloc irq_desc for 29 on node -1
Jul 10 08:47:55 160096 kernel: [   23.190424]   alloc kstat_irqs on node -1
Jul 10 08:47:55 160096 kernel: [   23.190446] i915 0000:00:02.0: irq 29 for MSI/MSI-X
Jul 10 08:47:55 160096 kernel: [   23.190463] [drm] set up 7M of stolen space
Jul 10 08:47:55 160096 kernel: [   23.305438] [drm] initialized overlay support
Jul 10 08:47:55 160096 kernel: [   23.708814] fb0: inteldrmfb frame buffer device
Jul 10 08:47:55 160096 kernel: [   23.708821] registered panic notifier
Jul 10 08:47:55 160096 kernel: [   23.724294] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04731/0xa40000/0xa0000
Jul 10 08:47:55 160096 kernel: [   23.760303] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
Jul 10 08:47:55 160096 NetworkManager: <info>  starting...
Jul 10 08:47:55 160096 avahi-daemon[718]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Jul 10 08:47:55 160096 avahi-daemon[718]: Successfully dropped root privileges.
Jul 10 08:47:55 160096 avahi-daemon[718]: avahi-daemon 0.6.25 starting up.
Jul 10 08:47:55 160096 avahi-daemon[718]: Successfully called chroot().
Jul 10 08:47:55 160096 avahi-daemon[718]: Successfully dropped remaining capabilities.
Jul 10 08:47:55 160096 avahi-daemon[718]: No service file found in /etc/avahi/services.
Jul 10 08:47:55 160096 NetworkManager: <info>  Trying to start the modem-manager...
Jul 10 08:47:55 160096 kernel: [   23.870535] acpi device:22: registered as cooling_device2
Jul 10 08:47:55 160096 kernel: [   23.874586] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input8
Jul 10 08:47:55 160096 kernel: [   23.875061] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jul 10 08:47:55 160096 kernel: [   23.875253] ACPI Warning for \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) (20090903/nspredef-433)
Jul 10 08:47:55 160096 kernel: [   23.876774] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input9
Jul 10 08:47:55 160096 kernel: [   23.877241] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Jul 10 08:47:55 160096 kernel: [   23.878519] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jul 10 08:47:55 160096 kernel: [   23.878635] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jul 10 08:47:55 160096 kernel: [   23.878708] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jul 10 08:47:55 160096 avahi-daemon[718]: Network interface enumeration completed.
Jul 10 08:47:55 160096 avahi-daemon[718]: Registering HINFO record with values 'I686'/'LINUX'.
Jul 10 08:47:55 160096 avahi-daemon[718]: Server startup complete. Host name is 160096.local. Local service cookie is 3629577023.
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: init!
Jul 10 08:47:55 160096 kernel: [   23.908583] type=1505 audit(1341928075.630:5):  operation="profile_replace" pid=733 name="/sbin/dhclient3"
Jul 10 08:47:55 160096 kernel: [   23.909401] type=1505 audit(1341928075.630:6):  operation="profile_replace" pid=733 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 10 08:47:55 160096 kernel: [   23.909885] type=1505 audit(1341928075.630:7):  operation="profile_replace" pid=733 name="/usr/lib/connman/scripts/dhclient-script"
Jul 10 08:47:55 160096 kernel: [   23.913195] type=1505 audit(1341928075.634:8):  operation="profile_load" pid=732 name="/usr/share/gdm/guest-session/Xsession"
Jul 10 08:47:55 160096 kernel: [   23.918721] vga16fb: initializing
Jul 10 08:47:55 160096 kernel: [   23.918735] vga16fb: mapped to 0xc00a0000
Jul 10 08:47:55 160096 kernel: [   23.918747] vga16fb: not registering due to another framebuffer present
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jul 10 08:47:55 160096 NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1)
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0, iface: eth0)
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: end _init.
Jul 10 08:47:55 160096 NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 10 08:47:55 160096 NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 10 08:47:55 160096 NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/virtual/rfkill/rfkill0) (driver <unknown>)
Jul 10 08:47:55 160096 modem-manager: Loaded plugin AnyData
Jul 10 08:47:55 160096 NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Jul 10 08:47:55 160096 NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: (142598896) ... get_connections.
Jul 10 08:47:55 160096 NetworkManager:    SCPlugin-Ifupdown: (142598896) ... get_connections (managed=false): return empty list.
Jul 10 08:47:55 160096 modem-manager: Loaded plugin Option
Jul 10 08:47:55 160096 modem-manager: Loaded plugin Longcheer
Jul 10 08:47:55 160096 modem-manager: Loaded plugin Gobi
Jul 10 08:47:55 160096 modem-manager: Loaded plugin Generic
Jul 10 08:47:55 160096 modem-manager: Loaded plugin Ericsson MBM
Jul 10 08:47:55 160096 modem-manager: Loaded plugin Novatel
Jul 10 08:47:55 160096 modem-manager: Loaded plugin Option High-Speed
Jul 10 08:47:55 160096 modem-manager: Loaded plugin Huawei
Jul 10 08:47:55 160096 modem-manager: Loaded plugin Sierra
Jul 10 08:47:55 160096 modem-manager: Loaded plugin Nokia
Jul 10 08:47:55 160096 modem-manager: Loaded plugin ZTE
Jul 10 08:47:55 160096 modem-manager: Loaded plugin MotoC
Jul 10 08:47:55 160096 gdm-binary[749]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul 10 08:47:55 160096 NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jul 10 08:47:55 160096 NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01).
Jul 10 08:47:55 160096 NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Jul 10 08:47:55 160096 NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 10 08:47:55 160096 NetworkManager: <info>  (eth1): now managed
Jul 10 08:47:55 160096 NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Jul 10 08:47:55 160096 NetworkManager: <info>  (eth1): bringing up device.
Jul 10 08:47:55 160096 kernel: [   24.016506] type=1505 audit(1341928075.738:9):  operation="profile_load" pid=752 name="/usr/bin/freshclam"
Jul 10 08:47:55 160096 kernel: [   24.051044] type=1505 audit(1341928075.770:10):  operation="profile_load" pid=756 name="/usr/lib/cups/backend/cups-pdf"
Jul 10 08:47:55 160096 kernel: [   24.052079] type=1505 audit(1341928075.774:11):  operation="profile_load" pid=756 name="/usr/sbin/cupsd"
Jul 10 08:47:55 160096 kernel: [   24.076736] [drm] Big FIFO is enabled
Jul 10 08:47:55 160096 kernel: [   24.076756] [drm] Big FIFO is enabled
Jul 10 08:47:55 160096 kernel: [   24.093642] Console: switching to colour frame buffer device 128x37
Jul 10 08:47:55 160096 kernel: [   24.142734] hda_codec: ALC269: BIOS auto-probing.
Jul 10 08:47:55 160096 kernel: [   24.142936] hda_codec: connection list not available for 0x24
Jul 10 08:47:55 160096 kernel: [   24.143387] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth1): preparing device.
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Jul 10 08:47:56 160096 NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth0): carrier is OFF
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3')
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth0): now managed
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth0): bringing up device.
Jul 10 08:47:56 160096 kernel: [   24.456742]   alloc irq_desc for 30 on node -1
Jul 10 08:47:56 160096 kernel: [   24.456751]   alloc kstat_irqs on node -1
Jul 10 08:47:56 160096 kernel: [   24.456811] tg3 0000:09:00.0: irq 30 for MSI/MSI-X
Jul 10 08:47:56 160096 kernel: [   24.513090] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 10 08:47:56 160096 gdm-simple-slave[851]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth0): preparing device.
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jul 10 08:47:56 160096 NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0
Jul 10 08:47:56 160096 NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul 10 08:47:56 160096 NetworkManager: <info>  modem-manager is now available
Jul 10 08:47:56 160096 gdm-binary[749]: WARNING: Unable to find users: no seat-id found
Jul 10 08:47:56 160096 NetworkManager: <info>  Trying to start the supplicant...
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 0)
Jul 10 08:47:56 160096 NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Jul 10 08:47:56 160096 init: apport pre-start process (888) terminated with status 1
Jul 10 08:47:56 160096 acpid: starting up with proc fs
Jul 10 08:47:56 160096 anacron[912]: Anacron 2.3 started on 2012-07-10
Jul 10 08:47:56 160096 init: apport post-stop process (910) terminated with status 1
Jul 10 08:47:56 160096 acpid: 36 rules loaded
Jul 10 08:47:56 160096 acpid: waiting for events: event logging is off
Jul 10 08:47:56 160096 anacron[912]: Normal exit (0 jobs run)
Jul 10 08:47:56 160096 kernel: [   25.067388] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 10 08:47:56 160096 kernel: [   25.245347] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul 10 08:47:56 160096 kernel: [   25.245887] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Jul 10 08:47:56 160096 kernel: [   25.245896] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Jul 10 08:47:56 160096 kernel: [   25.245904] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Jul 10 08:47:57 160096 kernel: [   25.377130] tg3: eth0: Link is down.
Jul 10 08:47:57 160096 acpid: client connected from 993[0:0]
Jul 10 08:47:57 160096 acpid: 1 client rule loaded
Jul 10 08:47:58 160096 avahi-daemon[718]: Registering new address record for fe80::e206:e6ff:fe64:f8ea on eth1.*.
Jul 10 08:48:00 160096 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jul 10 08:48:00 160096 kernel: [   28.381070] tg3: eth0: Link is up at 1000 Mbps, full duplex.
Jul 10 08:48:00 160096 kernel: [   28.381079] tg3: eth0: Flow control is on for TX and on for RX.
Jul 10 08:48:00 160096 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jul 10 08:48:00 160096 kernel: [   28.381612] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jul 10 08:48:00 160096 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 10 08:48:00 160096 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 10 08:48:00 160096 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jul 10 08:48:00 160096 NetworkManager: <info>  dhclient started with pid 1433
Jul 10 08:48:00 160096 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jul 10 08:48:00 160096 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jul 10 08:48:00 160096 dhclient: All rights reserved.
Jul 10 08:48:00 160096 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 10 08:48:00 160096 dhclient: 
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jul 10 08:48:00 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jul 10 08:48:00 160096 NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jul 10 08:48:00 160096 dhclient: Listening on LPF/eth0/5c:f9:dd:3d:74:0a
Jul 10 08:48:00 160096 dhclient: Sending on   LPF/eth0/5c:f9:dd:3d:74:0a
Jul 10 08:48:00 160096 dhclient: Sending on   Socket/fallback
Jul 10 08:48:00 160096 gdm-session-worker[1442]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul 10 08:48:01 160096 rtkit-daemon[1450]: Sucessfully called chroot.
Jul 10 08:48:01 160096 rtkit-daemon[1450]: Sucessfully dropped privileges.
Jul 10 08:48:01 160096 rtkit-daemon[1450]: Sucessfully limited resources.
Jul 10 08:48:01 160096 rtkit-daemon[1450]: Running.
Jul 10 08:48:01 160096 rtkit-daemon[1450]: Watchdog thread running.
Jul 10 08:48:01 160096 rtkit-daemon[1450]: Canary thread running.
Jul 10 08:48:01 160096 polkitd[1454]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jul 10 08:48:01 160096 avahi-daemon[718]: Registering new address record for fe80::5ef9:ddff:fe3d:740a on eth0.*.
Jul 10 08:48:01 160096 rtkit-daemon[1450]: Sucessfully made thread 1448 of process 1448 (n/a) owned by '114' high priority at nice level -11.
Jul 10 08:48:01 160096 rtkit-daemon[1450]: Supervising 1 threads of 1 processes of 1 users.
Jul 10 08:48:01 160096 anacron[1489]: Anacron 2.3 started on 2012-07-10
Jul 10 08:48:01 160096 anacron[1489]: Normal exit (0 jobs run)
Jul 10 08:48:01 160096 kernel: [   30.132627] CPU0 attaching NULL sched-domain.
Jul 10 08:48:01 160096 kernel: [   30.132643] CPU1 attaching NULL sched-domain.
Jul 10 08:48:01 160096 kernel: [   30.152721] CPU0 attaching sched-domain:
Jul 10 08:48:01 160096 kernel: [   30.152733]  domain 0: span 0-1 level SIBLING
Jul 10 08:48:01 160096 kernel: [   30.152741]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Jul 10 08:48:01 160096 kernel: [   30.152760]   domain 1: span 0-1 level MC
Jul 10 08:48:01 160096 kernel: [   30.152768]    groups: 0-1 (cpu_power = 1178)
Jul 10 08:48:01 160096 kernel: [   30.152785] CPU1 attaching sched-domain:
Jul 10 08:48:01 160096 kernel: [   30.152793]  domain 0: span 0-1 level SIBLING
Jul 10 08:48:01 160096 kernel: [   30.152801]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Jul 10 08:48:01 160096 kernel: [   30.152818]   domain 1: span 0-1 level MC
Jul 10 08:48:01 160096 kernel: [   30.152826]    groups: 0-1 (cpu_power = 1178)
Jul 10 08:48:02 160096 rtkit-daemon[1450]: Sucessfully made thread 1494 of process 1448 (n/a) owned by '114' RT at priority 5.
Jul 10 08:48:02 160096 rtkit-daemon[1450]: Supervising 2 threads of 1 processes of 1 users.
Jul 10 08:48:02 160096 rtkit-daemon[1450]: Sucessfully made thread 1497 of process 1448 (n/a) owned by '114' RT at priority 5.
Jul 10 08:48:02 160096 rtkit-daemon[1450]: Supervising 3 threads of 1 processes of 1 users.
Jul 10 08:48:02 160096 kernel: [   30.883630] ppdev: user-space parallel port driver
Jul 10 08:48:02 160096 gdm-simple-greeter[1440]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jul 10 08:48:03 160096 gdm-simple-greeter[1440]: WARNING: Unable to parse history: (null)   1#012
Jul 10 08:48:03 160096 init: plymouth-stop pre-start process (1601) terminated with status 1
Jul 10 08:48:04 160096 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jul 10 08:48:04 160096 dhclient: DHCPOFFER of 10.9.6.77 from 10.9.1.2
Jul 10 08:48:04 160096 dhclient: DHCPREQUEST of 10.9.6.77 on eth0 to 255.255.255.255 port 67
Jul 10 08:48:04 160096 dhclient: DHCPACK of 10.9.6.77 from 10.9.1.2
Jul 10 08:48:04 160096 NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jul 10 08:48:04 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 10 08:48:04 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 10 08:48:04 160096 NetworkManager: <info>    address 10.9.6.77
Jul 10 08:48:04 160096 NetworkManager: <info>    prefix 16 (255.255.0.0)
Jul 10 08:48:04 160096 NetworkManager: <info>    gateway 10.9.0.2
Jul 10 08:48:04 160096 NetworkManager: <info>    nameserver '10.9.1.4'
Jul 10 08:48:04 160096 NetworkManager: <info>    nameserver '10.9.1.2'
Jul 10 08:48:04 160096 NetworkManager: <info>    domain name 'mchs.com'
Jul 10 08:48:04 160096 NetworkManager: <info>    wins '10.9.1.2'
Jul 10 08:48:04 160096 NetworkManager: <info>    wins '10.9.1.4'
Jul 10 08:48:04 160096 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 10 08:48:04 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 10 08:48:04 160096 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jul 10 08:48:04 160096 avahi-daemon[718]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.9.6.77.
Jul 10 08:48:04 160096 avahi-daemon[718]: New relevant interface eth0.IPv4 for mDNS.
Jul 10 08:48:04 160096 avahi-daemon[718]: Registering new address record for 10.9.6.77 on eth0.IPv4.
Jul 10 08:48:04 160096 dhclient: bound to 10.9.6.77 -- renewal in 195028 seconds.
Jul 10 08:48:05 160096 NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jul 10 08:48:05 160096 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jul 10 08:48:05 160096 NetworkManager: <info>  Activation (eth0) successful, device activated.
Jul 10 08:48:05 160096 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 10 08:48:06 160096 ntpdate[1641]: step time server 10.9.1.2 offset 1.523011 sec
Jul 10 08:48:08 160096 kernel: [   35.420518] eth1: no IPv6 routers present
Jul 10 08:48:12 160096 kernel: [   39.044023] eth0: no IPv6 routers present
Jul 10 08:49:22 160096 gdm-session-worker[1442]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jul 10 08:49:28 160096 rtkit-daemon[1450]: Sucessfully made thread 2137 of process 2137 (n/a) owned by '1001' high priority at nice level -11.
Jul 10 08:49:28 160096 rtkit-daemon[1450]: Supervising 4 threads of 2 processes of 2 users.
Jul 10 08:49:28 160096 rtkit-daemon[1450]: Sucessfully made thread 2140 of process 2137 (n/a) owned by '1001' RT at priority 5.
Jul 10 08:49:28 160096 rtkit-daemon[1450]: Supervising 5 threads of 2 processes of 2 users.
Jul 10 08:49:28 160096 rtkit-daemon[1450]: Sucessfully made thread 2142 of process 2137 (n/a) owned by '1001' RT at priority 5.
Jul 10 08:49:28 160096 rtkit-daemon[1450]: Supervising 6 threads of 2 processes of 2 users.
Jul 10 08:49:29 160096 rtkit-daemon[1450]: Sucessfully made thread 2147 of process 2147 (n/a) owned by '1001' high priority at nice level -11.
Jul 10 08:49:29 160096 rtkit-daemon[1450]: Supervising 7 threads of 3 processes of 2 users.
Jul 10 08:49:29 160096 pulseaudio[2147]: pid.c: Daemon already running.
Jul 10 09:13:52 160096 kernel: [ 1579.530822] No module found in object
Jul 10 09:13:58 160096 kernel: [ 1585.064345] No module found in object
Jul 10 09:16:36 160096 kernel: [ 1743.068295] tg3 0000:09:00.0: PME# enabled
Jul 10 09:16:36 160096 avahi-daemon[718]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 10 09:16:36 160096 avahi-daemon[718]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.9.6.77.
Jul 10 09:16:36 160096 NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jul 10 09:16:36 160096 dhclient: receive_packet failed on eth0: Network is down
Jul 10 09:16:36 160096 NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0, iface: eth0)
Jul 10 09:16:36 160096 NetworkManager: <info>  (eth0): now unmanaged
Jul 10 09:16:36 160096 NetworkManager: <info>  (eth0): device state change: 8 -> 1 (reason 36)
Jul 10 09:16:36 160096 NetworkManager: <info>  (eth0): deactivating device (reason: 36).
Jul 10 09:16:36 160096 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1433
Jul 10 09:16:36 160096 avahi-daemon[718]: Withdrawing address record for fe80::5ef9:ddff:fe3d:740a on eth0.
Jul 10 09:16:36 160096 avahi-daemon[718]: Withdrawing address record for 10.9.6.77 on eth0.
Jul 10 09:16:36 160096 NetworkManager: <info>  (eth0): cleaning up...
Jul 10 09:16:36 160096 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jul 10 09:16:36 160096 nm-dispatcher.action: Error in get_property: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist#012
Jul 10 09:16:36 160096 kernel: [ 1743.360235] tg3 0000:09:00.0: PCI INT A disabled
Jul 10 09:16:57 160096 kernel: [ 1763.951314] tg3.c:v3.122n (March 09, 2012)
Jul 10 09:16:57 160096 kernel: [ 1763.951320] 
Jul 10 09:16:57 160096 kernel: [ 1763.964683] tg3 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul 10 09:16:57 160096 kernel: [ 1763.964707] tg3 0000:09:00.0: setting latency timer to 64
Jul 10 09:16:57 160096 kernel: [ 1764.021037] pcieport 0000:00:1c.3: eth0: Tigon3 [partno(BCM957760) rev 57780001] (PCI Express) MAC address 5c:f9:dd:3d:74:0a
Jul 10 09:16:57 160096 kernel: [ 1764.021052] pcieport 0000:00:1c.3: eth0: attached PHY is 57780 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Jul 10 09:16:57 160096 kernel: [ 1764.021063] pcieport 0000:00:1c.3: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Jul 10 09:16:57 160096 kernel: [ 1764.021072] pcieport 0000:00:1c.3: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Jul 10 09:16:57 160096 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0, iface: eth0)
Jul 10 09:16:57 160096 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 10 09:16:57 160096 NetworkManager: <info>  (eth0): carrier is OFF
Jul 10 09:16:57 160096 NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3')
Jul 10 09:16:57 160096 NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/2
Jul 10 09:16:57 160096 NetworkManager: <info>  (eth0): now managed
Jul 10 09:16:57 160096 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jul 10 09:16:57 160096 kernel: [ 1764.036412] tg3 0000:09:00.0: PME# disabled
Jul 10 09:16:57 160096 kernel: [ 1764.037793] tg3 0000:09:00.0: irq 30 for MSI/MSI-X
Jul 10 09:16:58 160096 NetworkManager: <info>  (eth0): bringing up device.
Jul 10 09:16:58 160096 NetworkManager: <info>  (eth0): preparing device.
Jul 10 09:16:58 160096 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jul 10 09:16:58 160096 kernel: [ 1764.852739] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 10 09:16:58 160096 NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0
Jul 10 09:17:00 160096 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jul 10 09:17:00 160096 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jul 10 09:17:00 160096 kernel: [ 1767.273033] pcieport 0000:00:1c.3: eth0: Link is up at 1000 Mbps, full duplex
Jul 10 09:17:00 160096 kernel: [ 1767.273046] pcieport 0000:00:1c.3: eth0: Flow control is on for TX and on for RX
Jul 10 09:17:00 160096 kernel: [ 1767.273681] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jul 10 09:17:00 160096 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 10 09:17:00 160096 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 10 09:17:00 160096 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jul 10 09:17:00 160096 NetworkManager: <info>  dhclient started with pid 5098
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jul 10 09:17:00 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jul 10 09:17:00 160096 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jul 10 09:17:00 160096 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jul 10 09:17:00 160096 dhclient: All rights reserved.
Jul 10 09:17:00 160096 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 10 09:17:00 160096 dhclient: 
Jul 10 09:17:00 160096 NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jul 10 09:17:00 160096 dhclient: Listening on LPF/eth0/5c:f9:dd:3d:74:0a
Jul 10 09:17:00 160096 dhclient: Sending on   LPF/eth0/5c:f9:dd:3d:74:0a
Jul 10 09:17:00 160096 dhclient: Sending on   Socket/fallback
Jul 10 09:17:02 160096 avahi-daemon[718]: Registering new address record for fe80::5ef9:ddff:fe3d:740a on eth0.*.
Jul 10 09:17:03 160096 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jul 10 09:17:03 160096 dhclient: DHCPOFFER of 10.9.6.77 from 10.9.1.2
Jul 10 09:17:03 160096 dhclient: DHCPREQUEST of 10.9.6.77 on eth0 to 255.255.255.255 port 67
Jul 10 09:17:03 160096 dhclient: DHCPACK of 10.9.6.77 from 10.9.1.2
Jul 10 09:17:03 160096 dhclient: bound to 10.9.6.77 -- renewal in 181184 seconds.
Jul 10 09:17:03 160096 NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jul 10 09:17:03 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 10 09:17:03 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 10 09:17:03 160096 NetworkManager: <info>    address 10.9.6.77
Jul 10 09:17:03 160096 NetworkManager: <info>    prefix 16 (255.255.0.0)
Jul 10 09:17:03 160096 NetworkManager: <info>    gateway 10.9.0.2
Jul 10 09:17:03 160096 NetworkManager: <info>    nameserver '10.9.1.4'
Jul 10 09:17:03 160096 NetworkManager: <info>    nameserver '10.9.1.2'
Jul 10 09:17:03 160096 NetworkManager: <info>    domain name 'mchs.com'
Jul 10 09:17:03 160096 NetworkManager: <info>    wins '10.9.1.2'
Jul 10 09:17:03 160096 NetworkManager: <info>    wins '10.9.1.4'
Jul 10 09:17:03 160096 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 10 09:17:03 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 10 09:17:03 160096 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jul 10 09:17:03 160096 avahi-daemon[718]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.9.6.77.
Jul 10 09:17:03 160096 avahi-daemon[718]: New relevant interface eth0.IPv4 for mDNS.
Jul 10 09:17:03 160096 avahi-daemon[718]: Registering new address record for 10.9.6.77 on eth0.IPv4.
Jul 10 09:17:04 160096 NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jul 10 09:17:04 160096 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jul 10 09:17:04 160096 NetworkManager: <info>  Activation (eth0) successful, device activated.
Jul 10 09:17:04 160096 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 10 09:17:04 160096 ntpdate[5144]: adjust time server 10.9.1.2 offset 0.003501 sec
Jul 10 09:17:11 160096 kernel: [ 1778.112113] eth0: no IPv6 routers present
Jul 10 09:19:02 160096 kernel: Kernel logging (proc) stopped.
Jul 10 09:19:02 160096 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="689" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul 10 09:19:44 160096 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 10 09:19:44 160096 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="709" x-info="http://www.rsyslog.com"] (re)start
Jul 10 09:19:44 160096 rsyslogd: rsyslogd's groupid changed to 103
Jul 10 09:19:44 160096 rsyslogd: rsyslogd's userid changed to 101
Jul 10 09:19:44 160096 rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul 10 09:19:44 160096 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 10 09:19:44 160096 kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 10 09:19:44 160096 kernel: [    0.000000] Linux version 2.6.32-41-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #90-Ubuntu SMP Tue May 22 11:31:25 UTC 2012 (Ubuntu 2.6.32-41.90-generic 2.6.32.59+drm33.24)
Jul 10 09:19:44 160096 kernel: [    0.000000] KERNEL supported cpus:
Jul 10 09:19:44 160096 kernel: [    0.000000]   Intel GenuineIntel
Jul 10 09:19:44 160096 kernel: [    0.000000]   AMD AuthenticAMD
Jul 10 09:19:44 160096 kernel: [    0.000000]   NSC Geode by NSC
Jul 10 09:19:44 160096 kernel: [    0.000000]   Cyrix CyrixInstead
Jul 10 09:19:44 160096 kernel: [    0.000000]   Centaur CentaurHauls
Jul 10 09:19:44 160096 kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 10 09:19:44 160096 kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 10 09:19:44 160096 kernel: [    0.000000]   UMC UMC UMC UMC
Jul 10 09:19:44 160096 kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5bf400 (usable)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 000000007f5bf400 - 000000007f5c1400 (ACPI NVS)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 000000007f5c1400 - 0000000080000000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda7000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000] DMI 2.4 present.
Jul 10 09:19:44 160096 kernel: [    0.000000] last_pfn = 0x7f5bf max_arch_pfn = 0x100000
Jul 10 09:19:44 160096 kernel: [    0.000000] MTRR default type: uncachable
Jul 10 09:19:44 160096 kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 10 09:19:44 160096 kernel: [    0.000000]   00000-9FFFF write-back
Jul 10 09:19:44 160096 kernel: [    0.000000]   A0000-BFFFF uncachable
Jul 10 09:19:44 160096 kernel: [    0.000000]   C0000-CFFFF write-protect
Jul 10 09:19:44 160096 kernel: [    0.000000]   D0000-EFFFF uncachable
Jul 10 09:19:44 160096 kernel: [    0.000000]   F0000-FFFFF write-protect
Jul 10 09:19:44 160096 kernel: [    0.000000] MTRR variable ranges enabled:
Jul 10 09:19:44 160096 kernel: [    0.000000]   0 base 000000000 mask 000000000 write-back
Jul 10 09:19:44 160096 kernel: [    0.000000]   1 base 0E0000000 mask 0E0000000 uncachable
Jul 10 09:19:44 160096 kernel: [    0.000000]   2 base 07F700000 mask 0FFF00000 uncachable
Jul 10 09:19:44 160096 kernel: [    0.000000]   3 base 07F800000 mask 0FF800000 uncachable
Jul 10 09:19:44 160096 kernel: [    0.000000]   4 base 07F600000 mask FFFF00000 write-through
Jul 10 09:19:44 160096 kernel: [    0.000000]   5 base 07F600000 mask FFFF00000 write-through
Jul 10 09:19:44 160096 kernel: [    0.000000]   6 base 07F600000 mask FFFF00000 write-through
Jul 10 09:19:44 160096 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 10 09:19:44 160096 kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 10 09:19:44 160096 kernel: [    0.000000] modified physical RAM map:
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 0000000000100000 - 000000007f5bf400 (usable)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 000000007f5bf400 - 000000007f5c1400 (ACPI NVS)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 000000007f5c1400 - 0000000080000000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 00000000feda0000 - 00000000feda7000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Jul 10 09:19:44 160096 kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Jul 10 09:19:44 160096 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jul 10 09:19:44 160096 kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jul 10 09:19:44 160096 kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jul 10 09:19:44 160096 kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jul 10 09:19:44 160096 kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jul 10 09:19:44 160096 kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Jul 10 09:19:44 160096 kernel: [    0.000000] RAMDISK: 3784e000 - 37feff9b
Jul 10 09:19:44 160096 kernel: [    0.000000] Allocated new RAMDISK: 008ea000 - 0108bf9b
Jul 10 09:19:44 160096 kernel: [    0.000000] Move RAMDISK from 000000003784e000 - 0000000037feff9a to 008ea000 - 0108bf9a
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: RSDP 000fbe70 00024 (v02 DELL  )
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: XSDT 7f5c3e00 0005C (v01 DELL    M09     27DB0A1F ASL  00000061)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: FACP 7f5c3c9c 000F4 (v04 DELL    M09     27DB0A1F ASL  00000061)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: DSDT 7f5c4400 05A7D (v02 INT430 SYSFexxx 00001001 INTL 20050624)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: FACS 7f5d2c00 00040
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: HPET 7f5c3f00 00038 (v01 DELL    M09     00000001 ASL  00000061)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: APIC 7f5c4000 00078 (v01 DELL    M09     27DB0A1F ASL  00000047)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: ASF! 7f5c3c00 00076 (v32 DELL    M09     27DB0A1F ASL  00000061)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: MCFG 7f5c3fc0 0003C (v16 DELL    M09     27DB0A1F ASL  00000061)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: SLIC 7f5c409c 00176 (v01 DELL    M09     27DB0A1F ASL  00000061)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: SSDT 7f5c2367 0066C (v01  PmRef    CpuPm 00003000 INTL 20050624)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 10 09:19:44 160096 kernel: [    0.000000] 1149MB HIGHMEM available.
Jul 10 09:19:44 160096 kernel: [    0.000000] 887MB LOWMEM available.
Jul 10 09:19:44 160096 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jul 10 09:19:44 160096 kernel: [    0.000000]   low ram: 0 - 377fe000
Jul 10 09:19:44 160096 kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jul 10 09:19:44 160096 kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Jul 10 09:19:44 160096 kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jul 10 09:19:44 160096 kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jul 10 09:19:44 160096 kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jul 10 09:19:44 160096 kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jul 10 09:19:44 160096 kernel: [    0.000000]   #3 [0000100000 - 00008e5f18]    TEXT DATA BSS ==> [0000100000 - 00008e5f18]
Jul 10 09:19:44 160096 kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Jul 10 09:19:44 160096 kernel: [    0.000000]   #5 [00008e6000 - 00008e9184]              BRK ==> [00008e6000 - 00008e9184]
Jul 10 09:19:44 160096 kernel: [    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Jul 10 09:19:44 160096 kernel: [    0.000000]   #7 [00008ea000 - 000108bf9b]      NEW RAMDISK ==> [00008ea000 - 000108bf9b]
Jul 10 09:19:44 160096 kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Jul 10 09:19:44 160096 kernel: [    0.000000] Zone PFN ranges:
Jul 10 09:19:44 160096 kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jul 10 09:19:44 160096 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jul 10 09:19:44 160096 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007f5bf
Jul 10 09:19:44 160096 kernel: [    0.000000] Movable zone start PFN for each node
Jul 10 09:19:44 160096 kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul 10 09:19:44 160096 kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Jul 10 09:19:44 160096 kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Jul 10 09:19:44 160096 kernel: [    0.000000]     0: 0x00000100 -> 0x0007f5bf
Jul 10 09:19:44 160096 kernel: [    0.000000] On node 0 totalpages: 521562
Jul 10 09:19:44 160096 kernel: [    0.000000] free_area_init_node: node 0, pgdat c07a0a20, node_mem_map c108d000
Jul 10 09:19:44 160096 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 10 09:19:44 160096 kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 10 09:19:44 160096 kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Jul 10 09:19:44 160096 kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jul 10 09:19:44 160096 kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Jul 10 09:19:44 160096 kernel: [    0.000000]   HighMem zone: 2300 pages used for memmap
Jul 10 09:19:44 160096 kernel: [    0.000000]   HighMem zone: 292037 pages, LIFO batch:31
Jul 10 09:19:44 160096 kernel: [    0.000000] Using APIC driver default
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul 10 09:19:44 160096 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 10 09:19:44 160096 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 10 09:19:44 160096 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jul 10 09:19:44 160096 kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul 10 09:19:44 160096 kernel: [    0.000000] nr_irqs_gsi: 24
Jul 10 09:19:44 160096 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 10 09:19:44 160096 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 10 09:19:44 160096 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Jul 10 09:19:44 160096 kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
Jul 10 09:19:44 160096 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 10 09:19:44 160096 kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jul 10 09:19:44 160096 kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u1048576
Jul 10 09:19:44 160096 kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
Jul 10 09:19:44 160096 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 10 09:19:44 160096 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517486
Jul 10 09:19:44 160096 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-41-generic root=UUID=dab19fca-2dbe-4769-af3e-61a711b51c94 ro quiet splash
Jul 10 09:19:44 160096 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 10 09:19:44 160096 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 10 09:19:44 160096 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 10 09:19:44 160096 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul 10 09:19:44 160096 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul 10 09:19:44 160096 kernel: [    0.000000] Initializing CPU#0
Jul 10 09:19:44 160096 kernel: [    0.000000] allocated 10433260 bytes of page_cgroup
Jul 10 09:19:44 160096 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 10 09:19:44 160096 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007f5bf)
Jul 10 09:19:44 160096 kernel: [    0.000000] Memory: 2041480k/2086652k available (4699k kernel code, 43524k reserved, 2128k data, 664k init, 1177348k highmem)
Jul 10 09:19:44 160096 kernel: [    0.000000] virtual kernel memory layout:
Jul 10 09:19:44 160096 kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jul 10 09:19:44 160096 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 10 09:19:44 160096 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jul 10 09:19:44 160096 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jul 10 09:19:44 160096 kernel: [    0.000000]       .init : 0xc07ab000 - 0xc0851000   ( 664 kB)
Jul 10 09:19:44 160096 avahi-daemon[730]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Jul 10 09:19:44 160096 avahi-daemon[730]: Successfully dropped root privileges.
Jul 10 09:19:44 160096 avahi-daemon[730]: avahi-daemon 0.6.25 starting up.
Jul 10 09:19:44 160096 NetworkManager: <info>  starting...
Jul 10 09:19:44 160096 avahi-daemon[730]: Successfully called chroot().
Jul 10 09:19:44 160096 avahi-daemon[730]: Successfully dropped remaining capabilities.
Jul 10 09:19:44 160096 NetworkManager: <info>  Trying to start the modem-manager...
Jul 10 09:19:44 160096 avahi-daemon[730]: No service file found in /etc/avahi/services.
Jul 10 09:19:44 160096 kernel: [    0.000000]       .data : 0xc0596c47 - 0xc07aafc8   (2128 kB)
Jul 10 09:19:44 160096 kernel: [    0.000000]       .text : 0xc0100000 - 0xc0596c47   (4699 kB)
Jul 10 09:19:44 160096 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 10 09:19:44 160096 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 10 09:19:44 160096 kernel: [    0.000000] Hierarchical RCU implementation.
Jul 10 09:19:44 160096 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Jul 10 09:19:44 160096 kernel: [    0.000000] Extended CMOS year: 2000
Jul 10 09:19:44 160096 kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 10 09:19:44 160096 kernel: [    0.000000] console [tty0] enabled
Jul 10 09:19:44 160096 kernel: [    0.000000] hpet clockevent registered
Jul 10 09:19:44 160096 kernel: [    0.000000] Fast TSC calibration using PIT
Jul 10 09:19:44 160096 kernel: [    0.000000] Detected 1662.634 MHz processor.
Jul 10 09:19:44 160096 kernel: [    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.26 BogoMIPS (lpj=6650536)
Jul 10 09:19:44 160096 kernel: [    0.004046] Security Framework initialized
Jul 10 09:19:44 160096 kernel: [    0.004084] AppArmor: AppArmor initialized
Jul 10 09:19:44 160096 kernel: [    0.004101] Mount-cache hash table entries: 512
Jul 10 09:19:44 160096 kernel: [    0.004338] Initializing cgroup subsys ns
Jul 10 09:19:44 160096 kernel: [    0.004348] Initializing cgroup subsys cpuacct
Jul 10 09:19:44 160096 kernel: [    0.004358] Initializing cgroup subsys memory
Jul 10 09:19:44 160096 kernel: [    0.004371] Initializing cgroup subsys devices
Jul 10 09:19:44 160096 kernel: [    0.004377] Initializing cgroup subsys freezer
Jul 10 09:19:44 160096 kernel: [    0.004383] Initializing cgroup subsys net_cls
Jul 10 09:19:44 160096 kernel: [    0.004421] CPU: L1 I cache: 32K, L1 D cache: 24K
Jul 10 09:19:44 160096 kernel: [    0.004428] CPU: L2 cache: 512K
Jul 10 09:19:44 160096 kernel: [    0.004433] CPU: Physical Processor ID: 0
Jul 10 09:19:44 160096 kernel: [    0.004438] CPU: Processor Core ID: 0
Jul 10 09:19:44 160096 kernel: [    0.004444] mce: CPU supports 5 MCE banks
Jul 10 09:19:44 160096 kernel: [    0.004457] CPU0: Thermal monitoring enabled (TM2)
Jul 10 09:19:44 160096 kernel: [    0.004465] using mwait in idle threads.
Jul 10 09:19:44 160096 kernel: [    0.004477] Performance Events: Atom events, Intel PMU driver.
Jul 10 09:19:44 160096 kernel: [    0.004492] ... version:                3
Jul 10 09:19:44 160096 kernel: [    0.004496] ... bit width:              40
Jul 10 09:19:44 160096 kernel: [    0.004501] ... generic registers:      2
Jul 10 09:19:44 160096 kernel: [    0.004506] ... value mask:             000000ffffffffff
Jul 10 09:19:44 160096 kernel: [    0.004511] ... max period:             000000007fffffff
Jul 10 09:19:44 160096 kernel: [    0.004516] ... fixed-purpose events:   3
Jul 10 09:19:44 160096 kernel: [    0.004520] ... event mask:             0000000700000003
Jul 10 09:19:44 160096 kernel: [    0.004529] Checking 'hlt' instruction... OK.
Jul 10 09:19:44 160096 kernel: [    0.020008] Disabling 4MB page tables to avoid TLB bug
Jul 10 09:19:44 160096 kernel: [    0.024309] ACPI: Core revision 20090903
Jul 10 09:19:44 160096 kernel: [    0.040018] ftrace: converting mcount calls to 0f 1f 44 00 00
Jul 10 09:19:44 160096 kernel: [    0.040030] ftrace: allocating 21840 entries in 43 pages
Jul 10 09:19:44 160096 kernel: [    0.044113] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 10 09:19:44 160096 kernel: [    0.044513] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 10 09:19:44 160096 kernel: [    0.085479] CPU0: Intel(R) Atom(TM) CPU N455   @ 1.66GHz stepping 0a
Jul 10 09:19:44 160096 kernel: [    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
Jul 10 09:19:44 160096 kernel: [    0.008000] Initializing CPU#1
Jul 10 09:19:44 160096 kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
Jul 10 09:19:44 160096 kernel: [    0.008000] CPU: L2 cache: 512K
Jul 10 09:19:44 160096 kernel: [    0.008000] CPU: Physical Processor ID: 0
Jul 10 09:19:44 160096 kernel: [    0.008000] CPU: Processor Core ID: 0
Jul 10 09:19:44 160096 kernel: [    0.008000] CPU1: Thermal monitoring enabled (TM2)
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: init!
Jul 10 09:19:44 160096 kernel: [    0.172052] CPU1: Intel(R) Atom(TM) CPU N455   @ 1.66GHz stepping 0a
Jul 10 09:19:44 160096 kernel: [    0.172068] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul 10 09:19:44 160096 kernel: [    0.176042] Brought up 2 CPUs
Jul 10 09:19:44 160096 kernel: [    0.176050] Total of 2 processors activated (6650.27 BogoMIPS).
Jul 10 09:19:44 160096 kernel: [    0.176463] CPU0 attaching sched-domain:
Jul 10 09:19:44 160096 kernel: [    0.176472]  domain 0: span 0-1 level SIBLING
Jul 10 09:19:44 160096 kernel: [    0.176477]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Jul 10 09:19:44 160096 kernel: [    0.176490]   domain 1: span 0-1 level MC
Jul 10 09:19:44 160096 kernel: [    0.176495]    groups: 0-1 (cpu_power = 1178)
Jul 10 09:19:44 160096 kernel: [    0.176506] CPU1 attaching sched-domain:
Jul 10 09:19:44 160096 kernel: [    0.176510]  domain 0: span 0-1 level SIBLING
Jul 10 09:19:44 160096 kernel: [    0.176515]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Jul 10 09:19:44 160096 kernel: [    0.176526]   domain 1: span 0-1 level MC
Jul 10 09:19:44 160096 kernel: [    0.176531]    groups: 0-1 (cpu_power = 1178)
Jul 10 09:19:44 160096 kernel: [    0.176702] devtmpfs: initialized
Jul 10 09:19:44 160096 kernel: [    0.176702] regulator: core version 0.5
Jul 10 09:19:44 160096 kernel: [    0.176702] Time: 14:19:20  Date: 07/10/12
Jul 10 09:19:44 160096 kernel: [    0.176702] NET: Registered protocol family 16
Jul 10 09:19:44 160096 kernel: [    0.176702] Trying to unpack rootfs image as initramfs...
Jul 10 09:19:44 160096 kernel: [    0.176702] EISA bus registered
Jul 10 09:19:44 160096 kernel: [    0.176702] ACPI: bus type pci registered
Jul 10 09:19:44 160096 kernel: [    0.176735] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Jul 10 09:19:44 160096 kernel: [    0.176744] PCI: MCFG area at f8000000 reserved in E820
Jul 10 09:19:44 160096 kernel: [    0.176750] PCI: Using MMCONFIG for extended config space
Jul 10 09:19:44 160096 kernel: [    0.176756] PCI: Using configuration type 1 for base access
Jul 10 09:19:44 160096 kernel: [    0.181927] bio: create slab <bio-0> at 0
Jul 10 09:19:44 160096 kernel: [    0.184043] ACPI: EC: Look up EC in DSDT
Jul 10 09:19:44 160096 kernel: [    0.184624] ACPI: BIOS _OSI(Linux) query ignored
Jul 10 09:19:44 160096 kernel: [    0.228439] ACPI: Interpreter enabled
Jul 10 09:19:44 160096 kernel: [    0.228453] ACPI: (supports S0 S3 S4 S5)
Jul 10 09:19:44 160096 kernel: [    0.228521] ACPI: Using IOAPIC for interrupt routing
Jul 10 09:19:44 160096 kernel: [    0.309112] ACPI: EC: GPE = 0x19, I/O: command/status = 0x934, data = 0x930
Jul 10 09:19:44 160096 kernel: [    0.309795] ACPI: No dock devices found.
Jul 10 09:19:44 160096 kernel: [    0.357611] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 10 09:19:44 160096 kernel: [    0.357819] pci 0000:00:02.0: reg 10 32bit mmio: [0xf6e00000-0xf6e7ffff]
Jul 10 09:19:44 160096 kernel: [    0.357832] pci 0000:00:02.0: reg 14 io port: [0xeff8-0xefff]
Jul 10 09:19:44 160096 kernel: [    0.357844] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xe0000000-0xefffffff]
Jul 10 09:19:44 160096 kernel: [    0.357855] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf6f00000-0xf6ffffff]
Jul 10 09:19:44 160096 kernel: [    0.357926] pci 0000:00:02.1: reg 10 32bit mmio: [0xf6e80000-0xf6efffff]
Jul 10 09:19:44 160096 kernel: [    0.358092] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6dfc000-0xf6dfffff]
Jul 10 09:19:44 160096 kernel: [    0.358206] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul 10 09:19:44 160096 kernel: [    0.358218] pci 0000:00:1b.0: PME# disabled
Jul 10 09:19:44 160096 kernel: [    0.358384] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul 10 09:19:44 160096 kernel: [    0.358397] pci 0000:00:1c.0: PME# disabled
Jul 10 09:19:44 160096 kernel: [    0.358574] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jul 10 09:19:44 160096 kernel: [    0.358586] pci 0000:00:1c.1: PME# disabled
Jul 10 09:19:44 160096 kernel: [    0.358753] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jul 10 09:19:44 160096 kernel: [    0.358763] pci 0000:00:1c.2: PME# disabled
Jul 10 09:19:44 160096 kernel: [    0.358930] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jul 10 09:19:44 160096 kernel: [    0.358941] pci 0000:00:1c.3: PME# disabled
Jul 10 09:19:44 160096 kernel: [    0.359040] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
Jul 10 09:19:44 160096 kernel: [    0.359143] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
Jul 10 09:19:44 160096 kernel: [    0.359252] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
Jul 10 09:19:44 160096 kernel: [    0.359355] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
Jul 10 09:19:44 160096 kernel: [    0.359473] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
Jul 10 09:19:44 160096 kernel: [    0.359591] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul 10 09:19:44 160096 kernel: [    0.359602] pci 0000:00:1d.7: PME# disabled
Jul 10 09:19:44 160096 kernel: [    0.359960] pci 0000:00:1f.2: reg 10 io port: [0x6e70-0x6e77]
Jul 10 09:19:44 160096 kernel: [    0.359976] pci 0000:00:1f.2: reg 14 io port: [0x6e78-0x6e7b]
Jul 10 09:19:44 160096 kernel: [    0.360022] pci 0000:00:1f.2: reg 18 io port: [0x6e80-0x6e87]
Jul 10 09:19:44 160096 kernel: [    0.360037] pci 0000:00:1f.2: reg 1c io port: [0x6e88-0x6e8b]
Jul 10 09:19:44 160096 kernel: [    0.360052] pci 0000:00:1f.2: reg 20 io port: [0x6ea0-0x6ebf]
Jul 10 09:19:44 160096 kernel: [    0.360068] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfed1c800-0xfed1cbff]
Jul 10 09:19:44 160096 kernel: [    0.360154] pci 0000:00:1f.2: PME# supported from D3hot
Jul 10 09:19:44 160096 kernel: [    0.360165] pci 0000:00:1f.2: PME# disabled
Jul 10 09:19:44 160096 kernel: [    0.360250] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
Jul 10 09:19:44 160096 kernel: [    0.360522] pci 0000:0c:00.0: reg 10 64bit mmio: [0xf6cfc000-0xf6cfffff]
Jul 10 09:19:44 160096 kernel: [    0.360750] pci 0000:0c:00.0: supports D1 D2
Jul 10 09:19:44 160096 kernel: [    0.360759] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
Jul 10 09:19:44 160096 kernel: [    0.360772] pci 0000:0c:00.0: PME# disabled
Jul 10 09:19:44 160096 kernel: [    0.360907] pci 0000:00:1c.1: bridge 32bit mmio: [0xf6c00000-0xf6cfffff]
Jul 10 09:19:44 160096 kernel: [    0.361110] pci 0000:0d:00.0: reg 10 32bit mmio: [0xf6bf0000-0xf6bfffff]
Jul 10 09:19:44 160096 kernel: [    0.361522] pci 0000:0d:00.0: supports D1 D2
Jul 10 09:19:44 160096 kernel: [    0.361530] pci 0000:0d:00.0: PME# supported from D1 D2 D3hot
Jul 10 09:19:44 160096 kernel: [    0.361550] pci 0000:0d:00.0: PME# disabled
Jul 10 09:19:44 160096 kernel: [    0.361718] pci 0000:00:1c.2: bridge 32bit mmio: [0xf6b00000-0xf6bfffff]
Jul 10 09:19:44 160096 kernel: [    0.361888] pci 0000:09:00.0: reg 10 64bit mmio: [0xf6af0000-0xf6afffff]
Jul 10 09:19:44 160096 kernel: [    0.362108] pci 0000:09:00.0: PME# supported from D3hot D3cold
Jul 10 09:19:44 160096 kernel: [    0.362124] pci 0000:09:00.0: PME# disabled
Jul 10 09:19:44 160096 kernel: [    0.362262] pci 0000:00:1c.3: bridge 32bit mmio: [0xf6a00000-0xf6afffff]
Jul 10 09:19:44 160096 kernel: [    0.362361] pci 0000:00:1e.0: transparent bridge
Jul 10 09:19:44 160096 kernel: [    0.362423] pci_bus 0000:00: on NUMA node 0
Jul 10 09:19:44 160096 kernel: [    0.362445] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 10 09:19:44 160096 kernel: [    0.363144] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Jul 10 09:19:44 160096 kernel: [    0.363503] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jul 10 09:19:44 160096 kernel: [    0.363727] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Jul 10 09:19:44 160096 kernel: [    0.363938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Jul 10 09:19:44 160096 kernel: [    0.364182] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Jul 10 09:19:44 160096 kernel: [    0.398177] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
Jul 10 09:19:44 160096 kernel: [    0.398507] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Jul 10 09:19:44 160096 kernel: [    0.398832] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *3
Jul 10 09:19:44 160096 kernel: [    0.399162] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *10 11)
Jul 10 09:19:44 160096 kernel: [    0.399439] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul 10 09:19:44 160096 kernel: [    0.399787] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jul 10 09:19:44 160096 kernel: [    0.400155] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Jul 10 09:19:44 160096 kernel: [    0.400491] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jul 10 09:19:44 160096 kernel: [    0.400871] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jul 10 09:19:44 160096 kernel: [    0.400906] vgaarb: loaded
Jul 10 09:19:44 160096 kernel: [    0.401235] SCSI subsystem initialized
Jul 10 09:19:44 160096 kernel: [    0.401487] libata version 3.00 loaded.
Jul 10 09:19:44 160096 kernel: [    0.401738] usbcore: registered new interface driver usbfs
Jul 10 09:19:44 160096 kernel: [    0.401780] usbcore: registered new interface driver hub
Jul 10 09:19:44 160096 kernel: [    0.401865] usbcore: registered new device driver usb
Jul 10 09:19:44 160096 kernel: [    0.402361] ACPI: WMI: Mapper loaded
Jul 10 09:19:44 160096 kernel: [    0.402368] PCI: Using ACPI for IRQ routing
Jul 10 09:19:44 160096 kernel: [    0.402837] NetLabel: Initializing
Jul 10 09:19:44 160096 kernel: [    0.402844] NetLabel:  domain hash size = 128
Jul 10 09:19:44 160096 kernel: [    0.402849] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 10 09:19:44 160096 kernel: [    0.402881] NetLabel:  unlabeled traffic allowed by default
Jul 10 09:19:44 160096 kernel: [    0.402983] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul 10 09:19:44 160096 kernel: [    0.402998] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 10 09:19:44 160096 kernel: [    0.403012] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jul 10 09:19:44 160096 kernel: [    0.408055] Switching to clocksource tsc
Jul 10 09:19:44 160096 kernel: [    0.412897] AppArmor: AppArmor Filesystem Enabled
Jul 10 09:19:44 160096 kernel: [    0.412934] pnp: PnP ACPI init
Jul 10 09:19:44 160096 kernel: [    0.412972] ACPI: bus type pnp registered
Jul 10 09:19:44 160096 kernel: [    0.462387]   alloc irq_desc for 20 on node -1
Jul 10 09:19:44 160096 kernel: [    0.462396]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    0.518231] pnp: PnP ACPI: found 13 devices
Jul 10 09:19:44 160096 kernel: [    0.518240] ACPI: ACPI bus type pnp unregistered
Jul 10 09:19:44 160096 kernel: [    0.518250] PnPBIOS: Disabled by ACPI PNP
Jul 10 09:19:44 160096 kernel: [    0.518284] system 00:05: ioport range 0xc80-0xcff could not be reserved
Jul 10 09:19:44 160096 kernel: [    0.518307] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518326] system 00:0a: ioport range 0x900-0x92f has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518336] system 00:0a: ioport range 0x931-0x933 has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518345] system 00:0a: ioport range 0x935-0x97f has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518355] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518364] system 00:0a: ioport range 0x1000-0x1005 has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518374] system 00:0a: ioport range 0x1008-0x100f has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518394] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518403] system 00:0b: ioport range 0x1006-0x1007 has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518413] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
Jul 10 09:19:44 160096 kernel: [    0.518422] system 00:0b: ioport range 0x1060-0x107f has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518432] system 00:0b: ioport range 0x1080-0x10bf has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518441] system 00:0b: ioport range 0x10c0-0x10df has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518451] system 00:0b: ioport range 0x1010-0x102f has been reserved
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jul 10 09:19:44 160096 kernel: [    0.518460] system 00:0b: ioport range 0x809-0x809 has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518479] system 00:0c: iomem range 0x0-0x9efff could not be reserved
Jul 10 09:19:44 160096 kernel: [    0.518489] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
Jul 10 09:19:44 160096 kernel: [    0.518499] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Jul 10 09:19:44 160096 kernel: [    0.518508] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Jul 10 09:19:44 160096 kernel: [    0.518518] system 00:0c: iomem range 0x100000-0x7f5bf3ff could not be reserved
Jul 10 09:19:44 160096 kernel: [    0.518528] system 00:0c: iomem range 0x7f5bf400-0x7f5fffff could not be reserved
Jul 10 09:19:44 160096 kernel: [    0.518538] system 00:0c: iomem range 0x7f600000-0x7f6fffff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518548] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518558] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518569] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
Jul 10 09:19:44 160096 kernel: [    0.518579] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518589] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518599] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518609] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518619] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518629] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518639] system 00:0c: iomem range 0xfed1c800-0xfed1cfff could not be reserved
Jul 10 09:19:44 160096 kernel: [    0.518649] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.518659] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
Jul 10 09:19:44 160096 kernel: [    0.553849] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
Jul 10 09:19:44 160096 kernel: [    0.553861] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
Jul 10 09:19:44 160096 kernel: [    0.553875] pci 0000:00:1c.0:   MEM window: 0x80000000-0x801fffff
Jul 10 09:19:44 160096 kernel: [    0.553887] pci 0000:00:1c.0:   PREFETCH window: 0x00000080200000-0x000000803fffff
Jul 10 09:19:44 160096 NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jul 10 09:19:44 160096 kernel: [    0.553903] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
Jul 10 09:19:44 160096 kernel: [    0.553912] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
Jul 10 09:19:44 160096 kernel: [    0.553924] pci 0000:00:1c.1:   MEM window: 0xf6c00000-0xf6cfffff
Jul 10 09:19:44 160096 kernel: [    0.553936] pci 0000:00:1c.1:   PREFETCH window: 0x00000080400000-0x000000805fffff
Jul 10 09:19:44 160096 kernel: [    0.553951] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:0d
Jul 10 09:19:44 160096 kernel: [    0.553960] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
Jul 10 09:19:44 160096 kernel: [    0.553973] pci 0000:00:1c.2:   MEM window: 0xf6b00000-0xf6bfffff
Jul 10 09:19:44 160096 kernel: [    0.553984] pci 0000:00:1c.2:   PREFETCH window: 0x00000080600000-0x000000807fffff
Jul 10 09:19:44 160096 kernel: [    0.554000] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:09
Jul 10 09:19:44 160096 kernel: [    0.554010] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
Jul 10 09:19:44 160096 kernel: [    0.554024] pci 0000:00:1c.3:   MEM window: 0xf6a00000-0xf6afffff
Jul 10 09:19:44 160096 kernel: [    0.554036] pci 0000:00:1c.3:   PREFETCH window: 0x00000080800000-0x000000809fffff
Jul 10 09:19:44 160096 kernel: [    0.554053] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Jul 10 09:19:44 160096 kernel: [    0.554059] pci 0000:00:1e.0:   IO window: disabled
Jul 10 09:19:44 160096 kernel: [    0.554071] pci 0000:00:1e.0:   MEM window: disabled
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1)
Jul 10 09:19:44 160096 kernel: [    0.554082] pci 0000:00:1e.0:   PREFETCH window: disabled
Jul 10 09:19:44 160096 kernel: [    0.554125]   alloc irq_desc for 16 on node -1
Jul 10 09:19:44 160096 kernel: [    0.554133]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    0.554150] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 10 09:19:44 160096 kernel: [    0.554165] pci 0000:00:1c.0: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.554189]   alloc irq_desc for 17 on node -1
Jul 10 09:19:44 160096 kernel: [    0.554196]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jul 10 09:19:44 160096 kernel: [    0.554210] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul 10 09:19:44 160096 kernel: [    0.554221] pci 0000:00:1c.1: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.554243]   alloc irq_desc for 18 on node -1
Jul 10 09:19:44 160096 kernel: [    0.554249]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0, iface: eth0)
Jul 10 09:19:44 160096 kernel: [    0.554260] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul 10 09:19:44 160096 kernel: [    0.554271] pci 0000:00:1c.2: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.554291]   alloc irq_desc for 19 on node -1
Jul 10 09:19:44 160096 kernel: [    0.554297]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    0.554308] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 10 09:19:44 160096 kernel: [    0.554319] pci 0000:00:1c.3: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.554338] pci 0000:00:1e.0: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.554349] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jul 10 09:19:44 160096 kernel: [    0.554358] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 10 09:19:44 160096 kernel: [    0.554366] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
Jul 10 09:19:44 160096 kernel: [    0.554374] pci_bus 0000:0b: resource 1 mem: [0x80000000-0x801fffff]
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 10 09:19:44 160096 kernel: [    0.554383] pci_bus 0000:0b: resource 2 pref mem [0x80200000-0x803fffff]
Jul 10 09:19:44 160096 kernel: [    0.554391] pci_bus 0000:0c: resource 0 io:  [0x3000-0x3fff]
Jul 10 09:19:44 160096 kernel: [    0.554399] pci_bus 0000:0c: resource 1 mem: [0xf6c00000-0xf6cfffff]
Jul 10 09:19:44 160096 kernel: [    0.554408] pci_bus 0000:0c: resource 2 pref mem [0x80400000-0x805fffff]
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: end _init.
Jul 10 09:19:44 160096 kernel: [    0.554416] pci_bus 0000:0d: resource 0 io:  [0x4000-0x4fff]
Jul 10 09:19:44 160096 kernel: [    0.554424] pci_bus 0000:0d: resource 1 mem: [0xf6b00000-0xf6bfffff]
Jul 10 09:19:44 160096 kernel: [    0.554433] pci_bus 0000:0d: resource 2 pref mem [0x80600000-0x807fffff]
Jul 10 09:19:44 160096 kernel: [    0.554441] pci_bus 0000:09: resource 0 io:  [0x5000-0x5fff]
Jul 10 09:19:44 160096 kernel: [    0.554450] pci_bus 0000:09: resource 1 mem: [0xf6a00000-0xf6afffff]
Jul 10 09:19:44 160096 NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 10 09:19:44 160096 kernel: [    0.554458] pci_bus 0000:09: resource 2 pref mem [0x80800000-0x809fffff]
Jul 10 09:19:44 160096 kernel: [    0.554467] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
Jul 10 09:19:44 160096 kernel: [    0.554475] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
Jul 10 09:19:44 160096 kernel: [    0.554569] NET: Registered protocol family 2
Jul 10 09:19:44 160096 kernel: [    0.554849] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 10 09:19:44 160096 kernel: [    0.555783] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 10 09:19:44 160096 kernel: [    0.556869] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 10 09:19:44 160096 kernel: [    0.557376] TCP: Hash tables configured (established 131072 bind 65536)
Jul 10 09:19:44 160096 kernel: [    0.557387] TCP reno registered
Jul 10 09:19:44 160096 kernel: [    0.557645] NET: Registered protocol family 1
Jul 10 09:19:44 160096 kernel: [    0.557702] pci 0000:00:02.0: Boot video device
Jul 10 09:19:44 160096 kernel: [    0.557754]   alloc irq_desc for 22 on node -1
Jul 10 09:19:44 160096 kernel: [    0.557761]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    0.557780] pci 0000:00:1d.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 10 09:19:44 160096 kernel: [    0.557815] pci 0000:00:1d.0: PCI INT A disabled
Jul 10 09:19:44 160096 kernel: [    0.557838]   alloc irq_desc for 21 on node -1
Jul 10 09:19:44 160096 kernel: [    0.557845]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    0.557858] pci 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jul 10 09:19:44 160096 kernel: [    0.557892] pci 0000:00:1d.1: PCI INT B disabled
Jul 10 09:19:44 160096 kernel: [    0.557915] pci 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jul 10 09:19:44 160096 kernel: [    0.557948] pci 0000:00:1d.2: PCI INT C disabled
Jul 10 09:19:44 160096 kernel: [    0.557968]   alloc irq_desc for 23 on node -1
Jul 10 09:19:44 160096 kernel: [    0.557975]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    0.557987] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jul 10 09:19:44 160096 kernel: [    0.558019] pci 0000:00:1d.3: PCI INT D disabled
Jul 10 09:19:44 160096 kernel: [    0.558047] pci 0000:00:1d.7: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 10 09:19:44 160096 kernel: [    0.558095] pci 0000:00:1d.7: PCI INT A disabled
Jul 10 09:19:44 160096 kernel: [    0.558616] cpufreq-nforce2: No nForce2 chipset.
Jul 10 09:19:44 160096 kernel: [    0.558695] Scanning for low memory corruption every 60 seconds
Jul 10 09:19:44 160096 kernel: [    0.559026] audit: initializing netlink socket (disabled)
Jul 10 09:19:44 160096 kernel: [    0.559052] type=2000 audit(1341929960.555:1): initialized
Jul 10 09:19:44 160096 kernel: [    0.580014] highmem bounce pool size: 64 pages
Jul 10 09:19:44 160096 kernel: [    0.580033] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jul 10 09:19:44 160096 kernel: [    0.585222] VFS: Disk quotas dquot_6.5.2
Jul 10 09:19:44 160096 kernel: [    0.585418] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 10 09:19:44 160096 kernel: [    0.587419] fuse init (API version 7.13)
Jul 10 09:19:44 160096 kernel: [    0.587700] msgmni has been set to 1690
Jul 10 09:19:44 160096 kernel: [    0.588384] alg: No test for stdrng (krng)
Jul 10 09:19:44 160096 kernel: [    0.588573] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul 10 09:19:44 160096 kernel: [    0.588582] io scheduler noop registered
Jul 10 09:19:44 160096 kernel: [    0.588588] io scheduler anticipatory registered
Jul 10 09:19:44 160096 kernel: [    0.588594] io scheduler deadline registered
Jul 10 09:19:44 160096 kernel: [    0.588729] io scheduler cfq registered (default)
Jul 10 09:19:44 160096 kernel: [    0.589085]   alloc irq_desc for 24 on node -1
Jul 10 09:19:44 160096 kernel: [    0.589094]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    0.589116] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Jul 10 09:19:44 160096 kernel: [    0.589135] pcieport 0000:00:1c.0: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.589411]   alloc irq_desc for 25 on node -1
Jul 10 09:19:44 160096 kernel: [    0.589417]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    0.589435] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
Jul 10 09:19:44 160096 kernel: [    0.589453] pcieport 0000:00:1c.1: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.589731]   alloc irq_desc for 26 on node -1
Jul 10 09:19:44 160096 kernel: [    0.589738]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    0.589756] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
Jul 10 09:19:44 160096 kernel: [    0.589774] pcieport 0000:00:1c.2: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.590046]   alloc irq_desc for 27 on node -1
Jul 10 09:19:44 160096 kernel: [    0.590053]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    0.590070] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
Jul 10 09:19:44 160096 kernel: [    0.590089] pcieport 0000:00:1c.3: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.590339] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 10 09:19:44 160096 kernel: [    0.590680] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 10 09:19:44 160096 kernel: [    0.590969] ACPI: AC Adapter [AC] (on-line)
Jul 10 09:19:44 160096 kernel: [    0.591267] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Jul 10 09:19:44 160096 kernel: [    0.594169] ACPI: Lid Switch [LID]
Jul 10 09:19:44 160096 kernel: [    0.594336] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Jul 10 09:19:44 160096 kernel: [    0.594350] ACPI: Power Button [PBTN]
Jul 10 09:19:44 160096 kernel: [    0.594494] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jul 10 09:19:44 160096 kernel: [    0.594504] ACPI: Sleep Button [SBTN]
Jul 10 09:19:44 160096 kernel: [    0.596429] ACPI: SSDT 7f5c29d3 0023F (v01  PmRef   BspIst 00003000 INTL 20050624)
Jul 10 09:19:44 160096 kernel: [    0.597601] ACPI: SSDT 7f5c2de9 005C6 (v01  PmRef   BspCst 00003001 INTL 20050624)
Jul 10 09:19:44 160096 kernel: [    0.598548] Monitor-Mwait will be used to enter C-1 state
Jul 10 09:19:44 160096 kernel: [    0.598652] Monitor-Mwait will be used to enter C-2 state
Jul 10 09:19:44 160096 kernel: [    0.598738] Monitor-Mwait will be used to enter C-3 state
Jul 10 09:19:44 160096 kernel: [    0.598759] Marking TSC unstable due to TSC halts in idle
Jul 10 09:19:44 160096 kernel: [    0.598937] processor LNXCPU:00: registered as cooling_device0
Jul 10 09:19:44 160096 kernel: [    0.600161] ACPI: SSDT 7f5c2c12 001D7 (v01  PmRef    ApIst 00003000 INTL 20050624)
Jul 10 09:19:44 160096 kernel: [    0.601086] ACPI: SSDT 7f5c33af 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
Jul 10 09:19:44 160096 kernel: [    0.601844] Switching to clocksource hpet
Jul 10 09:19:44 160096 kernel: [    0.609092] processor LNXCPU:01: registered as cooling_device1
Jul 10 09:19:44 160096 kernel: [    0.622108] thermal LNXTHERM:01: registered as thermal_zone0
Jul 10 09:19:44 160096 kernel: [    0.622135] ACPI: Thermal Zone [THM] (48 C)
Jul 10 09:19:44 160096 NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 10 09:19:44 160096 kernel: [    0.627199] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jul 10 09:19:44 160096 kernel: [    0.631436] brd: module loaded
Jul 10 09:19:44 160096 kernel: [    0.633105] loop: module loaded
Jul 10 09:19:44 160096 kernel: [    0.633380] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Jul 10 09:19:44 160096 kernel: [    0.634832] Fixed MDIO Bus: probed
Jul 10 09:19:44 160096 kernel: [    0.634954] PPP generic driver version 2.4.2
Jul 10 09:19:44 160096 kernel: [    0.635093] tun: Universal TUN/TAP device driver, 1.6
Jul 10 09:19:44 160096 kernel: [    0.635100] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 10 09:19:44 160096 kernel: [    0.635373] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 10 09:19:44 160096 kernel: [    0.635424] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 10 09:19:44 160096 kernel: [    0.635464] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.635474] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 10 09:19:44 160096 kernel: [    0.635576] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul 10 09:19:44 160096 kernel: [    0.635634] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Jul 10 09:19:44 160096 kernel: [    0.635657] ehci_hcd 0000:00:1d.7: debug port 1
Jul 10 09:19:44 160096 kernel: [    0.639566] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jul 10 09:19:44 160096 kernel: [    0.639637] ehci_hcd 0000:00:1d.7: irq 22, io mem 0xfed1c000
Jul 10 09:19:44 160096 kernel: [    0.643561] isapnp: Scanning for PnP cards...
Jul 10 09:19:44 160096 kernel: [    0.726450] ACPI: Battery Slot [BAT0] (battery present)
Jul 10 09:19:44 160096 kernel: [    0.736505] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul 10 09:19:44 160096 kernel: [    0.736810] usb usb1: configuration #1 chosen from 1 choice
Jul 10 09:19:44 160096 kernel: [    0.736904] hub 1-0:1.0: USB hub found
Jul 10 09:19:44 160096 kernel: [    0.736927] hub 1-0:1.0: 8 ports detected
Jul 10 09:19:44 160096 kernel: [    0.737107] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 10 09:19:44 160096 kernel: [    0.737157] uhci_hcd: USB Universal Host Controller Interface driver
Jul 10 09:19:44 160096 kernel: [    0.737241] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul 10 09:19:44 160096 kernel: [    0.737263] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.737272] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 10 09:19:44 160096 kernel: [    0.737390] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul 10 09:19:44 160096 kernel: [    0.737440] uhci_hcd 0000:00:1d.0: irq 22, io base 0x0000bf80
Jul 10 09:19:44 160096 kernel: [    0.737713] usb usb2: configuration #1 chosen from 1 choice
Jul 10 09:19:44 160096 kernel: [    0.737796] hub 2-0:1.0: USB hub found
Jul 10 09:19:44 160096 kernel: [    0.737822] hub 2-0:1.0: 2 ports detected
Jul 10 09:19:44 160096 kernel: [    0.737948] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jul 10 09:19:44 160096 kernel: [    0.737967] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.737976] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 10 09:19:44 160096 kernel: [    0.738076] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul 10 09:19:44 160096 kernel: [    0.738145] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
Jul 10 09:19:44 160096 kernel: [    0.738437] usb usb3: configuration #1 chosen from 1 choice
Jul 10 09:19:44 160096 kernel: [    0.738524] hub 3-0:1.0: USB hub found
Jul 10 09:19:44 160096 kernel: [    0.738546] hub 3-0:1.0: 2 ports detected
Jul 10 09:19:44 160096 kernel: [    0.738676] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Jul 10 09:19:44 160096 kernel: [    0.738696] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.738705] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 10 09:19:44 160096 kernel: [    0.738828] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jul 10 09:19:44 160096 kernel: [    0.738875] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
Jul 10 09:19:44 160096 kernel: [    0.739145] usb usb4: configuration #1 chosen from 1 choice
Jul 10 09:19:44 160096 kernel: [    0.739233] hub 4-0:1.0: USB hub found
Jul 10 09:19:44 160096 kernel: [    0.739255] hub 4-0:1.0: 2 ports detected
Jul 10 09:19:44 160096 kernel: [    0.739385] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jul 10 09:19:44 160096 kernel: [    0.739403] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    0.739412] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jul 10 09:19:44 160096 kernel: [    0.739525] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jul 10 09:19:44 160096 kernel: [    0.739587] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
Jul 10 09:19:44 160096 kernel: [    0.739901] usb usb5: configuration #1 chosen from 1 choice
Jul 10 09:19:44 160096 kernel: [    0.739986] hub 5-0:1.0: USB hub found
Jul 10 09:19:44 160096 kernel: [    0.740056] hub 5-0:1.0: 2 ports detected
Jul 10 09:19:44 160096 kernel: [    0.740331] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 10 09:19:44 160096 kernel: [    0.741083] i8042.c: Warning: Keylock active.
Jul 10 09:19:44 160096 kernel: [    0.744237] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 10 09:19:44 160096 kernel: [    0.744263] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 10 09:19:44 160096 kernel: [    0.744689] mice: PS/2 mouse device common for all mice
Jul 10 09:19:44 160096 kernel: [    0.745111] rtc_cmos 00:03: RTC can wake from S4
Jul 10 09:19:44 160096 kernel: [    0.745231] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul 10 09:19:44 160096 kernel: [    0.745281] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jul 10 09:19:44 160096 kernel: [    0.745684] device-mapper: uevent: version 1.0.3
Jul 10 09:19:44 160096 kernel: [    0.770611] Freeing initrd memory: 7815k freed
Jul 10 09:19:44 160096 kernel: [    0.777358] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jul 10 09:19:44 160096 kernel: [    0.777610] device-mapper: multipath: version 1.1.0 loaded
Jul 10 09:19:44 160096 kernel: [    0.777619] device-mapper: multipath round-robin: version 1.0.0 loaded
Jul 10 09:19:44 160096 kernel: [    0.777978] EISA: Probing bus 0 at eisa.0
Jul 10 09:19:44 160096 kernel: [    0.777993] Cannot allocate resource for EISA slot 1
Jul 10 09:19:44 160096 kernel: [    0.778000] Cannot allocate resource for EISA slot 2
Jul 10 09:19:44 160096 kernel: [    0.778006] Cannot allocate resource for EISA slot 3
Jul 10 09:19:44 160096 kernel: [    0.778012] Cannot allocate resource for EISA slot 4
Jul 10 09:19:44 160096 kernel: [    0.778018] Cannot allocate resource for EISA slot 5
Jul 10 09:19:44 160096 kernel: [    0.778040] EISA: Detected 0 cards.
Jul 10 09:19:44 160096 kernel: [    0.778452] cpuidle: using governor ladder
Jul 10 09:19:44 160096 kernel: [    0.778777] cpuidle: using governor menu
Jul 10 09:19:44 160096 kernel: [    0.779934] TCP cubic registered
Jul 10 09:19:44 160096 kernel: [    0.780432] NET: Registered protocol family 10
Jul 10 09:19:44 160096 kernel: [    0.782585] NET: Registered protocol family 17
Jul 10 09:19:44 160096 kernel: [    0.785302] Using IPI No-Shortcut mode
Jul 10 09:19:44 160096 kernel: [    0.785546] PM: Resume from disk failed.
Jul 10 09:19:44 160096 kernel: [    0.785584] registered taskstats version 1
Jul 10 09:19:44 160096 kernel: [    0.786486]   Magic number: 4:512:333
Jul 10 09:19:44 160096 kernel: [    0.786520] tty tty54: hash matches
Jul 10 09:19:44 160096 kernel: [    0.786629] rtc_cmos 00:03: setting system clock to 2012-07-10 14:19:21 UTC (1341929961)
Jul 10 09:19:44 160096 kernel: [    0.786638] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 10 09:19:44 160096 kernel: [    0.786643] EDD information not available.
Jul 10 09:19:44 160096 kernel: [    0.788099] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jul 10 09:19:44 160096 kernel: [    1.007850] isapnp: No Plug & Play device found
Jul 10 09:19:44 160096 kernel: [    1.007896] Freeing unused kernel memory: 664k freed
Jul 10 09:19:44 160096 kernel: [    1.008485] Write protecting the kernel text: 4700k
Jul 10 09:19:44 160096 kernel: [    1.008590] Write protecting the kernel read-only data: 1848k
Jul 10 09:19:44 160096 kernel: [    1.045265] udev: starting version 151
Jul 10 09:19:44 160096 kernel: [    1.088109] usb 1-5: new high speed USB device using ehci_hcd and address 2
Jul 10 09:19:44 160096 kernel: [    1.324605] tg3.c:v3.102 (September 1, 2009)
Jul 10 09:19:44 160096 kernel: [    1.324678] tg3 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul 10 09:19:44 160096 kernel: [    1.324702] tg3 0000:09:00.0: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    1.332963] tg3 mdio bus: probed
Jul 10 09:19:44 160096 kernel: [    1.352056] usb 1-5: configuration #1 chosen from 1 choice
Jul 10 09:19:44 160096 kernel: [    1.401212] ahci 0000:00:1f.2: version 3.0
Jul 10 09:19:44 160096 kernel: [    1.401246] ahci 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jul 10 09:19:44 160096 kernel: [    1.401321]   alloc irq_desc for 28 on node -1
Jul 10 09:19:44 160096 kernel: [    1.401329]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [    1.401354] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
Jul 10 09:19:44 160096 kernel: [    1.401438] ahci: SSS flag set, parallel bus scan disabled
Jul 10 09:19:44 160096 kernel: [    1.401490] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
Jul 10 09:19:44 160096 kernel: [    1.401502] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part 
Jul 10 09:19:44 160096 kernel: [    1.401514] ahci 0000:00:1f.2: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [    1.401824] scsi0 : ahci
Jul 10 09:19:44 160096 kernel: [    1.402168] scsi1 : ahci
Jul 10 09:19:44 160096 kernel: [    1.402402] scsi2 : ahci
Jul 10 09:19:44 160096 kernel: [    1.402616] scsi3 : ahci
Jul 10 09:19:44 160096 kernel: [    1.403191] ata1: SATA max UDMA/133 abar m1024@0xfed1c800 port 0xfed1c900 irq 28
Jul 10 09:19:44 160096 NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/virtual/rfkill/rfkill0) (driver <unknown>)
Jul 10 09:19:44 160096 kernel: [    1.403202] ata2: DUMMY
Jul 10 09:19:44 160096 kernel: [    1.403208] ata3: DUMMY
Jul 10 09:19:44 160096 kernel: [    1.403213] ata4: DUMMY
Jul 10 09:19:44 160096 kernel: [    1.405419] eth0: Tigon3 [partno(BCM957760) rev 57780001] (PCI Express) MAC address 5c:f9:dd:3d:74:0a
Jul 10 09:19:44 160096 kernel: [    1.405431] eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=900:01)
Jul 10 09:19:44 160096 kernel: [    1.405441] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Jul 10 09:19:44 160096 kernel: [    1.405449] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Jul 10 09:19:44 160096 kernel: [    1.720144] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 10 09:19:44 160096 kernel: [    1.722357] ata1.00: ATA-8: ST250LT003-9YG14C, 0003DEM1, max UDMA/133
Jul 10 09:19:44 160096 kernel: [    1.722370] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
Jul 10 09:19:44 160096 kernel: [    1.725028] ata1.00: configured for UDMA/133
Jul 10 09:19:44 160096 kernel: [    1.740410] scsi 0:0:0:0: Direct-Access     ATA      ST250LT003-9YG14 0003 PQ: 0 ANSI: 5
Jul 10 09:19:44 160096 kernel: [    1.740859] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 10 09:19:44 160096 kernel: [    1.741215] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Jul 10 09:19:44 160096 kernel: [    1.741225] sd 0:0:0:0: [sda] 4096-byte physical blocks
Jul 10 09:19:44 160096 kernel: [    1.741419] sd 0:0:0:0: [sda] Write Protect is off
Jul 10 09:19:44 160096 kernel: [    1.741427] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 10 09:19:44 160096 kernel: [    1.741524] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 10 09:19:44 160096 kernel: [    1.742001]  sda: sda1 sda2
Jul 10 09:19:44 160096 kernel: [    1.791016] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 10 09:19:44 160096 kernel: [    7.294035] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jul 10 09:19:44 160096 kernel: [   22.084848] Adding 4882424k swap on /dev/sda2.  Priority:-1 extents:1 across:4882424k 
Jul 10 09:19:44 160096 kernel: [   22.122712] udev: starting version 151
Jul 10 09:19:44 160096 kernel: [   22.419590] lp: driver loaded but no devices found
Jul 10 09:19:44 160096 kernel: [   22.724783] Linux agpgart interface v0.103
Jul 10 09:19:44 160096 kernel: [   22.785190] lib80211: common routines for IEEE802.11 drivers
Jul 10 09:19:44 160096 kernel: [   22.785199] lib80211_crypt: registered algorithm 'NULL'
Jul 10 09:19:44 160096 kernel: [   22.788634] agpgart-intel 0000:00:00.0: Intel IGD Chipset
Jul 10 09:19:44 160096 kernel: [   22.788937] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
Jul 10 09:19:44 160096 kernel: [   22.867516] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Jul 10 09:19:44 160096 kernel: [   22.921029] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jul 10 09:19:44 160096 kernel: [   22.924128] Linux video capture interface: v2.00
Jul 10 09:19:44 160096 kernel: [   22.929694] wl: module license 'MIXED/Proprietary' taints kernel.
Jul 10 09:19:44 160096 kernel: [   22.929705] Disabling lock debugging due to kernel taint
Jul 10 09:19:44 160096 kernel: [   23.055121] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 10 09:19:44 160096 kernel: [   23.055140] wl 0000:0c:00.0: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [   23.089454] [drm] Initialized drm 1.1.0 20060810
Jul 10 09:19:44 160096 kernel: [   23.205395] type=1505 audit(1341929983.917:2):  operation="profile_load" pid=604 name="/sbin/dhclient3"
Jul 10 09:19:44 160096 kernel: [   23.206147] type=1505 audit(1341929983.917:3):  operation="profile_load" pid=604 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 10 09:19:44 160096 kernel: [   23.206588] type=1505 audit(1341929983.917:4):  operation="profile_load" pid=604 name="/usr/lib/connman/scripts/dhclient-script"
Jul 10 09:19:44 160096 kernel: [   23.267074] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 10 09:19:44 160096 kernel: [   23.267088] i915 0000:00:02.0: setting latency timer to 64
Jul 10 09:19:44 160096 kernel: [   23.274293] lib80211_crypt: registered algorithm 'TKIP'
Jul 10 09:19:44 160096 kernel: [   23.274453] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:6426)
Jul 10 09:19:44 160096 kernel: [   23.274949] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
Jul 10 09:19:44 160096 kernel: [   23.319594] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Jul 10 09:19:44 160096 kernel: [   23.319604] [drm] MTRR allocation failed.  Graphics performance may suffer.
Jul 10 09:19:44 160096 kernel: [   23.320897]   alloc irq_desc for 29 on node -1
Jul 10 09:19:44 160096 kernel: [   23.320906]   alloc kstat_irqs on node -1
Jul 10 09:19:44 160096 kernel: [   23.320927] i915 0000:00:02.0: irq 29 for MSI/MSI-X
Jul 10 09:19:44 160096 kernel: [   23.320944] [drm] set up 7M of stolen space
Jul 10 09:19:44 160096 kernel: [   23.326716] input: Dell WMI hotkeys as /devices/virtual/input/input5
Jul 10 09:19:44 160096 kernel: [   23.448170] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input6
Jul 10 09:19:44 160096 kernel: [   23.448331] usbcore: registered new interface driver uvcvideo
Jul 10 09:19:44 160096 kernel: [   23.448341] USB Video Class driver (v0.1.0)
Jul 10 09:19:44 160096 kernel: [   23.533715] [drm] initialized overlay support
Jul 10 09:19:44 160096 kernel: [   23.766013] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04731/0xa40000/0xa0000
Jul 10 09:19:44 160096 kernel: [   23.803969] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
Jul 10 09:19:44 160096 kernel: [   23.973846] fb0: inteldrmfb frame buffer device
Jul 10 09:19:44 160096 avahi-daemon[730]: Network interface enumeration completed.
Jul 10 09:19:44 160096 kernel: [   23.973854] registered panic notifier
Jul 10 09:19:44 160096 avahi-daemon[730]: Registering HINFO record with values 'I686'/'LINUX'.
Jul 10 09:19:44 160096 avahi-daemon[730]: Server startup complete. Host name is 160096.local. Local service cookie is 2795966939.
Jul 10 09:19:44 160096 NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Jul 10 09:19:44 160096 NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: (155789040) ... get_connections.
Jul 10 09:19:44 160096 NetworkManager:    SCPlugin-Ifupdown: (155789040) ... get_connections (managed=false): return empty list.
Jul 10 09:19:44 160096 modem-manager: Loaded plugin AnyData
Jul 10 09:19:44 160096 modem-manager: Loaded plugin Option
Jul 10 09:19:44 160096 modem-manager: Loaded plugin Longcheer
Jul 10 09:19:44 160096 modem-manager: Loaded plugin Gobi
Jul 10 09:19:44 160096 modem-manager: Loaded plugin Generic
Jul 10 09:19:44 160096 modem-manager: Loaded plugin Ericsson MBM
Jul 10 09:19:44 160096 modem-manager: Loaded plugin Novatel
Jul 10 09:19:44 160096 modem-manager: Loaded plugin Option High-Speed
Jul 10 09:19:44 160096 modem-manager: Loaded plugin Huawei
Jul 10 09:19:44 160096 kernel: [   24.047368] acpi device:22: registered as cooling_device2
Jul 10 09:19:44 160096 NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jul 10 09:19:44 160096 modem-manager: Loaded plugin Sierra
Jul 10 09:19:44 160096 modem-manager: Loaded plugin Nokia
Jul 10 09:19:44 160096 modem-manager: Loaded plugin ZTE
Jul 10 09:19:44 160096 modem-manager: Loaded plugin MotoC
Jul 10 09:19:44 160096 kernel: [   24.053131] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input8
Jul 10 09:19:44 160096 kernel: [   24.053816] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jul 10 09:19:44 160096 kernel: [   24.054008] ACPI Warning for \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) (20090903/nspredef-433)
Jul 10 09:19:44 160096 kernel: [   24.054803] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input9
Jul 10 09:19:44 160096 kernel: [   24.055485] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Jul 10 09:19:44 160096 kernel: [   24.056425] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jul 10 09:19:44 160096 kernel: [   24.056585] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Jul 10 09:19:44 160096 kernel: [   24.056658] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jul 10 09:19:44 160096 NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01).
Jul 10 09:19:44 160096 kernel: [   24.079621] vga16fb: initializing
Jul 10 09:19:44 160096 kernel: [   24.079634] vga16fb: mapped to 0xc00a0000
Jul 10 09:19:44 160096 kernel: [   24.079645] vga16fb: not registering due to another framebuffer present
Jul 10 09:19:44 160096 NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Jul 10 09:19:44 160096 NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 10 09:19:44 160096 NetworkManager: <info>  (eth1): now managed
Jul 10 09:19:44 160096 NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Jul 10 09:19:44 160096 NetworkManager: <info>  (eth1): bringing up device.
Jul 10 09:19:44 160096 gdm-binary[759]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul 10 09:19:44 160096 kernel: [   24.229223] type=1505 audit(1341929984.941:5):  operation="profile_replace" pid=769 name="/sbin/dhclient3"
Jul 10 09:19:44 160096 kernel: [   24.230023] type=1505 audit(1341929984.941:6):  operation="profile_replace" pid=769 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jul 10 09:19:44 160096 kernel: [   24.230489] type=1505 audit(1341929984.941:7):  operation="profile_replace" pid=769 name="/usr/lib/connman/scripts/dhclient-script"
Jul 10 09:19:44 160096 kernel: [   24.233351] type=1505 audit(1341929984.945:8):  operation="profile_load" pid=768 name="/usr/share/gdm/guest-session/Xsession"
Jul 10 09:19:44 160096 kernel: [   24.252069] [drm] Big FIFO is enabled
Jul 10 09:19:44 160096 kernel: [   24.252088] [drm] Big FIFO is enabled
Jul 10 09:19:44 160096 kernel: [   24.264428] Console: switching to colour frame buffer device 128x37
Jul 10 09:19:44 160096 kernel: [   24.280342] type=1505 audit(1341929984.993:9):  operation="profile_load" pid=773 name="/usr/bin/freshclam"
Jul 10 09:19:45 160096 kernel: [   24.316331] type=1505 audit(1341929985.029:10):  operation="profile_load" pid=774 name="/usr/lib/cups/backend/cups-pdf"
Jul 10 09:19:45 160096 kernel: [   24.317340] type=1505 audit(1341929985.029:11):  operation="profile_load" pid=774 name="/usr/sbin/cupsd"
Jul 10 09:19:45 160096 kernel: [   24.330639] hda_codec: ALC269: BIOS auto-probing.
Jul 10 09:19:45 160096 kernel: [   24.330845] hda_codec: connection list not available for 0x24
Jul 10 09:19:45 160096 kernel: [   24.331281] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth1): preparing device.
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Jul 10 09:19:45 160096 NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth0): carrier is OFF
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3')
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth0): now managed
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth0): bringing up device.
Jul 10 09:19:45 160096 kernel: [   24.398953]   alloc irq_desc for 30 on node -1
Jul 10 09:19:45 160096 kernel: [   24.398963]   alloc kstat_irqs on node -1
Jul 10 09:19:45 160096 kernel: [   24.398999] tg3 0000:09:00.0: irq 30 for MSI/MSI-X
Jul 10 09:19:45 160096 kernel: [   24.563112] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 10 09:19:45 160096 kernel: [   24.564285] tg3: eth0: Link is down.
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth0): preparing device.
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jul 10 09:19:45 160096 NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0
Jul 10 09:19:45 160096 gdm-binary[759]: WARNING: Unable to find users: no seat-id found
Jul 10 09:19:45 160096 NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul 10 09:19:45 160096 NetworkManager: <info>  modem-manager is now available
Jul 10 09:19:45 160096 NetworkManager: <info>  Trying to start the supplicant...
Jul 10 09:19:45 160096 gdm-simple-slave[856]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 0)
Jul 10 09:19:45 160096 NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Jul 10 09:19:45 160096 init: apport pre-start process (906) terminated with status 1
Jul 10 09:19:45 160096 acpid: starting up with proc fs
Jul 10 09:19:45 160096 init: apport post-stop process (933) terminated with status 1
Jul 10 09:19:45 160096 acpid: 36 rules loaded
Jul 10 09:19:45 160096 acpid: waiting for events: event logging is off
Jul 10 09:19:45 160096 anacron[942]: Anacron 2.3 started on 2012-07-10
Jul 10 09:19:45 160096 anacron[942]: Normal exit (0 jobs run)
Jul 10 09:19:45 160096 kernel: [   25.185368] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 10 09:19:46 160096 kernel: [   25.392971] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul 10 09:19:46 160096 kernel: [   25.394311] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Jul 10 09:19:46 160096 kernel: [   25.394321] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Jul 10 09:19:46 160096 kernel: [   25.394328] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Jul 10 09:19:46 160096 acpid: client connected from 1029[0:0]
Jul 10 09:19:46 160096 acpid: 1 client rule loaded
Jul 10 09:19:46 160096 avahi-daemon[730]: Registering new address record for fe80::e206:e6ff:fe64:f8ea on eth1.*.
Jul 10 09:19:49 160096 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jul 10 09:19:49 160096 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jul 10 09:19:49 160096 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jul 10 09:19:49 160096 kernel: [   28.565065] tg3: eth0: Link is up at 1000 Mbps, full duplex.
Jul 10 09:19:49 160096 kernel: [   28.565075] tg3: eth0: Flow control is on for TX and on for RX.
Jul 10 09:19:49 160096 kernel: [   28.565601] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 10 09:19:49 160096 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 10 09:19:49 160096 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jul 10 09:19:49 160096 NetworkManager: <info>  dhclient started with pid 1449
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jul 10 09:19:49 160096 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jul 10 09:19:49 160096 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jul 10 09:19:49 160096 dhclient: All rights reserved.
Jul 10 09:19:49 160096 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 10 09:19:49 160096 dhclient: 
Jul 10 09:19:49 160096 NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jul 10 09:19:49 160096 dhclient: Listening on LPF/eth0/5c:f9:dd:3d:74:0a
Jul 10 09:19:49 160096 dhclient: Sending on   LPF/eth0/5c:f9:dd:3d:74:0a
Jul 10 09:19:49 160096 dhclient: Sending on   Socket/fallback
Jul 10 09:19:49 160096 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jul 10 09:19:49 160096 dhclient: DHCPOFFER of 10.9.6.77 from 10.9.1.2
Jul 10 09:19:49 160096 dhclient: DHCPREQUEST of 10.9.6.77 on eth0 to 255.255.255.255 port 67
Jul 10 09:19:49 160096 dhclient: DHCPACK of 10.9.6.77 from 10.9.1.2
Jul 10 09:19:49 160096 NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 10 09:19:49 160096 NetworkManager: <info>    address 10.9.6.77
Jul 10 09:19:49 160096 NetworkManager: <info>    prefix 16 (255.255.0.0)
Jul 10 09:19:49 160096 NetworkManager: <info>    gateway 10.9.0.2
Jul 10 09:19:49 160096 NetworkManager: <info>    nameserver '10.9.1.4'
Jul 10 09:19:49 160096 NetworkManager: <info>    nameserver '10.9.1.2'
Jul 10 09:19:49 160096 NetworkManager: <info>    domain name 'mchs.com'
Jul 10 09:19:49 160096 NetworkManager: <info>    wins '10.9.1.2'
Jul 10 09:19:49 160096 NetworkManager: <info>    wins '10.9.1.4'
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 10 09:19:49 160096 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jul 10 09:19:49 160096 dhclient: bound to 10.9.6.77 -- renewal in 173292 seconds.
Jul 10 09:19:49 160096 avahi-daemon[730]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.9.6.77.
Jul 10 09:19:49 160096 avahi-daemon[730]: New relevant interface eth0.IPv4 for mDNS.
Jul 10 09:19:49 160096 avahi-daemon[730]: Registering new address record for 10.9.6.77 on eth0.IPv4.
Jul 10 09:19:50 160096 gdm-session-worker[1459]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul 10 09:19:50 160096 NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jul 10 09:19:50 160096 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jul 10 09:19:50 160096 NetworkManager: <info>  Activation (eth0) successful, device activated.
Jul 10 09:19:50 160096 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 10 09:19:50 160096 ntpdate[1497]: adjust time server 10.9.1.2 offset -0.004212 sec
Jul 10 09:19:51 160096 avahi-daemon[730]: Registering new address record for fe80::5ef9:ddff:fe3d:740a on eth0.*.
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Sucessfully called chroot.
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Sucessfully dropped privileges.
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Sucessfully limited resources.
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Running.
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Canary thread running.
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Watchdog thread running.
Jul 10 09:19:51 160096 polkitd[1522]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Sucessfully made thread 1514 of process 1514 (n/a) owned by '114' high priority at nice level -11.
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Supervising 1 threads of 1 processes of 1 users.
Jul 10 09:19:51 160096 anacron[1572]: Anacron 2.3 started on 2012-07-10
Jul 10 09:19:51 160096 anacron[1572]: Normal exit (0 jobs run)
Jul 10 09:19:51 160096 kernel: [   30.814072] CPU0 attaching NULL sched-domain.
Jul 10 09:19:51 160096 kernel: [   30.814088] CPU1 attaching NULL sched-domain.
Jul 10 09:19:51 160096 kernel: [   30.828691] CPU0 attaching sched-domain:
Jul 10 09:19:51 160096 kernel: [   30.828702]  domain 0: span 0-1 level SIBLING
Jul 10 09:19:51 160096 kernel: [   30.828710]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Jul 10 09:19:51 160096 kernel: [   30.828727]   domain 1: span 0-1 level MC
Jul 10 09:19:51 160096 kernel: [   30.828734]    groups: 0-1 (cpu_power = 1178)
Jul 10 09:19:51 160096 kernel: [   30.828750] CPU1 attaching sched-domain:
Jul 10 09:19:51 160096 kernel: [   30.828757]  domain 0: span 0-1 level SIBLING
Jul 10 09:19:51 160096 kernel: [   30.828764]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Jul 10 09:19:51 160096 kernel: [   30.828779]   domain 1: span 0-1 level MC
Jul 10 09:19:51 160096 kernel: [   30.828787]    groups: 0-1 (cpu_power = 1178)
Jul 10 09:19:51 160096 kernel: [   30.916241] ppdev: user-space parallel port driver
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Sucessfully made thread 1584 of process 1514 (n/a) owned by '114' RT at priority 5.
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Supervising 2 threads of 1 processes of 1 users.
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Sucessfully made thread 1585 of process 1514 (n/a) owned by '114' RT at priority 5.
Jul 10 09:19:51 160096 rtkit-daemon[1516]: Supervising 3 threads of 1 processes of 1 users.
Jul 10 09:19:52 160096 gdm-simple-greeter[1457]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jul 10 09:19:52 160096 init: plymouth-stop pre-start process (1664) terminated with status 1
Jul 10 09:19:52 160096 gdm-simple-greeter[1457]: WARNING: Unable to parse history: (null)   1#012
Jul 10 09:19:55 160096 kernel: [   35.224027] eth1: no IPv6 routers present
Jul 10 09:20:00 160096 kernel: [   39.372027] eth0: no IPv6 routers present
Jul 10 09:29:41 160096 gdm-session-worker[1459]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jul 10 09:29:47 160096 rtkit-daemon[1516]: Sucessfully made thread 3294 of process 3294 (n/a) owned by '1001' high priority at nice level -11.
Jul 10 09:29:47 160096 rtkit-daemon[1516]: Supervising 4 threads of 2 processes of 2 users.
Jul 10 09:29:47 160096 rtkit-daemon[1516]: Sucessfully made thread 3302 of process 3294 (n/a) owned by '1001' RT at priority 5.
Jul 10 09:29:47 160096 rtkit-daemon[1516]: Supervising 5 threads of 2 processes of 2 users.
Jul 10 09:29:47 160096 rtkit-daemon[1516]: Sucessfully made thread 3311 of process 3294 (n/a) owned by '1001' RT at priority 5.
Jul 10 09:29:47 160096 rtkit-daemon[1516]: Supervising 6 threads of 2 processes of 2 users.
Jul 10 09:29:48 160096 rtkit-daemon[1516]: Sucessfully made thread 3313 of process 3313 (n/a) owned by '1001' high priority at nice level -11.
Jul 10 09:29:48 160096 rtkit-daemon[1516]: Supervising 7 threads of 3 processes of 2 users.
Jul 10 09:29:48 160096 pulseaudio[3313]: pid.c: Daemon already running.
Jul 10 09:52:11 160096 kernel: [ 1970.484160] tg3: eth0: Link is down.
Jul 10 09:52:11 160096 NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jul 10 09:52:15 160096 NetworkManager: <info>  (eth0): device state change: 8 -> 2 (reason 40)
Jul 10 09:52:15 160096 NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Jul 10 09:52:15 160096 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1449
Jul 10 09:52:15 160096 NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Jul 10 09:52:15 160096 avahi-daemon[730]: Withdrawing address record for 10.9.6.77 on eth0.
Jul 10 09:52:15 160096 avahi-daemon[730]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.9.6.77.
Jul 10 09:52:15 160096 avahi-daemon[730]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 10 10:00:52 160096 kernel: [ 2491.765482] [drm] Big FIFO is enabled
Jul 10 10:27:44 160096 kernel: [ 4103.514490] [drm] Big FIFO is enabled
```

Hopefully someone will have some new ideas after looking at this information.

Thanks

---

### Post by computer13137 on 2012-07-10
I have some new information.  When this problem occurs, ethtool eth0 reports that "Link detected: no" when in fact there is a cable plugged in, and there's a gigabit connection indicated by the activity LEDs on my switch.

---

