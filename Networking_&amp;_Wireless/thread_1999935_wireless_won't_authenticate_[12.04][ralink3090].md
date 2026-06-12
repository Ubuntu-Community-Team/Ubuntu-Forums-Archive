---
title: "wireless won't authenticate [12.04][ralink3090]"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by louis_mallow on 2012-06-08
I moved from 10.04 to 12.04 by clean install. Previously I've had to use additional drivers, but 12.04 seems to recognise my wireless card no problem. The card can see my home network. Wired networking is okay.

No matter how I configure the wifi network, 12.04 will not connect; keeps looping back to 'Authentication required by wireless network'. All Windows and Android and iOS devices still connect fine.

Tried:
Setting wifi to WEP, also open, usually WPA2 AES
Every concievable setting in the network manager

I put off upgrading until a LTS came out to avoid this sort of thing. Makes me sad.Please can the community help me save Ubuntu's reputation in our house?

---

### Post by praseodym on 2012-06-09
Please show:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
dmesg | grep rt2
```
What kind of computer is that?

---

### Post by praseodym on 2012-06-09
Plus this one:

```
grep rt2 /etc/modprobe.d/*
```

---

### Post by louis_mallow on 2012-06-09
Hi, it's an ASUS Netbook, with a (fairly common) Ralink 3090 card.

Here's the output from thos commands:

```
admin@Linux:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
	Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
	Subsystem: AzureWave Device [1a3b:1087]
	Kernel driver in use: rt2800pci
```

```
admin@Linux:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
uas                    17828  0 
usb_storage            39646  1 
joydev                 17393  0 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
uvcvideo               67203  0 
snd_hda_codec_realtek   174055  1 
videodev               86588  1 uvcvideo
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
psmouse                72919  0 
snd_hwdep              13276  1 snd_hda_codec
serio_raw              13027  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48858  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  2 rt2x00lib,mac80211
i915                  414672  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
mac_hid                13077  0 
wmi                    18744  1 asus_wmi
eeprom_93cx6           12653  1 rt2800pci
soundcore              14635  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36718  0 
```



```
admin@Linux:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
```



```
admin@Linux:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```


```
admin@Linux:~$ dmesg | grep rt2
[   17.200386] rt2800pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.200429] rt2800pci 0000:02:00.0: setting latency timer to 64
[   17.257418] Registered led device: rt2800pci-phy0::radio
[   17.257505] Registered led device: rt2800pci-phy0::assoc
[   17.257596] Registered led device: rt2800pci-phy0::quality
[   19.156006] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  700.113933] rt2800pci 0000:02:00.0: PCI INT A disabled
[  700.638857] rt2800pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  704.475636] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```


```
admin@Linux:~$ grep rt2 /etc/modprobe.d/*
[no result]
```

---

### Post by praseodym on 2012-06-09
The card is "on", try to uninstall the package "resolvconf"
```

sudo apt-get remove --purge resolvconf
sudo /etc/init.d/networking restart
```
Maybe it helps to deactivate the PM:

```
sudo iwconfig wlan0 power off
```

---

### Post by louis_mallow on 2012-06-09
Thanks - tried all that, still no success. However, I've decided that since Unity has made this whole thing four times more difficult, as well as the wireless issue, the new Ubuntu just isn't for me.

Many thanks for your help, but I'm now going to distro-surf and find a new OS for the netbook.

---

