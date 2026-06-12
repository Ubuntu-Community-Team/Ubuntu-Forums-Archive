---
title: "Atheros 9825 wireless card"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by freewheel84 on 2009-07-30
Hello

I am absolutely new to linux, i have a band new hp dv3-2155mx laptop and installed the latest version of ubuntu on it (9.01 i believe), i cannot get my wireless to work, the make of the card is Atheros 9825 , from what i have followed after reading evrything over the net it comes back as network unclaimed, i dont have a wired acces from ubuntu, i need help.

---

### Post by freewheel84 on 2009-07-30
Here is all the info i gathered
 
 
[EMAIL="shikhir@ubuntu:~$"]shikhir@ubuntu:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. Device 002b (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

[EMAIL="shikhir@ubuntu:~$"]shikhir@ubuntu:~$[/EMAIL] lspci -nn | grep 'Atheros'
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002b] (rev 01)

[EMAIL="shikhir@ubuntu:~$"]shikhir@ubuntu:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:a2:c7:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:7584646853 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0x8000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

[EMAIL="shikhir@ubuntu:~$"]shikhir@ubuntu:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

[EMAIL="shikhir@ubuntu:~$"]shikhir@ubuntu:~$[/EMAIL] iwconfig wlan0
wlan0     No such device
[EMAIL="shikhir@ubuntu:~$"]shikhir@ubuntu:~$[/EMAIL] lsmod
Module                  Size  Used by
ipv6                  314312  14 
nls_iso8859_1          13568  1 
nls_cp437              15232  1 
vfat                   21120  1 
fat                    64824  1 vfat
i915                   44544  2 
drm                   110304  3 i915
binfmt_misc            18700  1 
rfcomm                 51104  0 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,bnep,sco,l2cap
ppdev                  16904  0 
acpi_cpufreq           16400  1 
cpufreq_stats          14468  0 
cpufreq_conservative    16392  0 
cpufreq_ondemand       16400  1 
freq_table             13568  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      12420  0 
cpufreq_powersave      10368  0 
container              12288  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
snd_hda_intel         489264  5 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  3 snd_hda_intel,snd_pcm_oss
psmouse                51612  0 
evdev                  20512  13 
pcspkr                 11136  0 
serio_raw              14596  0 
uvcvideo               68616  0 
snd_seq_dummy          11524  0 
compat_ioctl32         18176  1 uvcvideo
videodev               46720  2 uvcvideo,compat_ioctl32
v4l1_compat            24580  2 uvcvideo,videodev
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  3 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
video                  28948  0 
output                 11776  1 video
wmi                    15808  0 
battery                21128  0 
button                 15904  0 
ac                     13448  0 
intel_agp              39280  1 
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
loop                   26380  2 
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sd_mod                 45864  4 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
usb_storage            92864  1 
libusual               31784  1 usb_storage
ahci                   43148  1 
libata                200160  1 ahci
scsi_mod              183160  5 sr_mod,sd_mod,sg,usb_storage,libata
dock                   18464  1 libata
r8169                  40196  0 
ehci_hcd               48908  0 
uhci_hcd               34336  0 
usbcore               175376  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                27424  0 
processor              47800  4 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  5 
[EMAIL="shikhir@ubuntu:~$"]shikhir@ubuntu:~$[/EMAIL] sudo lshw -c network
[sudo] password for shikhir: 
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
       logical name: eth0
       version: 02
       serial: 00:23:5a:a2:c7:c7
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:02:40:42:fe:37
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[EMAIL="shikhir@ubuntu:~$"]shikhir@ubuntu:~$[/EMAIL] iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
pan0      Interface doesn't support scanning.

[EMAIL="shikhir@ubuntu:~$"]shikhir@ubuntu:~$[/EMAIL] uname -mr
2.6.27-7-generic x86_64
[EMAIL="shikhir@ubuntu:~$"]shikhir@ubuntu:~$[/EMAIL] sudo/etc/init.d/networking restart
bash: sudo/etc/init.d/networking: No such file or directory

---

### Post by superprash2003 on 2009-07-30
have you looked at system->admin->jhardware drivers?

---

### Post by freewheel84 on 2009-07-30
yes i did , it says No proprietary drivers are in use in this system.

---

### Post by freewheel84 on 2009-07-30
Any help will be appreciated.

---

