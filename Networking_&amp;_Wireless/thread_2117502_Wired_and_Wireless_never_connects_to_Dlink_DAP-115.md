---
title: "Wired and Wireless never connects to Dlink DAP-1155"
date: 2013-02-18
forum: Networking &amp; Wireless
---

### Post by Baba-Juju on 2013-02-18
Hi ,
Just bought a Dlink DAP-1155 but I am not able to connect to this device. (H/W Ver:A1 and F/W Ver: 1.00) My current wired connection and wireless connection are working with my other networks and devices. But it does not want to connect to my new DAP-1155. It sees it keeps on trying to constantly connect without result.

I am using this Dlink DAP-1155 in order to extend my wireless signal.

Some info:
```
jonathan@jonston-Inspiron-N5010:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux jonston-Inspiron-N5010 3.2.0-37-generic-pae #58-Ubuntu SMP Thu Jan 24 15:51:02 UTC 2013 i686 i686 i386 GNU/Linux

```

```
ljonathan@jonston-Inspiron-N5010:~$ lspci -nnk | grep -iA2 net
12:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
	Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1321]
	Kernel driver in use: iwlwifi
--
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Dell Device [1028:0447]
	Kernel driver in use: r8169

```

```
jonathan@jonston-Inspiron-N5010:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:6480 Microdia Sonix 1.3 MP Laptop Integrated Webcam
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 004: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 005: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 002 Device 006: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth

```

```
jonathan@jonston-Inspiron-N5010:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"San Fernando"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:17:88:12:5D   
          Bit Rate=12 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4639   Missed beacon:0

eth0      no wireless extensions.

```

```
jonathan@jonston-Inspiron-N5010:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

```
jonathan@jonston-Inspiron-N5010:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
bnep                   17830  2 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
rfcomm                 38139  12 
btusb                  17948  2 
snd_rawmidi            25424  1 snd_seq_midi
bluetooth             158479  23 bnep,rfcomm,btusb
parport_pc             32114  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 41937  0 
hid                    77428  1 usbhid
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17393  0 
i915                  419361  8 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
iwlwifi               366524  0 
i2c_algo_bit           13199  1 i915
mac_hid                13077  0 
binfmt_misc            17292  1 
mei                    36570  0 
mac80211              436493  1 iwlwifi
cfg80211              178877  2 iwlwifi,mac80211
intel_ips              17822  0 
dell_wmi               12601  0 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
video                  19068  1 i915
sparse_keymap          13658  1 dell_wmi
psmouse                86520  0 
serio_raw              13027  0 
wmi                    18744  1 dell_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0 

```

Any help is welcome.

---

### Post by ahallubuntu on 2013-02-18
~

---

### Post by Baba-Juju on 2013-02-18
> **ahallubuntu said:**
> Is the DAP-1155 itself connecting to your network - or do you have other devices working on the DAP-1155 just not this one?

Stick with wired at first - that is easier to figure out - then get wireless going.

How did you setup the DAP-1155?  What is it supposed to be connected to to get a network/internet connection (that it will then relay to your other devices)?
I can not setup the DAP-1155 since I can not connect to it even when wired. It detects a wired connection and if I try to connect to the wired connection it keeps on trying and eventually fails. Reseting the DAP-1155 does not change anything. This is also valid when trying it wirelessly.

---

### Post by praseodym on 2013-02-18
Deactivate the N-mode of the driver (bug):

```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
First line is "one" line, you better copy/paste it.

---

### Post by Baba-Juju on 2013-02-18
No change with your code. I restarted the laptop and also no change.

---

### Post by praseodym on 2013-02-19
Check the router settings, if a MAC-address filter is activated. If so, deactivate it. Router firmware is up-to-date?

---

### Post by Baba-Juju on 2013-02-19
> **praseodym said:**
> Check the router settings, if a MAC-address filter is activated. If so, deactivate it. Router firmware is up-to-date?

Praseodym: Thanks for the info but I am confused about the following: When you ask me to check my router settings - Do you mean my router with internet or do you mean my new router Dlink DAP-1155? 

My router with internet is fine. I can connect to it and can also check my router settings etc. But with my new Dlink DAP-1155 (I bought it for the sole purpose of extending my WIFI signal) I can not connect to it in any way: wired or wirelessly my network manager icon keeps on trying to connect but never does.
Thxs in advance!

---

