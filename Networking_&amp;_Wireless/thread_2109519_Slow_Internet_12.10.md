---
title: "Slow Internet 12.10"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by jradicle11 on 2013-01-27
My internet has been quite slow every since I was able to get wireless to work. I'm dual booting ubuntu 12.10 and windows 7. I've tried disabling ipv6 in terminal and in firefox. 

lsmod 
```
Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_idt      70209  1 
arc4                   12529  2 
coretemp               13400  0 
joydev                 17457  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
microcode              22803  0 
i915                  520539  3 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
b43                   369753  0 
snd_timer              29425  2 snd_pcm,snd_seq
psmouse                95552  0 
mac80211              539908  1 b43
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         49112  1 i915
serio_raw              13215  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
rfcomm                 46619  0 
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
cfg80211              206566  2 b43,mac80211
drm                   288670  4 i915,drm_kms_helper
jmb38x_ms              17416  0 
bcma                   35656  1 b43
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17061  0 
i2c_algo_bit           13413  1 i915
parport_pc             32688  0 
bnep                   18140  2 
memstick               16554  1 jmb38x_ms
soundcore              15047  1 snd
bluetooth             209199  10 rfcomm,bnep
ppdev                  17073  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
wmi                    19070  1 hp_wmi
ir_lirc_codec          12859  0 
lirc_dev               19166  1 ir_lirc_codec
ir_mce_kbd_decoder     12723  0 
ir_sanyo_decoder       12513  0 
ir_sony_decoder        12510  0 
ir_jvc_decoder         12507  0 
ir_rc6_decoder         12507  0 
ir_rc5_decoder         12507  0 
ir_nec_decoder         12507  0 
rc_rc6_mce             12502  0 
video                  19335  1 i915
ene_ir                 18320  0 
rc_core                22330  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
hp_accel               25976  0 
lis3lv02d              19829  1 hp_accel
input_polldev          13896  1 lis3lv02d
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
r8169                  61650  0 
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci
ssb                    52036  1 b43

```iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Ask me about my wiener"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 08:86:3B:16:94:70   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4176  Invalid misc:782   Missed beacon:0

```Thanks for the help!

lspci -nnk |grep -iA2 net
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:137f]
    Kernel driver in use: b43-pci-bridge
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30f7]
    Kernel driver in use: r8169

```

---

### Post by elgordodude on 2013-01-27
> Tx excessive retries:4176  Invalid misc:782 These numbers are excessively high, and point to a connectivity issue with your router.
> Kernel driver in use: b43-pci-bridge
I know the b43 is the default driver for broadcom, but how was it installed? Did you extract it from the Windows driver, or is it the one that started working for you? If the latter you may want to extract the .inf from the Windows .exe and see if that sorts it out.

And nice SSID bet it gives the neighbours a laugh...

---

### Post by jradicle11 on 2013-01-28
I have no issues with any of the other computers that are hooked up to that router. I actually live in a dorm room and just plugged a router into our ethernet port. My roommates mac that is dual booted with osx and ubuntu has no problems with the internet on either partitions. I don't remember how I got the driver but I'll find out and post it.

---

### Post by jradicle11 on 2013-01-28
For some reason, when I make changes in Ubuntu it makes my internet on my windows partition slower as well. I'll make a change in terminal, then switch over to windows 7, and chkdsk will start automatically by itself, then my internet will be slower.

---

### Post by TOMBSTONEV2 on 2013-01-28
Try this, in a terminal type: 
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```If this does not solve your problem, you may want to install the b43 drivers and firmware:
```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```Restart the computer then open a terminal and type:
```
sudo modprobe b43
```

---

### Post by Schnappi1989 on 2013-01-29
The b43 drivers and firmware is adapt for me too or ?

---

### Post by pdforum on 2013-01-29
I think you should be cleared cookies from your browser properly.

---

