---
title: "Actiontec 802AIN Wireless N Adapter"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by CommanderEPH on 2013-03-17
My problem is identical to what is described here: [http://ubuntuforums.org/showthread.php?t=1964872](http://ubuntuforums.org/showthread.php?t=1964872)
I dont' know if anyone has figured this out because the conversation just drops off.

Would like to get this working as I don't have the cash for another adapter. Please halp.

lsusb output:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 001 Device 019: ID 1668:1200 Actiontec Electronics, Inc. [hex] 802AIN Wireless N Network Adapter [Atheros AR9170+AR9101]

```




Modules:
```
Module                  Size  Used by
nls_utf8               12493  1 
hfsplus                83544  1 
nfsd                  229909  11 
lockd                  78865  1 nfsd
nfs_acl                12771  1 nfsd
auth_rpcgss            39597  1 nfsd
sunrpc                205991  12 nfsd,lockd,nfs_acl,auth_rpcgss
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158479  10 bnep,rfcomm
dm_crypt               22528  0 
carl9170               77667  0 
ath9k_htc              90811  0 
ath9k_common           13781  1 ath9k_htc
ath9k_hw              391626  2 ath9k_htc,ath9k_common
ath                    19387  4 carl9170,ath9k_htc,ath9k_common,ath9k_hw
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
zd1211rw               57509  0 
snd_hwdep              13276  1 snd_hda_codec
mac80211              436493  3 carl9170,ath9k_htc,zd1211rw
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
cfg80211              178877  5 carl9170,ath9k_htc,ath,zd1211rw,mac80211
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
mac_hid                13077  0 
ppdev                  12849  0 
parport_pc             32114  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            39646  2 
i915                  423416  3 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
sky2                   49545  0

```



Messages received: These lines actually loop for quite some time on inserting the device
```
[ 1842.985518] usb 1-1: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
[ 1843.984023] ath9k_htc 1-1:1.0: ath9k_htc: Target is unresponsive
[ 1843.993040] ath9k_htc: probe of 1-1:1.0 failed with error -22

```


I am running Ubuntu 12.04.2 LTS
3.2.0-38-generic i686

---

### Post by halhack on 2013-11-13
Here is the output of lsusb
hal@hal-EP43-UD3L:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 004 Device 002: ID 046d:08ae Logitech, Inc. QuickCam for Notebooks
Bus 002 Device 052: ID 1668:1200 Actiontec Electronics, Inc. [hex] 802AIN Wireless N Network Adapter [Atheros AR9170+AR9101]

Shows the device plugged in. Now How/where do I get a driver for it so that it will WPS to my wireless router? I guess I could always go back to Win 7. NOT!

I'm sure someone has solved this. Come on guys, PLEASE help. I'm a newbie. :)

---

