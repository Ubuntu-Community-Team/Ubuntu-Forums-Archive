---
title: "Re-find Wi-Fi Card"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by Matt_Rapp on 2009-12-25
Hi,

So I just got a brand new HD 5770 and to install it I had to move my Wi-Fi card to a different PCI slot. Ubuntu no longer can find my card at all despite it working fine for many weeks before.

My card is a Encore ENLWI-N 802.11n card REV 1.1

I am going to test the physical slot with another card soon, with the graphics card installed there is only one PCI and one PCIE 1X slot open so if the slot turns out to be bad it looks like I am going to have to go looking for a PCIE adapter.

In the mean time here are some terminal results I gathered, hope they are of some help.

```

matt@matt-desktop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge 
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0) 
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a) 
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control 
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control 
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68b8 
01:00.1 Audio device: ATI Technologies Inc Device aa58 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01) 
matt@matt-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:26:18:05:1d:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 

matt@matt-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 
matt@matt-desktop:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1           5280  1 
nls_cp437               6976  1 
vfat                   13184  1 
fat                    59832  1 vfat 
usb_storage            65984  1 
binfmt_misc            10220  1 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_via      35456  1 
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi 
amd64_edac_mod         26688  0 
iptable_filter          3872  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
ip_tables              21200  1 iptable_filter 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel 
x_tables               25832  1 ip_tables 
snd_hwdep               9352  1 snd_hda_codec 
i2c_piix4              11728  0 
ppdev                   8232  0 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
lp                     11908  0 
edac_core              48876  1 amd64_edac_mod 
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_timer              26992  2 snd_seq,snd_pcm 
snd                    77096  15 snd_seq_oss,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer 
soundcore               9088  1 snd 
parport_pc             37352  1 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm 
parport                40528  3 ppdev,lp,parport_pc 
asus_atk0110            9472  0 
usbhid                 43968  0 
r8169                  38884  0 
mii                     6368  1 r8169 
matt@matt-desktop:~$ lsmod | grep "wlan_module_name" 
matt@matt-desktop:~$ sudo lshw -C network 
[sudo] password for matt: 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:26:18:05:1d:f3 
       size: 10MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
       resources: irq:27 ioport:e800(size=256) memory:fbfff000-fbffffff memory:fbfc0000-fbfdffff(prefetchable) 
matt@matt-desktop:~$ lsb_release -d 
Description:	Ubuntu 9.10 
matt@matt-desktop:~$ uname -mr 
2.6.31-16-generic x86_64 

```

---

### Post by Matt_Rapp on 2009-12-28
I reinstalled a few cards and did a new installation of 9.10 and everything worked itself out.

---

