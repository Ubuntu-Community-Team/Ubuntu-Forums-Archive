---
title: "Slow Wireless Speeds Compared to OS X"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by yonexFactory on 2012-04-24
I recently purchased a MacBook Pro, and so far, everything in Ubuntu 12.04 works well, with one minor exception:

I got wireless working with little effort, but I noticed that my wireless speeds are 1/2 to 2/3 as fast in Ubuntu as they are in OS X (10.7).

I've tried

```
rmmod iwlagn

modprobe iwlagn 11n_disable=0
```

which doesn't seem to do anything (and iwconfig still shows "IEEE 802.11bg"). I have also tried disabling wireless power saving using

```
sudo iwconfig wlan0 power off
```

but that just returns a message saying "Operation not supported." And powertop shows wireless power saving as being disabled already anyway.

Any ideas to fix my slow wireless connection?

---

### Post by wildmanne39 on 2012-04-24
Hi, if you have the iwlagn driver then try this:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```
do not reboot if it works we will need to make it permanent.
Thanks

---

### Post by yonexFactory on 2012-04-24
Hey, thanks for the reply. Unfortunately, your above instructions didn't seem to work; my wireless speeds remain the same. Here's my terminal summary:

```
sudo ifconfig wlan0 down
sudo rmmod iwlagn
ERROR: Module iwlagn does not exist in /proc/modules
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```

I think I have the proper driver installed, but I'm not positive. I just followed the instructions [here]("https://help.ubuntu.com/community/MacBookPro8-2/Oneiric#Wireless"), replacing Oneiric with Precise as necessary.

---

### Post by wildmanne39 on 2012-04-24
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by yonexFactory on 2012-04-24
cat /etc/lsb-release; uname -a

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux theNorseMac 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux

```


lspci -nnk | grep -iA2 net

```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
	Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
	Kernel driver in use: tg3
	Kernel modules: tg3
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
	Subsystem: Broadcom Corporation Device [14e4:0000]
	Kernel driver in use: sdhci-pci
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
	Subsystem: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331]
	Kernel driver in use: bcma-pci-bridge
```

iwconfig

```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"theNorseman"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:29:C4:46:A6   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:133  Invalid misc:134   Missed beacon:0

eth0      no wireless extensions.
```

rfkill list all

```
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

lsmod

```
Module                  Size  Used by
msr                    12772  0 
iwlwifi               289862  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_cirrus    23293  1 
rfcomm                 37291  0 
bnep                   17711  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
arc4                   12473  2 
b43                   343208  0 
mac80211              440734  2 iwlwifi,b43
cfg80211              178818  3 iwlwifi,b43,mac80211
ssb                    55319  1 b43
pcmcia                 39791  2 b43,ssb
pcmcia_core            21511  1 pcmcia
joydev                 17393  0 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
bcma                   25587  1 b43
applesmc               18978  0 
input_polldev          13648  1 applesmc
snd_rawmidi            25424  1 snd_seq_midi
btusb                  17919  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
bluetooth             164346  13 rfcomm,bnep,btusb
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414603  3 
snd                    62064  19 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
bcm5974                17199  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
apple_gmux             12655  0 
video                  19068  2 i915,apple_gmux
apple_bl               13425  0 
mac_hid                13077  0 
mei                    36570  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   141369  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
hid_apple              13166  0 
usbhid                 41906  0 
hid                    77367  2 hid_apple,usbhid
```

---

### Post by wildmanne39 on 2012-04-24
Hi, first let's blacklist:
```
echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
then reboot.
Now:
```
sudo rmmod -f b43
sudo modprobe bcma
```
if this helps we will need to make it permanent so do not reboot.
Thanks

---

### Post by yonexFactory on 2012-04-24
Thanks for your continued help.

```
sudo rmmod -f b43
sudo modprobe bcma
```

That only seemed to disable wireless completely.

Note: I removed the the "blacklist iwlwifi" from /etc/modprobe.d/blacklist.conf, since this fix didn't appear to work; let me know if I need to add this back again for other fixes.

---

### Post by wildmanne39 on 2012-04-24
Hi, iwlwifi needs to be blacklisted.

I will help more tomorrow it is getting late I have had a long day.

---

### Post by wildmanne39 on 2012-04-25
Hi, please try this:
```
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
post the output of:
```
dmesg | grep bcma
```
reboot.
Thanks

---

### Post by yonexFactory on 2012-04-30
'dmesg | grep bcma' gives
```
[   16.563675] bcma-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.563691] bcma-pci-bridge 0000:03:00.0: setting latency timer to 64
[   16.563756] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[   16.563783] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[   16.563842] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[   16.563982] bcma: PMU resource config unknown for device 0x4331
[   16.633506] bcma: Bus registered
```

---

### Post by wildmanne39 on 2012-05-02
Hi, please set your wireless settings to match the screenshots and let us know if it helps.
Thanks

---

### Post by yonexFactory on 2012-05-02
Well, I'll be... that seemed to do the trick. Thanks! (1) What exactly do those settings do? (2) I assume I'll need to change those settings if set up any new connections?

---

### Post by wildmanne39 on 2012-05-03
Hi, yes you will need to change those settings for new connections.

Setting the dns server to googles server speeds things up and IPV6 still has issues to be worked out so it is best set to ignore for now, I use the same settings on my system and it has increased my speeds a lot, please use thread tools and mark the thread solved.
Thanks

---

### Post by yonexFactory on 2012-05-03
Gotcha. Thanks again for the help.

---

