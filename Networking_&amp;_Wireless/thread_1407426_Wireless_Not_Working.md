---
title: "Wireless Not Working"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by larry on 2010-02-15
Dear All,
I made a fresh xubuntu 9.10 installation on my laptop (amilo pa 3553 fujitsu-siemens,amd64 architecture).
The problem is that the network manager applet does not allow me to enable wireless. I have always had problems with my own wireless card, but I have also tried 2 usb wireless sticks: Belkin Wireless-G USB Adapter and D-link DWL-G122 (allegedly linux-friendly).
They both used to work under Debian, but also there (at least on Debian testing) they are broken now. Maybe a kernel issue...however, not having wireless connections on a laptop is pretty annoying.
Any suggestions are welcome.
Cheers

larry

---

### Post by northd_tech on 2010-02-15
Could you post the results when you run these commands in a terminal to see what kind of hardware you are working with, Larry?

```
lspci

lsusb

lsmod

uname -a

sudo lshw -C network 

ifconfig

iwconfig
```

---

### Post by larry on 2010-02-15
> **northd_tech said:**
> Could you post the results when you run these commands in a terminal to see what kind of hardware you are working with, Larry?

```
lspci

lsusb

lsmod

uname -a

sudo lshw -C network 

ifconfig

iwconfig
```


Hello,
And thanks for helping. Below is the output of the commands you requested.
I am not that experienced about networks, but the problem looks to me more about enabling the wireless network than hardware recognition.
I ran the commands with the belkin wireless usb stick plugged into my laptop.
Cheers

larry

~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
02:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0a:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
0a:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

~$ lsmod
Module                  Size  Used by
ppdev                   8232  0 
snd_hda_codec_atihdmi     4320  2 
snd_hda_codec_realtek   277860  1 
joydev                 13088  0 
snd_hda_intel          31880  4 
arc4                    2144  4 
rt73usb                29092  0 
ecb                     3296  4 
crc_itu_t               2336  1 rt73usb
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  2 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
rt2500usb              23364  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00usb              13600  2 rt73usb,rt2500usb
snd_timer              26992  2 snd_pcm,snd_seq
rt2x00lib              34624  3 rt73usb,rt2500usb,rt2x00usb
ath9k                 278176  0 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci               8928  0 
iptable_filter          3872  0 
jmb38x_ms              11300  0 
sdhci                  20484  1 sdhci_pci
input_polldev           4720  1 rt2x00lib
ip_tables              21200  1 iptable_filter
snd                    77096  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              210040  3 rt2x00usb,rt2x00lib,ath9k
fglrx                2234552  31 
x_tables               25832  1 ip_tables
soundcore               9088  2 snd
memstick               12528  1 jmb38x_ms
amd64_edac_mod         26688  0 
lp                     11908  0 
led_class               5256  3 rt2x00lib,ath9k,sdhci
ath                    10304  1 ath9k
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
psmouse                57124  0 
shpchp                 37756  0 
parport                40528  2 ppdev,lp
serio_raw               6596  0 
edac_core              48876  1 amd64_edac_mod
cfg80211              109144  4 rt2x00lib,ath9k,mac80211,ath
i2c_piix4              11728  0 
usbhid                 43968  0 
r8169                  38884  0 
mii                     6368  1 r8169
video                  23612  0 
output                  3680  1 video
ohci1394               33780  0 
ieee1394              100896  1 ohci1394


~$ uname -a
Linux sandworm 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux


~$ sudo lshw -C network 
[sudo] password for ****: 
  *-network DISABLED      
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:ce:86:9b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0200000-f020ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:02:b2:83
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.136 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:b000(size=256) memory:f0300000-f0300fff memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan2
       serial: 00:22:75:fe:2d:3d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:02:b2:83  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe02:b283/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36855886 (36.8 MB)  TX bytes:2834358 (2.8 MB)
          Interrupt:30 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15400 (15.4 KB)  TX bytes:15400 (15.4 KB)


:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by larry on 2010-02-15
Hi there,
Now I have fixed the problem: I had to update the bios (new driver available from manufacturer's website).
Now I can drop all the external usb sticks, wireless connectivity just works fine.

---

### Post by northd_tech on 2010-02-15
> **larry said:**
>  lspci
08:00.0 Network controller: **Atheros** Communications Inc. **AR928X Wireless** Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: **Realtek** Semiconductor Co., Ltd. **RTL8111/8168B** PCI Express Gigabit Ethernet controller (rev 02)


~$ lsmod
Module                  Size  Used by

[COLOR=Red]rt73usb                29092  0 
rt2500usb              23364  0 
rt2x00usb              13600  2 rt73usb,rt2500usb
rt2x00lib              34624  3 rt73usb,rt2500usb,rt2x00usb[/COLOR]
**ath9k**                 278176  0 
mac80211              210040  3 rt2x00usb,rt2x00lib,**ath9k**
ath                    10304  1 **ath9k**
cfg80211              109144  4 rt2x00lib,**ath9k**,mac80211,ath

**r8169**                  38884  0 
mii                     6368  1 **r8169**

~$ uname -a
Linux sandworm 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

~$ sudo lshw -C network 
[sudo] password for ****: 
  *-network DISABLED      
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:ce:86:9b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0200000-f020ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:02:b2:83
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.136 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:b000(size=256) memory:f0300000-f0300fff memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan2
       serial: 00:22:75:fe:2d:3d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:02:b2:83  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe02:b283/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36855886 (36.8 MB)  TX bytes:2834358 (2.8 MB)
          Interrupt:30 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15400 (15.4 KB)  TX bytes:15400 (15.4 KB)


:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

For future reference, your wireless card is a Atheros **AR928X **and the ethernet is a Realtek[B] RTL8111/8168B.

[/B]I didn't see the results of **lsusb**, but the "rt...usb" look like wireless USB modules to me.  Those are the ones that I marked in [COLOR=Red]red[/COLOR] above.

I'm glad you got it working.  If you have any trouble with the wireless, search the forums here for "Atheros AR928X" and you will probably find some related information.

edit:  You are running a 64-bit 2.6.31-20-generic linux kernel.

---

### Post by Demask on 2010-02-23
> **larry said:**
> Hi there,
Now I have fixed the problem: I had to update the bios (new driver available from manufacturer's website).
Now I can drop all the external usb sticks, wireless connectivity just works fine.

Just like'd to say thanks. I have the same laptop and experienced exactly the same problem with Ubuntu 9.10. BIOS-upgrade from Fujitsu fixed it all! It seems that with the updated BIOS you can enable/disable Wireless more permanently from BIOS. Instead of the "Fn+F1" combo you had to use every time you rebooted the laptop with windows. 

:)

---

