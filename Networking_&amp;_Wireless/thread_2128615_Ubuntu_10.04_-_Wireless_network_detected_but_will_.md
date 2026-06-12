---
title: "Ubuntu 10.04 - Wireless network detected but will not connect"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by Eric-A on 2013-03-23
I have an Acer Aspire 5532 laptop with a broadcom b43 wifi and an Atheros ethernet. I can connect to the internet via eth0 but when I try to use the wifi it can see the Centurylink modem/router but will not connect. I installed the required broadcom STA driver, b43 cutter, and it still won't connect via eth1 wifi. I even tried changing the centurylink setup from wpa to wep and it reverts always back to wpa. My wifes Acer Aspire 5532 laptop windows7 connects just fine via wifi and ethernet.

---

### Post by Hadaka on 2013-03-23
Hi ,please COPY and paste
the following 3 commands..
```
lspci -n | grep 0280 | awk '{print$3}'| cut -c6-9
lsmod
fkill list all
```
post back the results..
thanks.

---

### Post by Eric-A on 2013-03-23
Here is the output.
.
eric@Acer-2:~$ lspci -n | grep 0280 | awk '{print$3}'| cut -c6-9
4357
eric@Acer-2:~$ lsmod
Module                  Size  Used by
binfmt_misc             6523  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203472  1 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
radeon                678607  3 
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ttm                    49847  1 radeon
drm_kms_helper         29329  1 radeon
snd_timer              19130  2 snd_pcm,snd_seq
drm                   163779  5 radeon,ttm,drm_kms_helper
lib80211_crypt_tkip     7596  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 radeon
snd                    54244  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1959598  0 
joydev                  8740  0 
led_class               2864  0 
psmouse                63677  0 
shpchp                 28835  0 
video                  17375  0 
soundcore               6620  1 snd
serio_raw               3978  0 
atl1c                  27955  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
k8temp                  3152  0 
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
lp                      7060  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32680  2 
eric@Acer-2:~$ fkill list all
No command 'fkill' found, did you mean:
 Command 'mkill' from package 'mtop' (universe)
 Command 'rfkill' from package 'rfkill' (universe)
 Command 'rfkill' from package 'wireless-tools' (main)
 Command 'rkill' from package 'pslist' (universe)
 Command 'kill' from package 'procps' (main)
 Command 'skill' from package 'procps' (main)
 Command 'xkill' from package 'x11-utils' (main)
 Command 'pkill' from package 'procps' (main)
 Command 'vkill' from package 'util-vserver' (universe)
 Command 'tkill' from package 'lam-runtime' (universe)
fkill: command not found
eric@Acer-2:~$ fkill list
No command 'fkill' found, did you mean:
 Command 'mkill' from package 'mtop' (universe)
 Command 'rfkill' from package 'rfkill' (universe)
 Command 'rfkill' from package 'wireless-tools' (main)
 Command 'rkill' from package 'pslist' (universe)
 Command 'kill' from package 'procps' (main)
 Command 'skill' from package 'procps' (main)
 Command 'xkill' from package 'x11-utils' (main)
 Command 'pkill' from package 'procps' (main)
 Command 'vkill' from package 'util-vserver' (universe)
 Command 'tkill' from package 'lam-runtime' (universe)
fkill: command not found
eric@Acer-2:~$ fkill all
No command 'fkill' found, did you mean:
 Command 'mkill' from package 'mtop' (universe)
 Command 'rfkill' from package 'rfkill' (universe)
 Command 'rfkill' from package 'wireless-tools' (main)
 Command 'rkill' from package 'pslist' (universe)
 Command 'kill' from package 'procps' (main)
 Command 'skill' from package 'procps' (main)
 Command 'xkill' from package 'x11-utils' (main)
 Command 'pkill' from package 'procps' (main)
 Command 'vkill' from package 'util-vserver' (universe)
 Command 'tkill' from package 'lam-runtime' (universe)
fkill: command not found
eric@Acer-2:~$

---

### Post by Hadaka on 2013-03-23
Hi, i made a typo..sorry
it was suppose to be...
```
rfkill list all
```
not fkill list all. It looks like you
have the correct driver loaded,you could
try a reload with it by doing...
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
```
then reinstall with..
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
your release version 10.4 i believe is no longer
supported, so thats pretty much all i have to offer.
other than loading 12.04 lts
good luck.

---

### Post by Eric-A on 2013-03-23
reloading didn't help, and I upgraded to Ubuntu 12.10 and it didn't help either, but thanks, hopefully someone else has a fix

---

