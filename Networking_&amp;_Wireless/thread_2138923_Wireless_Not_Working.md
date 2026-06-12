---
title: "Wireless Not Working"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by jkirnes13 on 2013-04-25
Hi I just upgraded 13.04, but I'm still having the same problem I had with 12.04, the wireless will not work. I've looked all over the forums and tried for over a year to work on the old version, but never got it to work. My ethernet connection works fine, but with the wireless it detects them, tries to connect and now just says "you are now offline" without even getting a connection. IF anyone could help, that would be great because I want to finally use ubuntu without have to use ethernet cable. Thanks.

P.S. I'm on ASUS computer

---

### Post by praseodym on 2013-04-25
Please show:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
```

---

### Post by kc1di on 2013-04-25
could you go to a terminal and type the following commands and list the output here:
```
lspci
rfkill list 
```

---

### Post by jkirnes13 on 2013-04-26
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
    Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
    Kernel driver in use: iwlwifi
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07d6 Intel Corp. 
Bus 001 Device 004: ID 13d3:5710 IMC Networks 

Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
joydev                 17377  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
coretemp               13355  0 
kvm_intel             132891  0 
arc4                   12615  2 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm                   443165  1 kvm_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ghash_clmulni_intel    13259  0 
iwldvm                241834  0 
i2400m_usb             36375  0 
i2400m                107578  1 i2400m_usb
snd_rawmidi            30180  1 snd_seq_midi
mac80211              606457  1 iwldvm
aesni_intel            55399  0 
wimax                  34760  1 i2400m
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
asus_nb_wmi            12854  0 
asus_wmi               24213  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
iwlwifi               173477  1 iwldvm
i915                  600351  3 
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
mac_hid                13205  0 
wmi                    19070  1 asus_wmi
video                  19390  2 i915,asus_wmi
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
mei                    41158  0 
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
psmouse                95870  0 
lpc_ich                17061  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
serio_raw              13215  0 
atl1c                  41071  0 
ahci                   25731  2 
libahci                31364  1 ahci

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: i2400m-usb:1-1.1:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-wimax: WiMAX
    Soft blocked: yes
    Hard blocked: no

wmx0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by jkirnes13 on 2013-04-26
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: i2400m-usb:1-1.1:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-wimax: WiMAX
    Soft blocked: yes
    Hard blocked: no

---

### Post by praseodym on 2013-04-26
Deactivate the N-mode of the driver (bug) and the power management:

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo iwconfig wlan0 power off

```

---

### Post by jkirnes13 on 2013-04-29
"[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rfv iwlwifi" returned "FATAL: Module iwlwifi is in use".

So I ran sudo rmmod on iwldvm, which was using iwlwifi, and iwlwifi so that the rest of your commands worked. But my wi-fi still doesn't connect.[/FONT][/COLOR]

---

### Post by praseodym on 2013-04-30
Reboot?

---

### Post by jkirnes13 on 2013-04-30
Tried it as well. it still won't connect to a network. it deteacts, but does not connect.

---

### Post by praseodym on 2013-05-01
Check: 

dmesg | egrep 'wlan0|iwl'

---

### Post by jkirnes13 on 2013-05-02
julien@julien-U56E:~$ dmesg | egrep 'wlan0|iwl'
[   13.038731] iwlwifi 0000:02:00.0: irq 51 for MSI/MSI-X
[   13.123414] iwlwifi 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   13.156067] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   13.156072] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   13.156074] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   13.156076] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   13.156078] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   13.156081] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   13.156146] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   13.170568] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.010811] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.010960] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   16.286873] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.287021] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   16.496300] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.497707] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by praseodym on 2013-05-03
Did you activate WWAN and Bluetooth in your BIOS?

---

### Post by ramireddy on 2013-05-03
hi

---

### Post by jkirnes13 on 2013-05-07
I'm not sure...How can I activate them?

---

### Post by praseodym on 2013-05-07
Check the computer manual how to enter the BIOS

---

