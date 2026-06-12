---
title: "Wireless on Lenovo Permanently disabled."
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by Ben2r25 on 2011-10-07
I have a Lenovo v570 with a Centrino Wireless-N + WiMAX 6150 card. I'm running an up to date Ubuntu 11.04. The network manager applet says "wireless is disabled." I can click "enable wireless" and this puts a check next to enable wireless, but it still does not work. The hardware switch is turned on. Any ideas?

---

### Post by praseodym on 2011-10-07
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
```

---

### Post by Ben2r25 on 2011-12-10
I have upgraded to Ubuntu 11.10 and the issue is still here. 
```
robert@robert-Lenovo-V570:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0886] (rev 67)
	Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1315]
	Kernel driver in use: iwlagn
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Lenovo Device [17aa:3975]
	Kernel driver in use: r8169

```

```
robert@robert-Lenovo-V570:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
iwlagn                314213  0 
mac80211              462092  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
acer_wmi               23948  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
rts5139               351143  0 
ideapad_laptop         13871  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
snd_seq_midi_event     14899  1 snd_seq_midi
wmi                    19256  1 acer_wmi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17083  1 videodev
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  566827  3 
drm_kms_helper         42558  1 i915
psmouse                73882  0 
drm                   236290  4 i915,drm_kms_helper
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 
robert@robert-Lenovo-V570:~$ 
```

```
robert@robert-Lenovo-V570:~$ rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
robert@robert-Lenovo-V570:~$
```

```
robert@robert-Lenovo-V570:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
robert@robert-Lenovo-V570:~$ 

```

---

### Post by praseodym on 2011-12-11
The module "acer_wmi" is not needed on a Lenovo, blacklist it:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot.

---

### Post by Ben2r25 on 2011-12-11
> **praseodym said:**
> The module "acer_wmi" is not needed on a Lenovo, blacklist it:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot.

I blacklisted the module. Now when I click on the network icon, it also says "wireless is disabled by hardware switch." Flipping the actual hardware switch back and forth has no effect on this.

---

### Post by Ben2r25 on 2011-12-11
And it now reports that the wireless is soft blocked and hard blocked:

```
robert@robert-Lenovo-V570:~$ rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
robert@robert-Lenovo-V570:~$
```

---

### Post by praseodym on 2011-12-11
Try

```
sudo rfkill unblock all
```
Any buttons/switches/keys/key combinations (Fn+F2, etc.)?

---

### Post by Ben2r25 on 2011-12-11
> **praseodym said:**
> Try

```
sudo rfkill unblock all
```
Any buttons/switches/keys/key combinations (Fn+F2, etc.)?

Now rfkill list gives:

```
robert@robert-Lenovo-V570:~$ rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
robert@robert-Lenovo-V570:~$
```

The wireless still will not work and, when clicking on the wireless icon it still says "wireless is disabled by hardware switch."

---

### Post by praseodym on 2011-12-11
Check, if wireless can be activated in your BIOS. Try also to reset the BIOS

---

### Post by Ben2r25 on 2011-12-11
Resetting the bios worked! Thanks for the help

---

