---
title: "No wireless with RTL8111"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by dthuress on 2011-11-21
I can't get wireless to work on my laptop, wired does work. 
I have followed the steps in[**this**]("http://ubuntuforums.org/showthread.php?t=1022411") thread (without result) and searched the forums.

[B]1 ) Machine Brand and Model (PC/Laptop):
[/B]```
HP ProBook 4330s
```[B]2 ) Wireless Brand, Model and Wireless Chipset:
[/B]```
dennis@HP-ProBook-4330s:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]
24:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
24:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
24:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
25:00.0 Network controller: Ralink corp. Device 3592
26:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
dennis@HP-ProBook-4330s:~$ 

```**3 ) Interface:**
```
dennis@HP-ProBook-4330s:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 64:31:50:9f:07:17  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6631:50ff:fe9f:717/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2303278 (2.3 MB)  TX bytes:345953 (345.9 KB)
          Interrupt:46 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:02:b4:bd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


``````
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```**4 ) Modules:**
```
dennis@HP-ProBook-4330s:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_idt      60049  1 
binfmt_misc            17292  1 
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48717  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
fglrx                2595570  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
jmb38x_ms              17406  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               15857  1 jmb38x_ms
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36466  0 
hp_accel               21632  0 
lis3lv02d              19280  1 hp_accel
input_polldev          13648  1 lis3lv02d
psmouse                73673  0 
serio_raw              12990  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
i915                  505108  2 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
drm_kms_helper         32889  1 i915
wmi                    18744  1 hp_wmi
r8168                 202001  0 
drm                   192226  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915

```**5 ) Kernel boot messages**
```
dennis@HP-ProBook-4330s:~$ dmesg | grep "r8168"
[    1.995325] r8168 Gigabit Ethernet driver 8.026.00-NAPI loaded
[    1.995348] r8168 0000:26:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.995377] r8168 0000:26:00.0: setting latency timer to 64
[    1.995451] r8168 0000:26:00.0: irq 46 for MSI/MSI-X
[    2.161492] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    2.161500] r8168  Copyright (C) 2011  Realtek NIC software team <nicfae@realtek.com> 
[   13.403188] r8168: eth0: link down
[  503.315542] r8168: eth0: link up
[  504.147485] r8168: eth0: link up

```**6 ) Network configuration**
```
dennis@HP-ProBook-4330s:~$ sudo lshw -C network
[sudo] password for dennis: 
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:25:00.0
       logical name: wlan0
       version: 00
       serial: d0:df:9a:02:b4:bd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-12-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:d4600000-d460ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:26:00.0
       logical name: eth0
       version: 06
       serial: 64:31:50:9f:07:17
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.026.00-NAPI duplex=full ip=192.168.1.72 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff

```**7 ) Scan for networks:**
```
dennis@HP-ProBook-4330s:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results


```[B]8 ) Ubuntu Version: 
[/B]```
Ubuntu 11.10
```[B]9 ) Kernel/architecture 
[/B]```
dennis@HP-ProBook-4330s:~$ uname -mr
3.0.0-12-generic i686

```**10 ) Restarting the network:**
```
dennis@HP-ProBook-4330s:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```Thanks in advance for any help!

---

### Post by praseodym on 2011-11-21
Hi,

> 25:00.0 Network controller: Ralink corp. Device 3592
can you please additionally show:
```
lspci -nnk | grep -iA2 net
rfkill list
```to have a look at the chipset.
"r8168" is your LAN driver, LAN is working?

---

### Post by dthuress on 2011-11-21
```
dennis@HP-ProBook-4330s:~$ lspci -nnk | grep -iA2 net
25:00.0 Network controller [0280]: Ralink corp. Device [1814:3592]
    Subsystem: Hewlett-Packard Company Device [103c:1638]
    Kernel driver in use: rt2800pci
--
26:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:167f]
    Kernel driver in use: r8168

``````
dennis@HP-ProBook-4330s:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```

---

### Post by praseodym on 2011-11-21
Install this driver:

```
sudo apt-get install linux-headers-generic build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
tar xzvf angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make
sudo make install
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
```
and reboot. Check:
```
iwconfig
lsmod
sudo iwlist scan
dmesg | egrep 'rt3|rt2'
```

---

### Post by dthuress on 2011-11-22
Thanks it's working great now!

---

