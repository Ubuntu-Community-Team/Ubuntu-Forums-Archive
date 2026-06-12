---
title: "Wifi wont turn on."
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by Jce69 on 2011-09-17
Hi, I just installed Ubuntu 11.04 on my laptop. My wifi doesnt work but my wired connection does. Ive tried looking on google and on here. I have a Broadcom 802.11 wireless adapter.. I did the additional drivers and installed the driver it suggested and no such luck and I do have it enabled. My router shows up in Wifi Radar I try to connect and it just hangs. But my wifi doesnt show up in edit connections.

---

### Post by wildmanne39 on 2011-09-18
Hi, welcome to the forum! please open a terminal by hitting ctrl+atl+t then copy and paste the following commands into it, then paste the results here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Jce69 on 2011-09-18
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

```
ason@ubuntu:~$ sudo lshw -C network
[sudo] password for jason: 
  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: f0:de:f1:46:f7:01
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f2400000-f243ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: ac:81:12:49:f8:02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f2500000-f2503fff
jason@ubuntu:~$ 

```

```
03:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
jason@ubuntu:~$ lspci -nn | grep -e 0280 -e 0200

```

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:233
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

```
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
Module                  Size  Used by
binfmt_misc            17565  1 
b44                    36000  0 
ssb                    51945  1 b44
ndiswrapper           249811  0 
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_realtek   336771  1 
lib80211_crypt_tkip    17387  0 
wl                   2568244  0 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
acer_wmi               23809  0 
snd_timer              29602  2 snd_pcm,snd_seq
i915                  515121  3 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ideapad_laptop         13494  0 
videodev               82052  1 uvcvideo
soundcore              12680  1 snd
drm_kms_helper         42136  1 i915
sparse_keymap          13898  2 acer_wmi,ideapad_laptop
v4l2_compat_ioctl32    17078  1 videodev
psmouse                73535  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
intel_ips              18097  0 
drm                   227534  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
lp                     17825  0 
video                  19438  1 i915
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  1 
libahci                26642  1 ahci
atl1c                  41171  0 

```

---

### Post by wildmanne39 on 2011-09-18
Hi run this command and see if it turns on if so we will need to make it permanent.

Unplug your wired connection first and do not restart your computer.
```
sudo rmmod -f acer-wmi
```
Thank you

---

### Post by Jce69 on 2011-09-18
> **wildmanne39 said:**
> Hi run this command and see if it turns on if so we will need to make it permanent.

Unplug your wired connection first and do not restart your computer.
```
sudo rmmod -f acer-wmi
```
Thank you

it worked (:

---

### Post by wildmanne39 on 2011-09-18
Hi, that is great let's make it permanent. Run this command please.
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit

```

If I helped you in some small way would you click on the red link in my signature and show your support for me becoming an ubuntu member? and would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

