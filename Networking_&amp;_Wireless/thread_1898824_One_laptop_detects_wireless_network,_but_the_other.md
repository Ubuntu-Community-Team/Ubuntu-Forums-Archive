---
title: "One laptop detects wireless network, but the other laptop doesn't..."
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by mr.interested on 2011-12-22
Hi there,

I'm running Ubuntu 11.10 on two laptops. One laptop is able to detect a wireless network (from the modem TL-WR340G), but the other laptop doesn't see the network. However, all other wireless networks that are in the vicinity of the house are detected by both laptops.

When the laptop is connected through cable to the modem, the connection is fine.

How is it possible that two very same operating systems detect different networks? The modem is just next to the laptops, and so the coverage is at maximum. Why the other laptop cannot see this particular network?

Best

---

### Post by praseodym on 2011-12-22
Are you sure that both laptops are the same? Check the following on both systems:

```
iwlist chan
dmesg | grep country
```
On which channel does the router send?

---

### Post by mr.interested on 2011-12-22
> **praseodym said:**
> Are you sure that both laptops are the same? Check the following on both systems:

```
iwlist chan
dmesg | grep country
```
On which channel does the router send?

Thanks for the reply praseodym. The output of "iwlist chan" from the first laptop (the one that works) is as follows:

```
lo        no frequency information.

eth0      no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.472 GHz (Channel 13)
```

From the second (that one that doesn't work):

```
lo        no frequency information.

eth0      no frequency information.

eth1      no frequency information.
```

There's no output of "dmesg | grep country".

The output of "iwconfig" from the first laptop:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"***"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:301   Missed beacon:0
```

And the second: (I temporarily connected another router to the modem that is not detectable from the second laptop.)

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

---

### Post by praseodym on 2011-12-22
Looks like a Broadcom-device with the STA-driver on the 2nd laptop (interface name eth1)?! Please show from there:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
```

[COLOR="Red"]Edit[/COLOR]: Plus

```
iwlist chan
dmesg | grep country
```
Which country do you live?

---

### Post by mr.interested on 2011-12-23
> **praseodym said:**
> Looks like a Broadcom-device with the STA-driver on the 2nd laptop (interface name eth1)?! Please show from there:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
```

[COLOR="Red"]Edit[/COLOR]: Plus

```
iwlist chan
dmesg | grep country
```
Which country do you live?

Thanks for your reply, I appreciate your help.

```
$ lspci -nnk | grep -iA2 net
08:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: wl
--
20:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Dell Device [1028:0418]
	Kernel driver in use: r8169

```

```
$ lsmod
Module                  Size  Used by
webcamstudio           23949  0 
michael_mic            12612  8 
arc4                   12529  4 
bnep                   18436  2 
rfcomm                 47946  8 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  0 
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
uvcvideo               72711  0 
videodev               92992  2 webcamstudio,uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
lib80211_crypt_tkip    17390  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
wl                   2568210  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211               14991  2 lib80211_crypt_tkip,wl
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
i915                  567092  3 
ahci                   26002  1 
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
r8169                  52788  0 
libahci                26861  1 ahci
i2c_algo_bit           13423  1 i915
wmi                    19256  1 dell_wmi
video                  19412  1 i915

```

```
$ rfkill list
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

```
$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

eth2      no frequency information.

```

```
$ dmesg | grep country
```

The above command again returns nothing.

---

### Post by praseodym on 2011-12-23
Blacklist the following driver:

```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.cnf
```
and reboot. Change the encryption settings to WPA2-AES if possible. Same checks again. Alternatively try the driver b43 instead.

---

### Post by mr.interested on 2011-12-23
> **praseodym said:**
> Blacklist the following driver:

```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.cnf
```
and reboot. Change the encryption settings to WPA2-AES if possible. Same checks again. Alternatively try the driver b43 instead.

praseodym, you were of valuable help--thanks a million! It works perfectly now :-)

The first command didn't work, and because I didn't have access to the router, I've switched to another driver from Broadcom STA  (System settings --> Additional Drivers --> Remove). Can't believe it was that simple!

---

