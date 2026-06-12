---
title: "Wireless not working for recently installed Ubuntu 8.10"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by Eagle Nest on 2009-10-22
I recently picked up a Toshiba laptop with Vista already installed. I was able to successfully install Ubuntu 8.10 using wubi and a disc that I had picked up. The plan is to wean myself from the Windows OS over time and as I am able. 

Anyway, despite the fact that the wireless connection works OK for the Windows OS, I've not been able to get the connection to work while I am booted up under Ubuntu 8.10. It could be a very simple problem - or not so simple - as I am pretty new to Linux. 

I read "How to Post a Wireless issue" and found the following data using the Terminal. **[COLOR="Red"]How do I get my wireless to work under the Linux OS? Much thanks for suggestions and I will check back regularly. [/COLOR]**

**1. Machine Brand and Model (laptop):**  Toshiba Setellite Pro S300L Model Number PSSD1C - 01100G.

2. **Wireless Brand, Model and Wireless Chipset:**

Code: lspci


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:0b.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:0b.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
05:0b.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
05:0b.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
05:0b.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

Code: lsusb

Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Code: lspci -nn | grep 'Atheros'

1:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

**3. check interface:**

Code: ifconfig

eth0      Link encap:Ethernet  HWaddr 00:23:18:2a:13:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3577295237 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

Code: iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

...

 Note ... (wlan0 No such device)

**4. Check for modules:**

Code: lsmod

Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
usb_storage            81728  1 
libusual               27156  1 usb_storage
ipv6                  263972  10 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  2 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14600  0 
container              11520  0 
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
pcmcia                 43052  0 
uvcvideo               62728  0 
psmouse                45200  0 
pcspkr                 10624  0 
serio_raw              13444  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
ricoh_mmc              11904  0 
mmc_core               58268  1 sdhci
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_hda_intel         381488  3 
joydev                 18368  0 
snd_pcm_oss            46848  0 
evdev                  17696  16 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
video                  25104  0 
output                 11008  1 video
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
battery                18436  0 
ac                     12292  0 
button                 14224  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
intel_agp              33724  1 
pci_hotplug            35236  1 shpchp
agpgart                42184  3 drm,intel_agp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
loop                   23180  2 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ahci                   37132  1 
libata                177312  1 ahci
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
r8169                  35972  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  7 usb_storage,libusual,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 

[B]5. Kernel boot messages:
[/B]
Code: dmesg

A very large amount of information came up here. If I need to, then I will cut and paste it. 

**6. Network Configuration **

Code: Code: sudo lshw -C network

 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:23:18:2a:13:4a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7a:7e:f0:95:de:67
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

**7. Scan for networks:**

Code: iwlist scan

lo Interface doesn't support scanning
eth0           ibid
pano           ibid

 **8. Ubuntu Versions**

Code: lsb_release -d

Ubuntu 8.10

[B]9. Kernel/architecture (32 bit)
[/B]
uname -mr

2.6.27-7-generic i686

---

### Post by Cuba71 on 2009-10-22
The Atheros AR252x should work out of the box with Ubuntu, using the Linux driver ath5k.

For some reason beyond my knowledge, ath_pci 99096 0 shows on your lsmod list, instead of the ath5k.

Perhaps someone else can help you out with this.

```

  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: xxxxxxxxxxxxxxxxx
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.101 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

---

### Post by Eagle Nest on 2009-10-23
More information. Perhaps I should have entered this first. 

I've been booting up, at which point I choose between Vista and Ubuntu. I skip over the step to "enter the menu" and arrive at the Ubuntu desktop after entering my username and password. 

The Network Manager Applet (0.7.0) can be opened from the TaskBar along the top. Left-clicking gives no connections, only "Wired Network" or "auto eth0" - both of which cannot be clicked on - or VPN connections - which CAN be clicked on. VPN Connections leads to Configure VPN (which works) and then I get the Network Connections applet.  I can also reach this Network Connections applet by right-clicking. 

Enable Networking is checked. 

I had a look at [www.gnome.org/projects/NetworkManager](www.gnome.org/projects/NetworkManager) but it didn't seem to be all that helpful in figuring out how to use the applet.

---

### Post by Eagle Nest on 2009-10-28
By using an ethernet cable and doing a non-wireless connection I've been able to connect to the www and update my version of Ubuntu 8.10. The upgrade has followed and I'm hoping that my wireless connection will not be a problem once 9.04 is properly installed. 

I think the problem is solved but I will make another entry to confirm.

---

### Post by Eagle Nest on 2009-10-28
Updates to Ubuntu 8.10 and an upgrade to 9.04 solved the problem.

---

