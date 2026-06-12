---
title: "My network doesnt appear on the wifi list"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by smokiespartakus on 2012-01-18
I have an asus rt-n56u router which by the way is brilliant. The problem is my wifi network doesnt appear on the list of nearby wifis even though all the other networks in the neighbourhood seems to be listed (20-30ish).

I'm using (or trying to) ubuntu 11.04, and I've tested Mint 12 as well. 

My computer is an Asus eee 1215b, with some Broadcom 802.11 adapter (cant find any other info from windows) - and it works perfectly in win7.

It's a really odd issue if you ask me - any ideas to what I can do to solve it?

cheers /Jonas

---

### Post by praseodym on 2012-01-18
Hi,

please show the output of

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
dmesg | grep b43
```

---

### Post by smokiespartakus on 2012-01-19
Thanks - Here it is
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: AzureWave Device [1a3b:2047]
	Kernel driver in use: brcmsmac
--
02:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8468]
	Kernel driver in use: atl1c
Module                  Size  Used by
rfcomm                 47946  8 
bnep                   18436  2 
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_realtek   330769  1 
snd_hda_codec_hdmi     32040  1 
wl                   2568210  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
lib80211               14991  1 wl
bcma                   20219  0 
snd_rawmidi            30547  1 snd_seq_midi
binfmt_misc            17540  1 
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon               1015995  3 
snd                    68266  14 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17693  0 
soundcore              12680  1 snd
brcmsmac              631693  0 
ttm                    76805  1 radeon
uvcvideo               72711  0 
brcmutil               17837  1 brcmsmac
mac80211              310872  1 brcmsmac
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
drm_kms_helper         42558  1 radeon
cfg80211              199587  2 brcmsmac,mac80211
eeepc_wmi              12826  0 
psmouse                73882  0 
drm                   236330  5 radeon,ttm,drm_kms_helper
serio_raw              13166  0 
btusb                  18600  2 
asus_wmi               20035  1 eeepc_wmi
bluetooth             166112  23 rfcomm,bnep,btusb
sparse_keymap          13890  1 asus_wmi
sp5100_tco             13791  0 
crc_ccitt              12667  1 brcmsmac
k10temp                13166  0 
i2c_algo_bit           13423  1 radeon
i2c_piix4              13301  0 
video                  19412  0 
wmi                    19256  1 asus_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  0 
uas                    18027  0 
xhci_hcd               78641  0 
atl1c                  41643  0 
ahci                   26002  3 
libahci                26861  1 ahci
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
[    0.290193] pci 0000:00:14.2: reg 10: [mem 0xfeb40000-0xfeb43fff 64bit]

```

---

### Post by praseodym on 2012-01-19
Blacklist these modules:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```
enter these 3 new lines:

```
blacklist bcma
blacklist brcmsmac
blacklist brcm80211
```
sav, close the editor, and reboot. Wireless should work now.

---

### Post by smokiespartakus on 2012-01-19
Thanks - didn't work though.

It's not that my wifi doesn't work, it's just that my router doesn't appear on the lists of wireless networks in the area. It's broadcasting SSID and everyone else can find it. Just not me from my ubuntu.

I'm puzzled...

---

### Post by IndyGunFreak on 2012-01-19
> **smokiespartakus said:**
> Thanks - didn't work though.

It's not that my wifi doesn't work, it's just that my router doesn't appear on the lists of wireless networks in the area. It's broadcasting SSID and everyone else can find it. Just not me from my ubuntu.

I'm puzzled...

Have you tried just "creating a new connection" as if you were connecting to a hidden network... to see if it will let you on your network?

---

### Post by praseodym on 2012-01-19
Did you deactivate the MAC-address filter in the router interface?

---

### Post by smokiespartakus on 2012-01-21
I've figured it out. My router was set to give my laptop a specific ip, and since the windows and linux computername weren't the same it didn't work.

Now I've removed the forced ip, and everything works perfectly.

Thanks for all your help;o)

---

