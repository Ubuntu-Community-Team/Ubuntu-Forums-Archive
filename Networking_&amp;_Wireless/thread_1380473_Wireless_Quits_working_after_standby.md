---
title: "Wireless Quits working after standby"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by jeh311 on 2010-01-13
i am running 9.10 on a compaq 2209cl laptop. has been working great with no issues till i updated the other day. when i come out of standby (opening laptop lid, or hit the power button to wake up) my network connection does not start, and there is no wireless networks displayed. a reboot usually takes care of this prob until it goes into standby again. just wanna know if there is a way i can solve this myself or if i gotta wait for a patch? it aint too bad but is sure is annoying when i get on and off this thing all the time.

---

### Post by Crafty Kisses on 2010-01-13
It could be a module problem, before the computer goes into standby (when the wireless is working) go into a terminal and run the following:
```
lsmod
```
Then when the computer goes into standby (when the wireless isn't working) go into a terminal and run the same command, then post them here, and we will see if this is a module problem.

---

### Post by jeh311 on 2010-01-13
here is the first one

joey@Joey-Laptop:~$ lsmod
Module                  Size  Used by
ufs                    75524  0 
qnx4                    8576  0 
hfsplus                73632  0 
hfs                    43232  0 
minix                  27588  0 
ntfs                   98240  0 
vfat                   10716  0 
msdos                   7836  0 
fat                    51452  2 vfat,msdos
jfs                   177380  0 
xfs                   512096  0 
exportfs                4412  1 xfs
reiserfs              229288  0 
isofs                  31620  0 
udf                    80900  1 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_intel          26920  0 
snd_hda_codec          75708  1 snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
joydev                 10240  0 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  5 snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
pcmcia                 36808  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
b43                   122168  0 
mac80211              181140  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                56500  0 
serio_raw               5280  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_hda_intel,snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ssb                    35364  1 b43
i915                  221320  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

i will get back to you soon with the other one.

---

### Post by jeh311 on 2010-01-13
and now here is the other one after standby

joey@Joey-Laptop:~$ lsmod
Module                  Size  Used by
ufs                    75524  0 
qnx4                    8576  0 
hfsplus                73632  0 
hfs                    43232  0 
minix                  27588  0 
ntfs                   98240  0 
vfat                   10716  0 
msdos                   7836  0 
fat                    51452  2 vfat,msdos
jfs                   177380  0 
xfs                   512096  0 
exportfs                4412  1 xfs
reiserfs              229288  0 
isofs                  31620  0 
udf                    80900  1 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_intel          26920  0 
snd_hda_codec          75708  1 snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
joydev                 10240  0 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  5 snd_hda_intel,snd_hda_codec,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
pcmcia                 36808  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
b43                   122168  0 
mac80211              181140  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                56500  0 
serio_raw               5280  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_hda_intel,snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ssb                    35364  1 b43
i915                  221320  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

---

### Post by jeh311 on 2010-01-16
anything in there?

---

### Post by Crafty Kisses on 2010-01-17
Hey, I didn't see anything wrong with the modules they look like they are all there and there is no difference between the outputs. When the wireless goes down, try running the following command as root:
```
/etc/init.d/networking restart
```
Then see if that brings your wireless back up.

---

### Post by jeh311 on 2010-01-27
that dont work when i try it i get this in the terminal

joey@Joey-Laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for joey: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
joey@Joey-Laptop:~$ 

sorry for taking so long to reply on this, been very busy lately.

---

### Post by jeh311 on 2010-02-10
no luck yet

---

### Post by jeh311 on 2010-02-13
even goes out when the wireless router is yanked and have to reboot? thats the only thing new i have.

---

### Post by madtom1999 on 2010-02-13
I'm having a similar problem
but when I pop the wireless card out and back in it reconfigure itself and starts working.
Is there a way to kick the pcmcia to do this without popping it in and out?

---

### Post by SecretCode on 2010-02-13
Does the following help? 
Right-click the network manager icon, uncheck 'Enable wireless', then check it again. Wait a few seconds.

If that's no good, try these terminal commands:
```
rfkill list
rfkill unblock wifi
```

---

### Post by jeh311 on 2010-02-24
i tried that with the wireless to enable and disable with no luck, but will try the code as soon as i can.

---

### Post by kerry_s on 2010-02-24
you have to suspend the wifi.

press **alt+f2**
type> **gksudo gedit /etc/pm/config.d/config**
put> **SUSPEND_MODULES="b43"**

now reboot & try it.

---

