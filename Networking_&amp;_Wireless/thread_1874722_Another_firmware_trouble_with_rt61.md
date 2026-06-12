---
title: "Another firmware trouble with rt61"
date: 2011-11-03
forum: Networking &amp; Wireless
---

### Post by funkypotatoe on 2011-11-03
Hello Ubuntu people. After spending the whole day trying to resolve my wi-fi card troubles on my own, i gave up. So here i'm.. :(
wlan0: Interface doesn't support scanning : Network is down
Now i'm stuck. My wlan interface doesn't want to start up and do anything at all. Most of How-to's on internet are 2 (and more) years old.

dmesg:
```
[   24.976011] eth0: no IPv6 routers present
[  142.312019] phy0 -> rt61pci_load_firmware: Error - MCU Control register not ready.

```

iwconfig:
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

lspci -nnk:
```
00:0d.0 Network controller [0280]: Ralink corp. RT2600 802.11 MIMO [1814:0401]
	Subsystem: Advance Multimedia Internet Technology, Inc. Device [18eb:0302]
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci

```

rfkill list all:
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod:
```
Module                  Size  Used by
bnep                   18436  2 
bluetooth             166112  7 bnep
binfmt_misc            17540  1 
snd_via82xx_modem      18825  0 
snd_via82xx            29735  2 
ppdev                  17113  0 
gameport               19693  1 snd_via82xx
snd_ac97_codec        134826  2 snd_via82xx_modem,snd_via82xx
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96755  3 snd_via82xx_modem,snd_via82xx,snd_ac97_codec
snd_mpu401_uart        14169  1 snd_via82xx
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
radeon               1015995  3 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
amd64_edac_mod         24730  0 
psmouse                73882  0 
serio_raw              13166  0 
edac_core              53746  3 amd64_edac_mod
k8temp                 13057  0 
snd                    68266  13 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_mce_amd           23709  1 amd64_edac_mod
rt61pci                32257  0 
snd_page_alloc         18529  3 snd_via82xx_modem,snd_via82xx,snd_pcm
crc_itu_t              12707  1 rt61pci
soundcore              12680  1 snd
i2c_viapro             13153  0 
rt2x00pci              14578  1 rt61pci
rt2x00lib              50325  2 rt61pci,rt2x00pci
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  5 radeon,ttm,drm_kms_helper
mac80211              310872  2 rt2x00pci,rt2x00lib
i2c_algo_bit           13423  1 radeon
parport_pc             36962  1 
cfg80211              199587  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt61pci
shpchp                 37345  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
pata_via               13623  0 
sata_via               13846  4 
skge                   49902  0 

```


#EDIT: sorry forgot to tell - Ubuntu 11.10 x64

---

### Post by gordintoronto on 2011-11-03
Where/when did you see this: "wlan0: Interface doesn't support scanning : Network is down"

As far as I can make out, your wireless adapter is based on the RT2600, which has been supported "out of the box" for four years.

Are you using the Unity interface? Do you have a network manager icon on the panel? When you right-click on it, are you offered an "edit connections" option? Does your router use WPA? Do you know the SSID? The password?

---

### Post by funkypotatoe on 2011-11-04
> **gordintoronto said:**
> Where/when did you see this: "wlan0: Interface doesn't support scanning : Network is down"

As far as I can make out, your wireless adapter is based on the RT2600, which has been supported "out of the box" for four years.

Are you using the Unity interface? Do you have a network manager icon on the panel? When you right-click on it, are you offered an "edit connections" option? Does your router use WPA? Do you know the SSID? The password?

i see message "wlan0: Interface doesn't support scanning : Network is down" when i try to do "iwlist scan".
yes, i'm using unity interface.
yes, i do have network manager icon, and there is "edit connections" button, but there's no "enable wireless" & "create new wireless network" or anything for wireless options.

---

### Post by gordintoronto on 2011-11-04
Run Edit Connections. There's a wireless tab.

---

### Post by funkypotatoe on 2011-11-05
ok. i added new wifi network with my routers SSID (& i switched off any security), and nothing happens. when you press Network Manager's applet with right button there is grayed off "Wireless networks" string and "device not ready" below. 
dmesg gives me : phy0 -> rt61pci_load_firmware: Error - MCU Control register not ready.

---

### Post by funkypotatoe on 2011-11-05
Ubuntu doesn't want to save screenshot of desktop when Network manager's menu is shown after clicking icon with right button.. :(

---

### Post by funkypotatoe on 2011-11-07
any more ideas ?

---

### Post by cvgaviao on 2011-11-09
I'm facing a similar problem that I'm tracking [here]("http://askubuntu.com/questions/75871/dwl-g510-rt61-card-not-recognized").

It seems that the problem is related to the 64bits...

I'll try with a 32bits at night... 

cheers

Cristiano

---

### Post by cvgaviao on 2011-11-10
Confirmed, in 32bits environments (ubuntu 11.10 and Debian 6.03) it works out of box with no problem.

---

