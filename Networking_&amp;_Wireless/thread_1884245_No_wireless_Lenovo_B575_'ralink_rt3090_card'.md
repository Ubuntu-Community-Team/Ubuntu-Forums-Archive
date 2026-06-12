---
title: "No wireless: Lenovo B575 'ralink rt3090 card'"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by jameswm on 2011-11-20
After having Windows 7 crash on me all the time, and getting tired of it, I wound up turning to Ubuntu for my laptop. I have Ubuntu 11.10 on there running fine, but my wireless internet wont work. Wired does; just not wireless. I've found other people with this problem, but nothing I've found seems to help. All the threads I've found in places are either unanswered or the conversation stopped abruptly. (Another random problem to tack on that I just noticed: when I close my laptop with Ubuntu running and open it back up, the screen is black and I have to manually shut it down and restart it.)
 My wireless card is a Ralink rt3090 and I'm using a Lenovo B575. 
Thanks a lot!!!

---

### Post by jameswm on 2011-11-21
Bumpin for high hopes. :s

---

### Post by praseodym on 2011-11-21
Hi,

please show the outputs of:
```
uname -a
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
dmesg | egrep 'rt2|rt3'
```

---

### Post by jameswm on 2011-11-21
> **praseodym said:**
> Hi,

please show the outputs of:
```
uname -a
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
dmesg | egrep 'rt2|rt3'
```


Here is the results!
> uname -a
Linux james-Lenovo-B575 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
james@james-Lenovo-B575:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Lenovo Device [17aa:3975]
	Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: Lenovo Device [17aa:f101]
	Kernel driver in use: rt2800pci
james@james-Lenovo-B575:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
james@james-Lenovo-B575:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_conexant    62197  1 
snd_hda_codec_hdmi     32040  1 
sp5100_tco             13791  0 
binfmt_misc            17540  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
joydev                 17693  0 
acer_wmi               23948  0 
rts5139               351143  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
arc4                   12529  2 
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              310872  3 rt2800lib,rt2x00pci,rt2x00lib
psmouse                73882  0 
snd_hda_intel          33390  2 
serio_raw              13166  0 
snd_hda_codec         104802  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
cfg80211              199587  2 rt2x00lib,mac80211
k10temp                13166  0 
eeprom_93cx6           12725  1 rt2800pci
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i2c_piix4              13301  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
ideapad_laptop         13871  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon               1015995  4 
wmi                    19256  1 acer_wmi
video                  19412  0 
snd                    68266  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  6 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci
james@james-Lenovo-B575:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
james@james-Lenovo-B575:~$ dmesg | egrep 'rt2|rt3'

---

### Post by praseodym on 2011-11-21
No need for the module acer_wmi on a lenovo:
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Shut off the power management
```
sudo iwconfig wlan0 power off
```
and reboot.

---

### Post by jameswm on 2011-11-22
> **praseodym said:**
> No need for the module acer_wmi on a lenovo:
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Shut off the power management
```
sudo iwconfig wlan0 power off
```
and reboot.

Thank you for your reply, but my wireless still doesn't work after doing this.

---

### Post by jameswm on 2011-11-22
Any more suggestions from anyone, please? Do I really have to go back to Windows? :s

---

### Post by jameswm on 2011-11-22
:( Guess it's back to Windows for me.

---

### Post by praseodym on 2011-11-23
Check if Windows shuts off the card during shutdown. Check the BIOS settings if it can be activated there. You may want to reset the BIOS, too.

---

### Post by jameswm on 2011-11-23
> **praseodym said:**
> Check if Windows shuts off the card during shutdown. Check the BIOS settings if it can be activated there. You may want to reset the BIOS, too.

................. After your comment, it made me think to check boot order.....
WHY did I not think of that? Ubuntu was k set to load before the wireless card. -_- Works fine, now. Thank you! :)

---

### Post by susan :) on 2012-01-05
Hi! I am having the same issue - i have the same results from the commands as you, except my tx-power was off (I turned it on... ). How did you edit your boot order? F2 during bootup? Thank you!!

---

### Post by kpuz on 2012-01-08
> **susan :) said:**
> Hi! I am having the same issue - i have the same results from the commands as you, except my tx-power was off (I turned it on... ). How did you edit your boot order? F2 during bootup? Thank you!!

Have you tried blacklisting the acer_wmi module?

---

