---
title: "Dell Inspiron 560 Wireless woes"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by williamtdr on 2011-08-23
Hello,
I am unable to connect to the Internet on the Dell Insprion 560.  I can see the names of the wireless networks, but when I click on any one of them, it prompts for a password, and then attemps to connect for a while before eventually saying "Wireless Network : disconnected- you are now offline". For now I am using a Tenda USB Wireless card, but having to plug this in anytime I want to use the internet is annoying.

lspci -v reports:
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

rein@Media-Center-Ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: Dell Device 0439
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0439
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fd800000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at dc00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
    Subsystem: Dell Device 0439
    Flags: bus master, fast devsel, latency 0
    Memory at fdd00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 (prog-if 00 [UHCI])
    Subsystem: Dell Device 0439
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 (prog-if 00 [UHCI])
    Subsystem: Dell Device 0439
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at d800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20 [EHCI])
    Subsystem: Dell Device 0439
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fdefa000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: Dell Device 0439
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fdef4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: fdf00000-fdffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: fe000000-fe7fffff
    Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000fcf00000-00000000fcffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 (prog-if 00 [UHCI])
    Subsystem: Dell Device 0439
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at d400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 (prog-if 00 [UHCI])
    Subsystem: Dell Device 0439
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 (prog-if 00 [UHCI])
    Subsystem: Dell Device 0439
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20 [EHCI])
    Subsystem: Dell Device 0439
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fdef8000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
    Subsystem: Dell Device 0439
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 0439
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at cc00 [size=8]
    I/O ports at c880 [size=4]
    I/O ports at c800 [size=8]
    I/O ports at c480 [size=4]
    I/O ports at c400 [size=32]
    Memory at fdef2000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
    Subsystem: Dell Device 0439
    Flags: medium devsel, IRQ 11
    Memory at fdef0000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Atheros Communications Inc. Device 0203
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

02:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
    Subsystem: Hauppauge computer works Inc. WinTV HVR-2250
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
    Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
    Capabilities: <access denied>
    Kernel driver in use: saa7164
    Kernel modules: saa7164

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Dell Device 0439
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at e800 [size=256]
    Memory at fcfff000 (64-bit, prefetchable) [size=4K]
    Memory at fcff8000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at febe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

rein@Media-Center-Ubuntu:~$ 

I am running a dual boot with Windows 7 and Ubuntu 11.04 64-bit.  Any help would be greatly appreciated.
---
I have Super Cow Powers. For more information, open a terminal and type "apt-get moo".

---

### Post by praseodym on 2011-08-24
Try the following module parameter for ath9k:

```
sudo modprobe -rf ath9k
sudo modprobe -v ath9k nohwcrypt=1
sudo service network-manager restart
```
If it works, make it permanent via:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Wired works?

---

### Post by williamtdr on 2011-08-24
Thanks for your reply, praseodym. No, I still cannot connect to the internet. Now the Ethernet does not work, either, and there are two instances of "Atheros AR928X Wireless Network Adapter (PCI-Express))". The two parentheses are not a misspelling, they are in the menu. One of the instances says the network names, but sill won't connect to them, and the other says "device not ready". Thank s again for your quick reply.

---

### Post by praseodym on 2011-08-25
Try the following: Completely remove your wireless and wired profiles in the network-manager applet and reboot the system. Create a new wireless progile and test wired too.

---

### Post by williamtdr on 2011-08-26
Hello,
I removed the "Auto eth0" and "Auto tedact" items from the "Edit Connections" option under the wireless menu, and then restarted the computer. When it booted back up, I selected "tedact" from the wireless menu and entered the password. I achived the same result of the computer attempting to connect to the wireless network for roughly two minutes before finally giving up. Thanks again for your quick reply -
 
William T.
---
I have Super Cow Powers. For more information, open a terminal and type "apt-get moo".

---

### Post by praseodym on 2011-08-26
Can you show:

```
dmesg | grep ath
iwconfig
rfkill list
cat /etc/network/interfaces
route -n
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
lsmod
```

---

