---
title: "Asus wireless pci card works in Live CD not installation"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by Janomark on 2012-09-07
I'm very new to the forums and just finished installing Ubuntu 12.04 (just as in a few hours ago that I've been looking around to find a solution). As the title states I was able to connect to my router with no issues in the Live CD but after installation finished and I booted up Network Manager tells me I'm connected but everything else such as Firefox disagrees.

Looking around these seem to be the outputs people need to resolve issues. If any other are needed let me know.

lspci
```
alejandro@Metastable:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port D)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port E)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port F)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port H)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx1 port A)
00:0b.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (NB-SB link)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cayman PRO [Radeon HD 6950]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]
02:00.0 SATA controller: JMicron Technology Corp. JMB362 SATA Controller (rev 10)
03:00.0 SATA controller: JMicron Technology Corp. JMB362 SATA Controller (rev 10)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
07:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cayman PRO [Radeon HD 6950]
07:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]
08:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```

iwconfig
```
alejandro@Metastable:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HUERTA"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:58:2E:EA   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

---

### Post by iponeverything on 2012-09-07
the live CD was probably using a different module than the install..

06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

"sudo lsmod" 

to list the loaded modules -- for both the live CD and install

---

### Post by Janomark on 2012-09-08
Thanks for the reply. Here are the requested outputs.

From the install:
```
alejandro@Metastable:~$ sudo lsmod
[sudo] password for alejandro: 
Module                  Size  Used by
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
ext2                   73795  1 
snd_hda_codec_hdmi     32474  2 
arc4                   12529  2 
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
mxm_wmi                12979  0 
sp5100_tco             13791  0 
snd_hda_codec_realtek   224066  1 
serio_raw              13211  0 
edac_core              53746  0 
k10temp                13166  0 
edac_mce_amd           23709  0 
fam15h_power           13115  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
i2c_piix4              13301  0 
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtl8192ce              84826  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
snd_seq_midi           13324  0 
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              205544  2 rtlwifi,mac80211
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                804372  3 
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
wmi                    19256  2 asus_wmi,mxm_wmi
drm                   242038  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  1 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  62099  0 

```

and from the live cd:
```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               23125  0 
snd_hda_codec_hdmi     32474  2 
snd_hda_codec_realtek   224066  1 
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
rtl8192ce              84826  0 
snd_seq_midi_event     14899  1 snd_seq_midi
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sp5100_tco             13791  0 
snd                    78855  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
dm_multipath           23230  0 
fam15h_power           13115  0 
edac_core              53746  0 
parport_pc             32866  0 
k10temp                13166  0 
sparse_keymap          13890  1 asus_wmi
ppdev                  17113  0 
cfg80211              205544  2 rtlwifi,mac80211
bnep                   18281  2 
edac_mce_amd           23709  0 
i2c_piix4              13301  0 
rfcomm                 47604  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13211  0 
lp                     17799  0 
bluetooth             180104  10 bnep,rfcomm
parport                46562  3 parport_pc,ppdev,lp
squashfs               36799  1 
overlayfs              28305  1 
nls_utf8               12557  1 
isofs                  40257  1 
ext2                   73795  0 
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 652957  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
uas                    18180  0 
usb_storage            49198  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
mxm_wmi                12979  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  62099  0 
radeon                804372  3 
ttm                    76949  1 radeon
wmi                    19256  2 asus_wmi,mxm_wmi
drm_kms_helper         46978  1 radeon
drm                   242038  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon

```

from my untrained eye it looks like the same rtl8192 drivers are being used. Any thoughts?

---

### Post by iponeverything on 2012-09-08
nope that is not it..

something else is going on.

---

### Post by Janomark on 2012-09-08
Any suggestions or other outputs that would help?

---

### Post by iponeverything on 2012-09-08
> **Janomark said:**
> Any suggestions or other outputs that would help?

perhaps "route -n" and "sudo iptables -L -n"


also run this to get some output from the logs with:

```
sudo ls -tr | tail -3 | sed ':a;N;$!ba;s/\n/ /g' |awk '{print "tail -vf "$0}' > wifidebug.txt
```

disconnect and connect with wireless --- wait a couple of minutes - to ctrl-c  to stop the above command send the contents of the file wifidebug.txt

---

### Post by Janomark on 2012-09-08
Here's the requested outputs;

route -n
```
alejandro@Metastable:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

iptables
```
alejandro@Metastable:~$ sudo iptables -L -n
[sudo] password for alejandro: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


```

as for the last command it returned right away and the output in the file was:
```
tail -vf Desktop Ubuntu One wifidebug.txt

```
I copy pasted the command just to be sure I had it exactly as you requested.

---

### Post by iponeverything on 2012-09-08
```
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

duplicate routes might be a problem.

```
sudo ifconfig eth0 down
```

messed up the command before.. 
```
sudo ls -tr /var/log | tail -3 | sed ':a;N;$!ba;s/\n/ /g' |awk '{print "tail -vf "$0}'|sh 
```

---

### Post by Janomark on 2012-09-08
Looks like

```
sudo ifconfig eth0 down
```

did the trick! If you think 

```
sudo ls -tr /var/log | tail -3 | sed ':a;N;$!ba;s/\n/ /g' |awk '{print "tail -vf "$0}'|sh
```

will still be useful I'll provide that, otherwise thanks!

---

### Post by iponeverything on 2012-09-08
you can add the ifconfig eth0 down command to /etc/rc.local so that eth0 disabled again after a reboot. 

The cause of the issue is an exercise for another day..

---

