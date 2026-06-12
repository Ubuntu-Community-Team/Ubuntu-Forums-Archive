---
title: "Trouble with both wired/wireless connection"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by seanrok190 on 2013-06-07
Hi guys, I'm very new to linux, and to ubuntu as well.

One thing that I've been having trouble with for a week or two is the connection. I tried searching on google and in the forums, but no solution seemed to work.

The situation is this. My wireless connects, but only on reboot. If it sleeps at all, wireless cannot reconnect. It is shown, but fails to reconnect and times out after trying for a while.

My wired connection is almost worse. It works probably 10 seconds every 30 seconds, and is very intermittent. It's strange though, because sometimes it just won't work for an hour. 

My laptop is HP Pavilion dv6, and help would be much appreciated.

---

### Post by praseodym on 2013-06-07
Hi,

please open a terminal with CTRL+ALT+T and show these outputs:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
cat /etc/network/interfaces
iwconfig
ifconfig -a
rfkill list
```

---

### Post by seanrok190 on 2013-06-07
uname -a
Linux sean-HP-Pavilion-dv7-Notebook-PC 3.5.0-32-generic #53~precise1-Ubuntu SMP Wed May 29 20:33:37 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


lspci -nnk | grep -iA2 net
It says (lspci not found) how do i download package pciutils..?

lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 5986:02ac Acer, Inc 

lsmod
Module                  Size  Used by
nls_utf8               12558  1 
isofs                  40307  1 
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_idt      70774  1 
joydev                 17694  0 
coretemp               13642  0 
uvcvideo               78117  0 
arc4                   12530  2 
kvm                   422160  0 
snd_hda_intel          34063  3 
ghash_clmulni_intel    13221  0 
bnep                   18240  2 
radeon                917824  1 
videobuf2_core         33025  1 uvcvideo
parport_pc             32867  0 
aesni_intel            51134  0 
ttm                    88495  1 radeon
i915                  535128  3 
iwlwifi               399576  0 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
hp_wmi                 18093  0 
sparse_keymap          13891  1 hp_wmi
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
ppdev                  17114  0 
rfcomm                 47562  0 
drm_kms_helper         49259  2 radeon,i915
hp_accel               25977  0 
wmi                    19257  1 hp_wmi
drm                   290344  7 radeon,ttm,i915,drm_kms_helper
mei                    41410  0 
lp                     17800  0 
lpc_ich                17145  0 
videodev              125126  2 uvcvideo,videobuf2_core
mac80211              555272  1 iwlwifi
snd_hwdep              17765  1 snd_hda_codec
aes_x86_64             17256  1 aesni_intel
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
lis3lv02d              19878  1 hp_accel
bluetooth             211812  10 bnep,rfcomm
videobuf2_vmalloc      12861  1 uvcvideo
rtsx_pci_ms            13181  0 
snd_seq_midi           13325  0 
memstick               16606  1 rtsx_pci_ms
snd_rawmidi            30750  1 snd_seq_midi
videobuf2_memops       13405  1 videobuf2_vmalloc
psmouse               102506  0 
cfg80211              208382  2 iwlwifi,mac80211
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
serio_raw              13216  0 
input_polldev          13897  1 lis3lv02d
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13254  0 
microcode              23030  0 
video                  19653  1 i915
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                46563  3 parport_pc,ppdev,lp
soundcore              15092  1 snd
i2c_algo_bit           13565  2 radeon,i915
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
rtsx_pci_sdmmc         17801  0 
ahci                   25869  3 
libahci                27338  1 ahci
rtsx_pci               33680  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  62766  0 

cat /etc/network/interfaces
auto lo
iface lo inet loopback

iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 10:1f:74:0c:3c:d2  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:fe0c:3cd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12184495 (12.1 MB)  TX bytes:1617701 (1.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:208681 (208.6 KB)  TX bytes:208681 (208.6 KB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:af:da:68  
          inet6 addr: fe80::8ea9:82ff:feaf:da68/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59548 (59.5 KB)  TX bytes:63164 (63.1 KB)


rfkill list

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by praseodym on 2013-06-07
Deactivate the N-mode of the wireless driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Installation of the tools:
```

sudo apt-get install pciutils
```

---

### Post by seanrok190 on 2013-06-07
Now I'm sad..

sean@sean-HP-Pavilion-dv7-Notebook-PC:~$ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
bash: [: missing `]'


I tried inputting that command and it spat out something was "missing".
Tried to get the tools, and it says the same thing

sean@sean-HP-Pavilion-dv7-Notebook-PC:~$ sudo apt-get install pciutils
bash: [: missing `]'

---

### Post by praseodym on 2013-06-07
[http://ubuntu.wallawalla.edu/ubuntu//pool/main/p/pciutils/pciutils_3.1.8-2ubuntu5_amd64.deb](http://ubuntu.wallawalla.edu/ubuntu//pool/main/p/pciutils/pciutils_3.1.8-2ubuntu5_amd64.deb)

Here is the pciutils-file. Install it by Double-click

---

### Post by seanrok190 on 2013-06-07
> **praseodym said:**
> Deactivate the N-mode of the wireless driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Installation of the tools:
```

sudo apt-get install pciutils
```

I have the package, but I still can't execute these commands. 

lspci

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

```

---

### Post by praseodym on 2013-06-07
Can you open the file with this:
```

gksu gedit /etc/modprobe.d/iwlwifi.conf
```
Insert```

options iwlwifi 11n_disable=1
```
Save, close the editor and reboot.

---

### Post by seanrok190 on 2013-06-07
I was able to save it with the editor.
It didn't really solve my problem though, still can't access wifi after suspend..

---

### Post by tgalati4 on 2013-06-07
Check with HP's website.  You might need a BIOS update.

---

