---
title: "Extremely slow internet in 11.10"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by ProfessorUnicorn on 2012-04-20
On my other partition with Windows 7, the internet is perfect, but when I switch to Ubuntu 11.10, it is VERY slow.  I often can't even load web pages.  I don't know what information you need. I am very new to Ubuntu, so any info you need, I will be more than happy to provide. Please help! Oh, and also, the internet runs fine when it is WIRED.  When I'm running through the router, THAT'S when it doesn't work well.

---

### Post by wildmanne39 on 2012-04-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

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

### Post by ProfessorUnicorn on 2012-04-21
My results:


shane@SexyBeast:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux SexyBeast 3.0.0-17-generic-pae #30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012 i686 i686 i386 GNU/Linux
shane@SexyBeast:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:165b]
	Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0886] (rev 67)
	Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1315]
	Kernel driver in use: iwlagn
shane@SexyBeast:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 04f2:b252 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0781:5530 SanDisk Corp. Cruzer U3 4gb SDCZ36
Bus 002 Device 004: ID 8087:07d7 Intel Corp. 
shane@SexyBeast:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:69:33:C9:AA   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-18 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:45  Invalid misc:250   Missed beacon:0

shane@SexyBeast:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
shane@SexyBeast:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  3 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
iwlagn                273973  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_accel               21632  0 
mac80211              393421  1 iwlagn
lis3lv02d              19280  1 hp_accel
cfg80211              172427  2 iwlagn,mac80211
input_polldev          13648  1 lis3lv02d
psmouse                63474  0 
serio_raw              12990  0 
rts_pstor             353227  0 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usb_storage            44173  0 
uas                    17699  0 
ahci                   21634  2 
libahci                25761  1 ahci
r8169                  47200  0 
i915                  509554  2 
xhci_hcd               77120  0 
drm_kms_helper         32889  1 i915
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
drm                   196290  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
wmi                    18744  1 hp_wmi
zram                   18007  1 
shane@SexyBeast:~$

---

### Post by wildmanne39 on 2012-04-21
Hi please try:
```
echo "iwlagn 11_ndisable=1" | sudo tee -a /etc/modules
```
then reboot.
Thanks

---

### Post by ProfessorUnicorn on 2012-04-21
I'm afraid it didn't work. Same slow internet.

---

### Post by wildmanne39 on 2012-04-21
Hi, please post the contents of:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
if it is empty add one line:
```
options iwlagn 11n_disable=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

