---
title: "No network conn at all."
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by Tiribulus on 2013-07-19
Hi folks,
I have an HP mini running Ubuntu 12.04 (precise)
3.2.0-49-generic kernel.
This machine has been running Ubbuntu for 3 years with no problem until recently. Started with the netbook version a couple back. I now have NO network connectivity at all. Wired or wireless. The little fan looking wave symbol just goes up and down forever and tries various networks, but never connecting. It asks for wireless keys, sees the networks, on and on but no connection. Plug it in  - auto Ethernet, same thing, on and on and on(the connection symbol in Gnome at the top). This is at multiple locations where windows boxes work fine. I do have dozens of wireless networks saved from the last few years. NONE of the one's I've tried will work including the house where everybody else's does. I'd think DHCP or something, but why does it ask for the keys then? I don't know. I'm not the greatest Linux guy and any help would be greatly appreciated. I'd hate to have to reload it or go to windows. I don't know where to start with this. Like I say. Never had a problem before.
Thanks

---

### Post by Hadaka on 2013-07-19
Hi please post the output of..
```
lspci -nnk | grep -iA3 net
rfkill list all
lsmod
cat /etc/network/interfaces
```
thanks.

---

### Post by Tiribulus on 2013-07-19
> **Hadaka said:**
> Hi please post the output of..
```
lspci -nnk | grep -iA3 net
rfkill list all
lsmod
cat /etc/network/interfaces
```
thanks.

Pretty quick on the draw there Bub. Thanks, I'm gonna be gone until tonight. Thanks again.

==========================================================================

victorious@victorious-laptop:~$ lspci -nnk | grep -iA3 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
	Kernel driver in use: wl
	Kernel modules: wl, ssb
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Kernel driver in use: atl1c
	Kernel modules: atl1c

======================================================================

victorious@victorious-laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

==========================================================================

victorious@victorious-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by Hadaka on 2013-07-19
hi..you forgot to post..
```
lsmod
```
meantime..give this a go..
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo modprobe -rf ssb
sudo modprobe -rf wl
sudo modprobe wl
```
wireless working now?

---

### Post by Tiribulus on 2013-07-19
Don't ask me what's goin on, but it works now at my church which was where all the trouble started day before yesterday.. or 3 days ago

================================================================================

victorious@victorious-laptop:~$ lsmod
Module                  Size  Used by
dm_crypt               22528  0 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60251  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
lib80211_crypt_tkip    17240  0 
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
wl                   2906597  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                96718  0 
snd_seq_midi           13132  0 
serio_raw              13027  0 
cfg80211              178877  1 wl
snd_rawmidi            25424  1 snd_seq_midi
lib80211               14040  2 lib80211_crypt_tkip,wl
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  10 rfcomm,bnep
ppdev                  12849  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  428021  2 
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
atl1c                  36718  0 
video                  19115  1 i915

===============================================================================

Do you think I should leave it alone and see if flips out again?
Thanks again for your help

---

### Post by Hadaka on 2013-07-19
Hi, yeah...leave it alone unless it causes
problems. If its not broke...no need to fix it.
Glad its working !
How to mark solved ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Tiribulus on 2013-07-19
> **Hadaka said:**
> Hi, yeah...leave it alone unless it causes
problems. If its not broke...no need to fix it.
Glad its working !
How to mark solved ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
I don't understand. I tried it wired AND wireless in 3 different buildings it would NOT connect then all of a sudden it does. Oh well. I do very much appreciate your gracious attention.

---

