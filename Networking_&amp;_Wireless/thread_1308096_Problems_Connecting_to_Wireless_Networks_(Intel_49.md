---
title: "Problems Connecting to Wireless Networks (Intel 4965ag)"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by mickeyfman on 2009-10-31
1.) Machine
HP Compaq 8710p

2.) Wireless Brand, Model and Wireless Chipset
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 320M (rev a1)
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
02:06.5 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 10)
02:06.6 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 10)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

3.) Check Interface
wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:ab:c7:af
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     IEEE 802.11abgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=14 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4.) Check For Modules
Module                  Size  Used by                                                                                                                                                 
pata_pcmcia            15200  1                                                                                                                                                       
arc4                    2144  2                                                                                                                                                       
pcmcia                 40116  1 pata_pcmcia                                                                                                                                           
joydev                 13088  0                                                                                                                                                       
vboxnetadp             93292  0                                                                                                                                                       
vboxnetflt            100300  0                                                                                                                                                       
vboxdrv              1708492  1 vboxnetflt                                                                                                                                            
hp_accel               12480  0
sdhci_pci               8928  0
tpm_infineon           10044  0
yenta_socket           27500  4
rsrc_nonstatic         11840  1 yenta_socket
ppdev                   8232  0
psmouse                57124  0
serio_raw               6596  0
parport_pc             37352  1
lp                     11908  0
parport                40528  3 ppdev,parport_pc,lp
tpm                    18464  1 tpm_infineon
tpm_bios                7680  1 tpm
sdhci                  20484  1 sdhci_pci
ecb                     3296  2
lis3lv02d               9312  1 hp_accel
pcmcia_core            41796  3 pcmcia,yenta_socket,rsrc_nonstatic
iwlagn                124832  0
iwlcore               133248  1 iwlagn
input_polldev           4720  1 lis3lv02d
led_class               5256  3 hp_accel,sdhci,iwlcore
snd_hda_codec_analog    79680  1
ricoh_mmc               4480  0
snd_hda_intel          31880  2
snd_hda_codec          87584  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0
snd_mixer_oss          18976  2 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0
snd_seq_oss            33440  0
snd_seq_midi            8192  0
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3872  0
snd_timer              26992  2 snd_pcm,snd_seq
mac80211              210104  2 iwlagn,iwlcore
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              21200  1 iptable_filter
snd                    77096  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               25832  1 ip_tables
soundcore               9088  2 snd
cfg80211              109144  3 iwlagn,iwlcore,mac80211
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
nvidia              10316904  38
ohci1394               33780  0
ieee1394              100896  1 ohci1394
video                  23612  0
output                  3680  1 video
e1000e                138672  0
intel_agp              32816  0

5.) Kernel Boot Message
[   11.881796] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k                                                                                                      
[   11.881800] iwlagn: Copyright(c) 2003-2009 Intel Corporation                                                                                                                       
[   11.882121] iwlagn 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                                                                        
[   11.882131] iwlagn 0000:10:00.0: setting latency timer to 64                                                                                                                       
[   11.882199] iwlagn 0000:10:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4                                                                                                 
[   11.925455] iwlagn 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels                                                                                                
[   11.925524]   alloc irq_desc for 29 on node 0                                                                                                                                      
[   11.925527]   alloc kstat_irqs on node 0                                                                                                                                           
[   11.925549] iwlagn 0000:10:00.0: irq 29 for MSI/MSI-X

6.) Network Configuration
  *-network
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1b:38:f2:5c:74
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.3-0 ip=192.168.1.68 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:e8000000-e801ffff memory:e8020000-e8020fff ioport:5000(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:ab:c7:af
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:e4000000-e4001fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

7.) Scan for Networks
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


8.) Ubuntu Version
Description:    Ubuntu 9.10

9.) Kernel Architecture
2.6.31-14-generic x86_64

10.) Restarting the Networks
 * Reconfiguring network interfaces...                                                                                                                                                                     Ignoring unknown interface eth0=eth0.

---

### Post by mickeyfmann on 2009-10-31
Any help anyone could offer would be greatly appreciated, I love KDE but this is a deal breaker for me. I just installed the OS today, it detects the networks just find but fails when it comes time to actually connect to them. As near as I can tell its authenticating but not getting an IP address.

---

### Post by MagusZero on 2009-10-31
I'm in an even worse state. I CAN see them. I can join them. I can get IP addresses. I can't use the internet...

And noone seems to have felt like replying to my topic yet.

---

