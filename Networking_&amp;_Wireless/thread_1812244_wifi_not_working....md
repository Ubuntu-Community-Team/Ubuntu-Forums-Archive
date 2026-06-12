---
title: "wifi not working..."
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by ankur.trapasiya on 2011-07-26
Hello...

I recently purchased lenovo b560 and i am not able to turn my wifi on. "Wireless is disabled" is shown in top panel which shows networking and connections details.

the output of "**sudo lshw -C network" **is as below..

*-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: f0:de:f1:59:65:4b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f2400000-f243ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: c0:cb:38:98:08:f2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-10-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f2500000-f250ffff


I surfed through athros website but they do now provide drivers for the ubuntu. 

Can anyone tell me by which way i can enable my wifi ? i am using ubuntu 11.04. and in windows my wifi is working very well.


Thanks in advance....

---

### Post by wildmanne39 on 2011-07-26
Hi, run these commands in a terminal please
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

### Post by ankur.trapasiya on 2011-07-26
Hello...!!! Thanks for reply... here is the required information...

```

# siyaram@siyaram-Lenovo-B560:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

``````

# siyaram@siyaram-Lenovo-B560:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
ppp0      no wireless extensions.

``````

# siyaram@siyaram-Lenovo-B560:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

``````

# siyaram@siyaram-Lenovo-B560:~$ lsmod
Module                  Size  Used by
btrfs                 527388  0 
libcrc32c              12543  1 btrfs
ufs                    78583  0 
qnx4                   13317  0 
hfsplus                79383  0 
hfs                    49504  0 
minix                  31481  0 
ntfs                  100098  0 
vfat                   17335  0 
msdos                  17133  0 
fat                    55505  2 vfat,msdos
jfs                   174783  0 
xfs                   735018  0 
exportfs               12870  1 xfs
reiserfs              234405  0 
ppp_deflate            12838  0 
zlib_deflate           26594  2 btrfs,ppp_deflate
bsd_comp               12777  0 
ppp_async              17308  1 
crc_ccitt              12595  1 ppp_async
option                 21045  2 
usb_wwan               19711  1 option
usbserial              37116  7 option,usb_wwan
usb_storage            43946  0 
uas                    17676  0 
rfcomm                 38125  8 
parport_pc             32111  0 
ppdev                  12849  0 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_codec_realtek   255882  1 
btusb                  18160  2 
snd_hda_intel          24140  2 
arc4                   12473  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  450969  8 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ath9k                 103669  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
acer_wmi               23153  0 
drm_kms_helper         40745  1 i915
mac80211              257001  1 ath9k
uvcvideo               66851  0 
drm                   184133  4 i915,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
ath9k_common           13611  1 ath9k
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
psmouse                59039  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
serio_raw              12990  0 
intel_ips              17769  0 
cfg80211              156212  3 ath9k,mac80211,ath
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ideapad_laptop         13262  0 
sparse_keymap          13666  2 acer_wmi,ideapad_laptop
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
atl1c                  36237  0 

```

---

### Post by wildmanne39 on 2011-07-26
Hi, try this in a terminal please.
```
rmmod -f acer-wmi
```
if this works we will need to blacklist it.

Please remove your wired connection before you do this.
Thank you

---

