---
title: "Install Wi-Fi drivers"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by yoweliz on 2011-08-03
i bought a Acer Aspire 4250 laptop i want to install the wi-fi driver for this and use the laptop as a wi-fi hot spot for me to connect my ipod to the internet.
pls help me.
thnkx

---

### Post by wildmanne39 on 2011-08-03
Hi, lets see if we can get your wireless working, but as for the wifi hotspot I know nothing about how to set it up.

Run these commands please in a terminal, you can open it by hitting ctrl+alt+t:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
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
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by yoweliz on 2011-08-03
> **wildmanne39 said:**
> Hi, lets see if we can get your wireless working, but as for the wifi hotspot I know nothing about how to set it up.

Run these commands please in a terminal, you can open it by hitting ctrl+alt+t:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
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
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you
yohan@ubuntu:~$ sudo lshw -c network
[sudo] password for yohan: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: e8:9a:8f:5a:5a:4b
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:90200000-9023ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: cc:af:78:60:aa:de
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-30-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90100000-9010ffff
yohan@ubuntu:~$ 
yohan@ubuntu:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
yohan@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

yohan@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
yohan@ubuntu:~$ lsmod
Module                  Size  Used by
ppp_deflate             4450  0 
zlib_deflate           21866  1 ppp_deflate
bsd_comp                5307  0 
ppp_async               8070  1 
crc_ccitt               1699  1 ppp_async
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11395  0 
snd_hda_intel          26147  2 
arc4                    1497  2 
snd_hda_codec         100919  1 snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
ath9k                 101858  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
fglrx                2525261  104 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
ath9k_common            6874  1 ath9k
ath9k_hw              314654  2 ath9k,ath9k_common
ath                    10413  2 ath9k,ath9k_hw
mac80211              267099  2 ath9k,ath9k_common
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62411  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
option                 16661  2 
usb_wwan               12201  1 option
cfg80211              170581  4 ath9k,ath9k_common,ath,mac80211
v4l2_compat_ioctl32    12614  1 videodev
snd                    64277  12 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbserial              40364  7 option,usb_wwan
psmouse                62080  0 
serio_raw               4910  0 
lp                     10201  0 
led_class               3393  1 ath9k
video                  22176  0 
output                  2527  1 video
i2c_piix4              10047  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
hid                    84710  1 usbhid
usb_storage            50788  0 
ahci                   22370  2 
atl1c                  34955  0 
libahci                26148  1 ahci
yohan@ubuntu:~$

---

### Post by wildmanne39 on 2011-08-03
Hi, try these two commands one at a time.
```
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
```

If that works we will need to make it persistent.

Also is your network set to WPA and WPA2 mixed mode? That is often causes problems? If you can, try WPA2 only.
Thank you

---

### Post by josephmills on 2011-08-03
> **yoweliz said:**
> yohan@ubuntu:~$ sudo lshw -c network
[sudo] password for yohan: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: e8:9a:8f:5a:5a:4b
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:90200000-9023ffff ioport:2000(size=128)
  *-network
       [COLOR="Red"]description: Wireless interface[/COLOR]
       [COLOR="red"]product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.[/COLOR]
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: cc:af:78:60:aa:de
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="red"]driver=ath9k driverversion=2.6.35-30-generic[/COLOR] firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90100000-9010ffff
yohan@ubuntu:~$ 
yohan@ubuntu:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [COLOR="red"][168c:002b][/COLOR] (rev 01)
yohan@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

yohan@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	[COLOR="red"]Soft blocked: no
	Hard blocked: no[/COLOR]
yohan@ubuntu:~$ lsmod
Module                  Size  Used by
ppp_deflate             4450  0 
zlib_deflate           21866  1 ppp_deflate
bsd_comp                5307  0 
ppp_async               8070  1 
crc_ccitt               1699  1 ppp_async
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11395  0 
snd_hda_intel          26147  2 
arc4                    1497  2 
snd_hda_codec         100919  1 snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
[COLOR="red"]ath9k                 101858  0 [/COLOR]
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
fglrx                2525261  104 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
[COLOR="red"]ath9k_common            6874  1 ath9k
ath9k_hw              314654  2 ath9k,ath9k_common
ath                    10413  2 ath9k,ath9k_hw
mac80211              267099  2 ath9k,ath9k_common[/COLOR]
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62411  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
option                 16661  2 
usb_wwan               12201  1 option
[COLOR="red"]cfg80211              170581  4 ath9k,ath9k_common,ath,mac80211[/COLOR]
v4l2_compat_ioctl32    12614  1 videodev
snd                    64277  12 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbserial              40364  7 option,usb_wwan
psmouse                62080  0 
serio_raw               4910  0 
lp                     10201  0 
[COLOR="red"]led_class               3393  1 ath9k[/COLOR]
video                  22176  0 
output                  2527  1 video
i2c_piix4              10047  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
hid                    84710  1 usbhid
usb_storage            50788  0 
ahci                   22370  2 
atl1c                  34955  0 
libahci                26148  1 ahci
yohan@ubuntu:~$

Hi there lets try and do a ```
sudo modprobe ath9k
``` anything if not you might have to switch over to wicd but first could we also see a ```
uname -a 
``` let me guess here it sees all networks but after entering password it sits and spins? Just a guess

---

### Post by seyavash on 2012-05-28
any final solution?! i have serious problem with this wireless! plz

---

### Post by shafi.dude99 on 2012-05-28
i had the same problem .... just make sure that ur wifi is working, that is check for wifi led is working or not...

---

### Post by lisati on 2012-05-28
Back to sleep, old thread.

---