### Post by williamtdr on 2011-08-27
rein@Media-Center-Ubuntu:~$ dmesg | grep ath
[    0.630319] device-mapper: multipath: version 1.2.0 loaded
[    0.630321] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.709709] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.709718] ath9k 0000:01:00.0: setting latency timer to 64
[   13.140088] ath: EEPROM regdomain: 0x60
[   13.140091] ath: EEPROM indicates we should expect a direct regpair map
[   13.140093] ath: Country alpha2 being used: 00
[   13.140094] ath: Regpair used: 0x60
[   13.190410] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.191285] Registered led device: ath9k-phy0::radio
[   13.191308] Registered led device: ath9k-phy0::assoc
[   13.191323] Registered led device: ath9k-phy0::tx
[   13.191338] Registered led device: ath9k-phy0::rx
rein@Media-Center-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSIDff/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=18 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff
          
wlan1     IEEE 802.11bgn  ESSID:"tedact"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:7B:FC:07:90   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementn
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:56  Invalid misc:30   Missed beacon:0

rein@Media-Center-Ubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
rein@Media-Center-Ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

rein@Media-Center-Ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan1
rein@Media-Center-Ubuntu:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain domain.actdsltmp
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 208.67.222.222
rein@Media-Center-Ubuntu:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Current Frequency:2.412 GHz (Channel 1)

wlan1     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

rein@Media-Center-Ubuntu:~$ sudo iwlist scan
[sudo] password for rein: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:7B:FC:07:90
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption keyn
                    ESSID:"tedact"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007746819357
                    Extra: Last beacon: 3890ms ago
                    IE: Unknown: 0006746564616374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD090010180202F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000
          Cell 02 - Address: 00:11:95:0C:926
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption keyn
                    ESSID:"BSD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c1105b954
                    Extra: Last beacon: 3590ms ago
                    IE: Unknown: 0003425344
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

wlan1     Scan completed :
          Cell 01 - Address: 00:24:7B:FC:07:90
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption keyn
                    ESSID:"tedact"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000077477195e0
                    Extra: Last beacon: 30ms ago
                    IE: Unknown: 0006746564616374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD090010180202F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000
rein@Media-Center-Ubuntu:~$ lsmod
Module                  Size  Used by
rt2870sta             450556  0 
rt2800usb              18235  0 
rt2800lib              45181  1 rt2800usb
crc_ccitt              12667  2 rt2870sta,rt2800lib
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
cryptd                 20510  0 
aes_x86_64             17208  2 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
arc4                   12529  4 
snd_hda_intel          33211  0 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
ath9k                 118238  0 
mac80211              294370  4 rt2800lib,rt2x00usb,rt2x00lib,ath9k
i915                  514985  3 
ath9k_common           13851  1 ath9k
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
binfmt_misc            17565  1 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42136  1 i915
saa7164               129885  0 
snd                    67382  10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   227495  4 i915,drm_kms_helper
joydev                 17606  0 
dcdbas                 14438  0 
dvb_core              110487  1 saa7164
v4l2_common            17647  1 saa7164
cfg80211              178528  4 rt2x00lib,ath9k,mac80211,ath
psmouse                73535  0 
serio_raw              13166  0 
videodev               82052  2 saa7164,v4l2_common
soundcore              12680  1 snd
i2c_algo_bit           13400  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  1 i915
v4l2_compat_ioctl32    17078  1 videodev
tveeprom               21249  1 saa7164
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
hid_sunplus            12619  0 
usb_storage            53538  0 
usbhid                 46956  0 
hid                    91020  2 hid_sunplus,usbhid
uas                    17996  0 
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0 
rein@Media-Center-Ubuntu:~$ 
I am typing this from the computer with the wireless issues via a wireless usb adapter, the Tenda W311U which I have plugged in while I ran these commands at the terminal, which may change the results a little. Thanks again for your help!
---
William T.
I have Super Cow Powers. For more information, open a terminal and type : "apt-get moo".

---

### Post by praseodym on 2011-08-27
This driver often makes problems with Natty.

Try to run wireless alone without wired (take out the other stick first). Take out the cable and:

```
sudo service network-manager restart
```

---

### Post by williamtdr on 2011-08-27
What do you mean? The ethernet isn't plugged in.

---

### Post by praseodym on 2011-08-28
The modules dell_laptop and dell_wmi are not loaded. Try the first on the fly:

```
sudo modprobe -v dell_laptop
sudo service network-manager restart
```

---

