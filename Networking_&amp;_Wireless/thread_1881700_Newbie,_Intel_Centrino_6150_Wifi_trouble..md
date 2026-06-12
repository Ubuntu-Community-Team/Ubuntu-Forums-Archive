---
title: "Newbie, Intel Centrino 6150 Wifi trouble."
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by jmbm on 2011-11-16
Hi I am new to ubuntu, actually 11.10 has been my first experience with it, and frankly I'm loving it. Unfortunately I have run into some trouble with my internet connection wich appears to be fluctuating.My internet speed constantly drops and sometimes pages just fail to load even though my download speed seems perfectly fine. I have a dual partition, and I don't have this problems with Windows. Thank You.

---

### Post by WinterMadness on 2011-11-16
im curious, are you able to connect to networks with wpa2?

If you look, i have a thread in this section trying to get the same wireless card to work

---

### Post by praseodym on 2011-11-16
Hi,

please show the terminal (CTRL+ALT+T) outputs of

```
lspci -nnk | grep -iA2 net
iwconfig
sudo iwlist scan
lsmod
```
Try pure WPA2 encryption (change it in your router interface) as WinterMadness wrote above.

---

### Post by jmbm on 2011-11-16
I'm sorry I don't quite get it, is that the same as WPA/WPA2?

```
lego@lego-Satellite-P745:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fc30]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
	Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
	Kernel driver in use: iwlagn
lego@lego-Satellite-P745:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Jah Bless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 68:7F:74:14:BD:3C   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:26  Invalid misc:393   Missed beacon:0

lego@lego-Satellite-P745:~$ sudo iwlist scan
[sudo] password for lego: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 68:7F:74:14:BD:3C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Jah Bless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001822058588
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00094A616820426C657373
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B000103104700108078CEB9E504CF1C8BA5A2013A41C505102100074C696E6B737973102300075752543136304E102400063132333435361042000234321054000800060050F2040001101100075752543136304E100800020084
                    IE: Unknown: DD090010180201F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080000000000000000000000000000000000000000

lego@lego-Satellite-P745:~$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_intel          33390  1 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
joydev                 17693  0 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  566711  3 
iwlagn                314213  0 
mac80211              310872  1 iwlagn
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
jmb38x_ms              17646  0 
cfg80211              199587  2 iwlagn,mac80211
memstick               16569  1 jmb38x_ms
snd                    68266  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
mei                    41480  0 
sparse_keymap          13890  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
xhci_hcd               78641  0 
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
lego@lego-Satellite-P745:~$ 

```

Thanks for all the help guys :)

---

### Post by praseodym on 2011-11-16
Your network uses mixed WPA/WPA2:
> ```
                   IE: IEEE 802.11i/[COLOR="Red"]WPA2[/COLOR] Version 1
...
                   IE: [COLOR="Red"]WPA[/COLOR] Version 1
```
You better change to WPA2. The driver iwlagn is buggy, you need to switch off the N-mode of it:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```
You may also want to rename the ESSID to a name without "blanks", it can also cause problems.

---

### Post by jmbm on 2011-11-16
Thanks, I'll try that and let you know if it did it :D

---

