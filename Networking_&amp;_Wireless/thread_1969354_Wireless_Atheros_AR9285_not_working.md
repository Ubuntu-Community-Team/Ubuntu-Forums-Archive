---
title: "Wireless Atheros AR9285 not working"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by amirtheg on 2012-04-30
My wireless, Atheros AR9285, is not working I have searched the forums and other places. 
The network manager applet says that "wireless not ready".
The following are a collection of applicable terminal commands:

user@ubuntu ~ $ uname -r
```
3.2.0-23-generic
```user@ubuntu ~ $ lspci | grep Network
```
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```user@ubuntu ~ $ lsmod  | grep ath
```
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
```user@ubuntu ~ $ ifconfig
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47104 (47.1 KB)  TX bytes:47104 (47.1 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:8b:66:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```user@ubuntu ~ $ iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"off/any"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```user@ubuntu ~ $ rfkill list all
```
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```user@ubuntu:~$ sudo lshw -class network
```
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:8b:66:08
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d1600000-d160ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:d0200000-d023ffff ioport:a000(size=128)
```So I have seen many other people have a similar problem where they did not have a hardware wifi switch on, I have mine on. Also I have seen others where there was an "acer-wifi" module that was blocking the wlan connection.

Thanks for the help,
Amir

---

### Post by josephmills on 2012-04-30
Hi there could we see a full lsmod thanks (sometimes there are other mods mucking up things) also a ```
lspci -nn 
```
would be cool. -nn is name and number option.  

do you have more then one wireless card ? pluges in say a usb one ?

---

### Post by amirtheg on 2012-04-30
Thanks for the response. No I don't have any extra wireless interfaces, I should note that also my wired connection drops in and out every 30 seconds. So I have blacklisted that module, and am trying to install the new qualcomm alx driver without much luck at this point. 
Here is what you requested:

user@ubuntu:~$ lsmod 
```
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
joydev                 17693  0 
ext2                   73795  1 
snd_hda_codec_hdmi     32474  1 
arc4                   12529  2 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k                 132390  0 
i7core_edac            28102  0 
psmouse                87603  0 
serio_raw              13211  0 
edac_core              53746  1 i7core_edac
mac80211              506816  1 ath9k
snd_seq_midi           13324  0 
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
snd_rawmidi            30748  1 snd_seq_midi
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
cfg80211              205544  3 ath9k,mac80211,ath
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
btusb                  18288  2 
bluetooth             180104  23 bnep,rfcomm,btusb
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
asus_laptop            24493  0 
sparse_keymap          13890  1 asus_laptop
input_polldev          13896  1 asus_laptop
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
radeon                804372  3 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
video                  19596  0 

```user@ubuntu:~$ lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Broadway XT [Mobility Radeon HD 5800 Series] [1002:68a0]
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Juniper HDMI Audio [Radeon HD 5700 Series] [1002:aa58]
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c52] (rev 04)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
ff:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
ff:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
ff:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
ff:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
ff:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
ff:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
ff:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
ff:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
ff:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
ff:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
ff:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)
```Thanks

---

### Post by Godspell on 2012-04-30
I have AR9227 chipset wireless card on my desktop PC but my problem seems to be much worse than yours. Linux detects everything but once it's connected to the wireless connection, the PC just freezes and I have to hard shutdown.

Anyway, I'm not going to talk about that. I just wanted to say I had searched a lot on the Internet and found out both **AR922X** and **AR928X** chipsets do not play well with Linux. I was told ath9k module never really worked well. It's always one problem or another. Also, this isn't just on Ubuntu, I've used both Fedora and openSUSE and the problem was exactly the same. These problems existed since previous kernel version and still does in the present one.
I'm sorry if I sound negative though. Just wanted to share this with someone who seems to be having the same problem.

Anyway, who knows,....your chipset is slightly different from mine and it may work at the end. I'll keep checking this thread :)

Just in case if you wanted to do technical comparison, here's my thread:
[http://ubuntuforums.org/showthread.php?t=1966137](http://ubuntuforums.org/showthread.php?t=1966137)

Thank you and regards.

---

### Post by anshul.arb on 2012-04-30
hey I am getting the same issue... did you solve it ?

---

### Post by amirtheg on 2012-04-30
Thanks for the response guys. No I have not fixed the problem with either the wireless or wired connections. I have known from experience the wireless cards and apparently even ethernet do not work well with Linux, since I used to run Arch on my laptop previously. 

Best,
Amir

---

### Post by mörgæs on 2012-04-30
Moved to the network forum.

---

