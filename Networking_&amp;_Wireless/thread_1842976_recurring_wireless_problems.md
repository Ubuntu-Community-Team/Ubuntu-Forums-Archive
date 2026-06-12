---
title: "recurring wireless problems"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by mdm27 on 2011-09-12
Dear all, 

I'm fairly new to ubuntu so please go slowly. Also, please accept my apologies if this has already been answered previously. I've tried to find the answer elsewhere on the forums, but with little success. 

In short, I have a wireless problem. I have installed Ubuntu on both my netbook and my desktop. My desktops is located such that it would be impossible to run a wired connection, so I also use wireless, with the help of an external USB adapter. 

I have a strong wireless signal, but for reasons I simply don't understand, I will occasionally lose my connection. On my netbook, I will lose my connection if I close the screen. When I open it up again, no wireless networks are shown from the drop down menu at the top of the screen. I have to reboot the computer in order to get online, which is very annoying. 

As far as my desktop is concerned, getting online is quite hit and miss. I will occasionally pick up the signal, but it will disappear at random intervals, particularly if the computer goes into standby mode. 

Can anyone out there help? If you need more information, please let me know. 

Thanks in advance for your assistance.

---

### Post by praseodym on 2011-09-12
Hi,

please show the terminal outputs of

```
lsusb
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by mdm27 on 2011-09-13
Hi, 


thanks for replying. Output is a follows:


matthew@matthew-N140:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2151 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
matthew@matthew-N140:~$ lsmod
Module                  Size  Used by
michael_mic            12540  4 
arc4                   12473  2 
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
r8192se_pci           482505  0 
snd_seq_midi           13132  0 
rfcomm                 38125  8 
snd_rawmidi            25269  1 snd_seq_midi
sco                    17827  2 
snd_seq_midi_event     14475  1 snd_seq_midi
bnep                   17785  2 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  451033  3 
l2cap                  48656  16 rfcomm,bnep
joydev                 17322  0 
cfg80211              156212  1 r8192se_pci
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
btusb                  18160  2 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
drm                   184164  4 i915,drm_kms_helper
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r8192e_pci            251260  0 
videodev               75143  1 uvcvideo
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
r8169                  42534  0 
matthew@matthew-N140:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"Sugar ****"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 1C:AF:F7:05:C1:5A   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=93/100  Signal level=-52 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by mdm27 on 2011-09-13
Hi, 


thanks for replying. Output is a follows:


matthew@matthew-N140:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2151 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
matthew@matthew-N140:~$ lsmod
Module                  Size  Used by
michael_mic            12540  4 
arc4                   12473  2 
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
r8192se_pci           482505  0 
snd_seq_midi           13132  0 
rfcomm                 38125  8 
snd_rawmidi            25269  1 snd_seq_midi
sco                    17827  2 
snd_seq_midi_event     14475  1 snd_seq_midi
bnep                   17785  2 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  451033  3 
l2cap                  48656  16 rfcomm,bnep
joydev                 17322  0 
cfg80211              156212  1 r8192se_pci
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
btusb                  18160  2 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
drm                   184164  4 i915,drm_kms_helper
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r8192e_pci            251260  0 
videodev               75143  1 uvcvideo
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
r8169                  42534  0 
matthew@matthew-N140:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"Sugar ****"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 1C:AF:F7:05:C1:5A   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=93/100  Signal level=-52 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by praseodym on 2011-09-13
Oh, ok, the problem is not the stick, right? Because its not plugged in. Please show:

```
lspci -nnk | grep -iA2 net
```
there are 2 drivers loaded for Realtek chips.

---

### Post by mdm27 on 2011-09-13
Thanks again for replying. 

The output is as follows:


00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
	Subsystem: nVidia Corporation Device [10de:cb84]
00:01.0 ISA bridge [0601]: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge [10de:075c] (rev a2)
	Subsystem: nVidia Corporation Device [10de:cb84]
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
	Subsystem: Acer Incorporated [ALI] Device [1025:0153]
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2
00:01.2 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0751] (rev a1)
	Subsystem: nVidia Corporation Device [10de:cb84]
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
	Subsystem: Acer Incorporated [ALI] Device [1025:0153]
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
	Subsystem: nVidia Corporation Device [10de:cb84]
	Kernel driver in use: ohci_hcd
00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
	Subsystem: nVidia Corporation Device [10de:cb84]
	Kernel driver in use: ehci_hcd
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
	Subsystem: nVidia Corporation Device [10de:cb84]
	Kernel driver in use: ohci_hcd
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
	Subsystem: nVidia Corporation Device [10de:cb84]
	Kernel driver in use: ehci_hcd
00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)
	Subsystem: nVidia Corporation Device [10de:cb84]
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd
00:07.0 Audio device [0403]: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio [10de:0774] (rev a1)
	Subsystem: Acer Incorporated [ALI] Device [1025:0153]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 SATA controller [0106]: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller [10de:0ad4] (rev a2)
	Subsystem: Acer Incorporated [ALI] Device [1025:0153]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
	Subsystem: Acer Incorporated [ALI] Device [1025:0153]
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
00:10.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0778] (rev a1)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:12.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:075b] (rev a1)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:13.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
	Kernel driver in use: k10temp
	Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV710 [Radeon HD 4350] [1002:954f]
	Subsystem: PC Partner Limited Device [174b:e990]
	Kernel driver in use: radeon
	Kernel modules: radeon
02:00.1 Audio device [0403]: ATI Technologies Inc RV710/730 [1002:aa38]
	Subsystem: PC Partner Limited R700 Audio Device [Radeon HD 4000 Series] [174b:aa38]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
04:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series Firewire Controller [1106:3403]
	Subsystem: Acer Incorporated [ALI] Device [1025:0153]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

other output to follow in separate post

---

### Post by mdm27 on 2011-09-13
Don't think it is my USB stick because it works fine with windows, plus I don't have a USB on my laptop.

---

### Post by praseodym on 2011-09-13
There is no card listed. Check your BIOS settings for a wireless device. Plus:

```
cat /etc/udev/rules.d/70-persistent-net.rules
rfkill list
```

Wired is working good?

---

### Post by mdm27 on 2011-09-13
sorry, how do I do that?

---

### Post by praseodym on 2011-09-13
Reboot the computer and look at the button to press to enter the BIOS settings (ESC or F2 or F12...). Somewhere should be the possibility to enable/disable the wireless.

---

