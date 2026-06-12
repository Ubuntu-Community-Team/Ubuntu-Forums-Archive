---
title: "No Wireless with 12.04 on HP Mini 1000"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by Daniel9 on 2012-05-31
I just installed 12.04 and can't get a wireless connection. The wired connection works great. I've tried several locations with wifi and none worked.

---

### Post by wildmanne39 on 2012-06-01
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Daniel9 on 2012-06-01
Thanks for replying. I got it up and running this morning. I hadn't activated the driver.

---

### Post by wildmanne39 on 2012-06-01
Hi, that is great! please use the thread tools at the top of the page and mark the thread solved.
Thanks

---

### Post by SteveCampsOut on 2012-07-01
How do you activate the driver? I'm trying to install Ubuntu on a friends HP Mini 1000 and I've never used Linux in my life. Is there a walk through for this somewhere?

---

### Post by wildmanne39 on 2012-07-01
Hi SteveCampsOut, you need to do exactly what post 2 says so we can help you.
Thanks

---

### Post by rsundar on 2012-11-22
Hi,

I just installed ubuntu 12.04 on my HP mini, the details of system are given below:

#cat /etc/lsb-release; uname -a
     DISTRIB_ID=Ubuntu
     DISTRIB_RELEASE=12.04
     DISTRIB_CODENAME=precise
     DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
     Linux mini-HP-Mini 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux
#lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e5:4315] (rev 01)
Subsytem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
Kernel driver in use: b43-pci-bridge
#lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 10f1:1a08 Importek Internal Webcam
Bus 003 Device 002: ID 13d3:3249 IMC Networks Internal Bluetooth
#rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hp-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no

---

### Post by wildmanne39 on 2012-11-22
Hi, please do:
the last two commands from this link.[http://ubuntuforums.org/showthread.php?p=12368349#post12368349](http://ubuntuforums.org/showthread.php?p=12368349#post12368349)

Post 4.
Thanks

---

### Post by rsundar on 2012-11-22
hi,

I get unable to locate package for those two commands

---

### Post by wildmanne39 on 2012-11-22
Hi, did you have a wired connection when you ran those commands? did you just copy and paste for accuracy?
Thanks

---

### Post by rsundar on 2012-11-22
Sorry I should have mentioned this before, no I do not have a wired connection I am currently posting this from my desktop.

---

### Post by wildmanne39 on 2012-11-22
Hi, please use this link [http://ubuntuforums.org/showthread.php?p=12364764#post12364764](http://ubuntuforums.org/showthread.php?p=12364764#post12364764) post 17 to get your wireless working.
Thanks

---

### Post by rsundar on 2012-11-22
Thank you so much it worked. :)

---

### Post by wildmanne39 on 2012-11-22
Your welcome!

---

### Post by BlackMist on 2012-12-10
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux mom-Compaq-Mini-CQ10-100 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:49:53 UTC 2012 i686 i686 i686 GNU/Linux
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
    Kernel driver in use: b43-pci-bridge
--
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Kernel driver in use: atl1c
1:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
    Kernel driver in use: b43-pci-bridge
--
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Hewlett-Packard Company Device [103c:308f]
    Kernel driver in use: atl1c
mom@mom-Compaq-Mini-CQ10-100:~$ lsusb
Bus 001 Device 003: ID 10f1:1a13 Importek 
Bus 002 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lo        no wireless extensions.

eth0      no wireless extensions.
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard bloModule                  Size  Used by
bnep                   17707  2 
rfcomm                 37276  0 
parport_pc             31968  0 
bluetooth             183228  10 bnep,rfcomm
ppdev                  12817  0 
snd_hda_codec_idt      59761  1 
b43                   347284  0 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel
i915                  461351  3 
snd_hwdep              13272  1 snd_hda_codec
mac80211              461161  1 b43
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
drm_kms_helper         45271  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
drm                   230463  4 i915,drm_kms_helper
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
snd_timer              24411  2 snd_pcm,snd_seq
videodev               95841  2 uvcvideo,videobuf2_core
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 13616  0 
sparse_keymap          13658  1 hp_wmi
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
snd                    61991  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                84843  0 
cfg80211              175375  2 b43,mac80211
joydev                 17161  0 
i2c_algo_bit           13197  1 i915
coretemp               13168  0 
wmi                    18590  1 hp_wmi
lpc_ich                16925  0 
soundcore              14599  1 snd
bcma                   34483  1 b43
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
serio_raw              13031  0 
microcode              18209  0 
video                  18847  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
atl1c                  36175  0 
cked: yes

---

### Post by donkris on 2013-02-10
Please help. My wifi isn't working propperly. 

::cat /etc/lsb-release; uname -a::


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux MainFrame 3.2.0-37-generic-pae #58-Ubuntu SMP Thu Jan 24 15:51:02 UTC 2013 i686 i686 i386 GNU/Linux


::lspci -nnk | grep -iA2 net::


01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:145c]
	Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1584]
	Kernel driver in use: r8169


::lsusb::


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b1fe Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305


::iwconfig::


lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.



::rfkill list all::


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no


::lsmod::


Module                  Size  Used by
usbhid                 41937  0 
hid                    77428  1 usbhid
michael_mic            12540  0 
arc4                   12473  0 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_seq_midi           13132  0 
psmouse                86520  0 
lib80211_crypt_tkip    17275  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
wl                   2906597  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i915                  419361  4 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
cfg80211              178877  1 wl
bnep                   17830  2 
parport_pc             32114  0 
snd                    62218  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
drm_kms_helper         45466  1 i915
bluetooth             158479  10 rfcomm,bnep
drm                   197641  5 i915,drm_kms_helper
lib80211               14040  2 lib80211_crypt_tkip,wl
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
soundcore              14635  1 snd
mac_hid                13077  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
tifm_sd                17566  0 
tifm_core              15040  1 tifm_sd
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0

---

