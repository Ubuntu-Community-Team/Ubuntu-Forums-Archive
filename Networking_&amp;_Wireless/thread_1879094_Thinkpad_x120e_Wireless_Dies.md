---
title: "Thinkpad x120e Wireless Dies"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by ArKZenyX on 2011-11-10
Hi, I have a Thinkpad X120e running on Ubuntu 11.10.  My wireless always dies (the icon disappears) after an hour or two, when I wake up from hibernation, or in one case, when I start my computer up.  I've looked at the other threads and given the output of the required commands below:

```
dennis@Netbook-X120e:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Netbook-X120e 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 athlon i386 GNU/Linux
dennis@Netbook-X120e:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Lenovo Device [17aa:21df]
    Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce
dennis@Netbook-X120e:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
dennis@Netbook-X120e:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
dennis@Netbook-X120e:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
arc4                   12473  2 
rtl8192ce              75448  0 
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95614  1 rtl8192ce
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_codec_conexant    52418  1 
snd_hda_codec_hdmi     31426  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
mac80211              272785  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_hda_intel          28358  2 
snd_hda_codec          91754  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
psmouse                63474  0 
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
serio_raw              12990  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              172392  2 rtlwifi,mac80211
k10temp                12990  0 
sp5100_tco             13495  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i2c_piix4              13093  0 
snd_timer              28932  2 snd_pcm,snd_seq
thinkpad_acpi          73942  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvram                  14029  1 thinkpad_acpi
snd                    55902  15 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,thinkpad_acpi,snd_seq_device
binfmt_misc            17292  1 
video                  18908  0 
wmi                    18744  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
r8169                  47200  0 
ahci                   21634  2 
libahci                25761  1 ahci
dennis@Netbook-X120e:~$ 


```

---

### Post by afxmac on 2011-11-30
Got the same problem...

cheers
afx

---

