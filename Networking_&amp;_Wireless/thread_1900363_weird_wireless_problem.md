---
title: "weird wireless problem"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by fouadk on 2011-12-26
hi everyone...

i am facing a weird problem with my wireless.
im on ubuntu 11.04 and my laptop has a broadcom card.

network manager shows available wireless access points except my wireless router.
i havent made nay changes to my router....its been sitting there for over a year with no configuration changes....windows 7 can connect normally to it....my android and symbian devices connect normally to it except my ubuntu....its been working fine and then i shutdown and the next day my access point isnt there in network manager.

can anyone think of what might the problem be?

thanks in advance

---

### Post by cappybob on 2011-12-26
Having same problem, as many others.

---

### Post by guv999 on 2011-12-26
Me too
My Wireless card is Realtek RTL8192e.
[LIST]
[*]It can actually detect two of my next door neighbours WIFI networks but not my own when using Lubuntu 11.10
[*]To this end I am satisfied that the laptop and wireless card are working normally.
[*]The Windows 7 partition on the device is working normally
[*]I have investigated any potential router issues and can confirm that:
[*]The device MAC address is correctly logged in the routers access list
[*]All other wireless devices in the house are working perfectly
[*]This all leads me to believe that the router is functioning okay as well
[/LIST]

Any advice is greatly appreciated - the thing that gets me is that it is picking up other networks but not my own.

---

### Post by wildmanne39 on 2011-12-26
Hi fouadk, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by fouadk on 2011-12-27
```

cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux TURBO 2.6.38-13-generic #53-Ubuntu SMP Mon Nov 28 19:23:39 UTC 2011 i686 athlon i386 GNU/Linux

```
```

lspci -nnk | grep -iA2 net

00:06.0 Ethernet controller [0200]: nVidia Corporation MCP65 Ethernet [10de:0450] (rev a3)
	Subsystem: Hewlett-Packard Company Device [103c:30cf]
	Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
	Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1375]
	Kernel driver in use: wl

```
```

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```

rfkill list all

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```
```

lsmod

Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  293 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
joydev                 17322  0 
ppdev                  12849  0 
dm_crypt               22463  1 
nvidia               9766978  43 
snd_hda_codec_conexant    43782  1 
binfmt_misc            13213  1 
rfcomm                 38125  10 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
lib80211_crypt_tkip    17203  0 
r852                   17878  0 
sm_common              16737  1 r852
wl                   2642531  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand                   49822  2 r852,sm_common
btusb                  18160  2 
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
psmouse                73312  0 
mtd                    26720  2 sm_common,nand
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw              12990  0 
k8temp                 12872  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  2 lib80211_crypt_tkip,wl
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
video                  18951  0 
firewire_core          56138  1 firewire_ohci
ahci                   21591  3 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
pata_amd               13762  0 
forcedeth              58190  0 
libahci                25548  1 ahci


```

---

### Post by wildmanne39 on 2011-12-27
Hi, please do the following:
```
sudo apt-get purge broadcom-sta-source
```
Then do:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
unplug wired connection and reboot.
Thanks

---

### Post by fouadk on 2011-12-29
for some reason the broadcom-sta-source was not installed...i re-added it via synaptic and wireless is working perfectly again

thanks everyone for your effort and time

---

### Post by wildmanne39 on 2011-12-29
Hi, I am glad you got it working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

