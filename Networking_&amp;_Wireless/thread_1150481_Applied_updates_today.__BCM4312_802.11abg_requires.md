---
title: "Applied updates today.  BCM4312 802.11a/b/g requires driver reinstall every boot."
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-05-06
I have an HP/Compaq 6715b Laptop which contains (according to lspci) Broadcom Corporation BCM4312 802.11a/b/g (rev 02).

I've been using it for the last 2 or three weeks with no issues what so ever.  However, SOME sort of update came down the wire today (I don't know what they were; I have a bad habit of trusting the distro) and now every time I boot Ubuntu I have to use the Hardware Drivers manager to deactivate and then reactivate the drivers in order to use my wireless adapter.  lspci will see the device before I do this, but my network manager acts as if there is no device to use until I go through this little inconvenient routine.

I'm not sure if I've provided enough detailed info about the wireless adapter, as far as hardware identification, but I can't remember the best command to use to determine the "precise" hardware this wireless adapter consists of.  So if there's another command I should enter to help further discovery of a solution, let me know.

Thanks!

---

### Post by diablo75 on 2009-05-06
Bump.

---

### Post by diablo75 on 2009-05-08
Bump.

Attached is what Hardware Drivers looks like every time I boot, before I reactivate my drivers.  What does it say "Driver is activated by not currently in use?"

---

### Post by hajk on 2009-05-08
I take it that you're trying to use the "wl" module. Sometimes the "ssb" module grabs the wireless interface before "wl", which should be avoided. 
Run the command```

$ lsmod |grep ssb
```in a terminal... does it give you any output? If yes, you should add the "ssb" module to the end of the blacklist file in the /etc/modprobe.d directory, then reboot.

---

### Post by superprash2003 on 2009-05-08
i had this problem after a kernal update.. i just selected an old kernel when booting ubuntu ( grub list )

---

### Post by diablo75 on 2009-05-08
> **hajk said:**
> I take it that you're trying to use the "wl" module. Sometimes the "ssb" module grabs the wireless interface before "wl", which should be avoided. 
Run the command```

$ lsmod |grep ssb
```in a terminal... does it give you any output? If yes, you should add the "ssb" module to the end of the blacklist file in the /etc/modprobe.d directory, then reboot.

Unfortunately, lsmod |grep ssb produces no output.  The output for simply "lsmod" is as follows:

```
Module                  Size  Used by
michael_mic            10496  2 
arc4                    9856  2 
ieee80211_crypt_tkip    16896  0 
wl                   1489748  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
isofs                  39844  1 
udf                    87716  0 
crc_itu_t              10112  1 udf
cbc                    11648  397 
aes_i586               15744  398 
aes_generic            35880  1 aes_i586
ecb                    10752  3 
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
pcmcia                 44748  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4              18448  0 
video                  25360  0 
psmouse                61972  0 
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
joydev                 18368  0 
k8temp                 12416  0 
pcspkr                 10496  0 
output                 11008  1 video
shpchp                 40212  0 
serio_raw              13316  0 
leds_hp_disk           10756  0 
led_class              12036  1 leds_hp_disk
btusb                  19608  2 
ppdev                  15620  0 
parport_pc             40100  0 
parport                42220  3 lp,ppdev,parport_pc
tpm_infineon           16936  0 
tpm                    22976  1 tpm_infineon
tpm_bios               14080  1 tpm
lis3lv02d              17848  0 
ndiswrapper           193436  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
david@ubuntu:~$ lsmod|grub ssb
Probing devices to guess BIOS drives. This may take a long time.
david@ubuntu:~$ lsmod|grep ssb
david@ubuntu:~$ lsmod |grep ssb
david@ubuntu:~$ lsmod
Module                  Size  Used by
michael_mic            10496  2 
arc4                    9856  2 
ieee80211_crypt_tkip    16896  0 
wl                   1489748  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
isofs                  39844  1 
udf                    87716  0 
crc_itu_t              10112  1 udf
cbc                    11648  398 
aes_i586               15744  399 
aes_generic            35880  1 aes_i586
ecb                    10752  3 
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
pcmcia                 44748  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4              18448  0 
video                  25360  0 
psmouse                61972  0 
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
joydev                 18368  0 
k8temp                 12416  0 
pcspkr                 10496  0 
output                 11008  1 video
shpchp                 40212  0 
serio_raw              13316  0 
leds_hp_disk           10756  0 
led_class              12036  1 leds_hp_disk
btusb                  19608  2 
ppdev                  15620  0 
parport_pc             40100  0 
parport                42220  3 lp,ppdev,parport_pc
tpm_infineon           16936  0 
tpm                    22976  1 tpm_infineon
tpm_bios               14080  1 tpm
lis3lv02d              17848  0 
ndiswrapper           193436  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
david@ubuntu:~$ clear

david@ubuntu:~$ lsmod
Module                  Size  Used by
michael_mic            10496  2 
arc4                    9856  2 
ieee80211_crypt_tkip    16896  0 
wl                   1489748  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
isofs                  39844  1 
udf                    87716  0 
crc_itu_t              10112  1 udf
cbc                    11648  398 
aes_i586               15744  399 
aes_generic            35880  1 aes_i586
ecb                    10752  3 
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
pcmcia                 44748  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4              18448  0 
video                  25360  0 
psmouse                61972  0 
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
joydev                 18368  0 
k8temp                 12416  0 
pcspkr                 10496  0 
output                 11008  1 video
shpchp                 40212  0 
serio_raw              13316  0 
leds_hp_disk           10756  0 
led_class              12036  1 leds_hp_disk
btusb                  19608  2 
ppdev                  15620  0 
parport_pc             40100  0 
parport                42220  3 lp,ppdev,parport_pc
tpm_infineon           16936  0 
tpm                    22976  1 tpm_infineon
tpm_bios               14080  1 tpm
lis3lv02d              17848  0 
ndiswrapper           193436  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

> **superprash2003 said:**
> i had this problem after a kernal update.. i just selected an old kernel when booting ubuntu ( grub list )

I've seen such things happen before, but unfortunately for me, the update was not a kernel update (or at least there is still only one kernel to select from in grub).

So, I'm still stuck with the same problem...

---

### Post by diablo75 on 2009-05-09
Bump.

---

### Post by diablo75 on 2009-05-19
Bump.

Edit:

I wanted to add that I checked the contents of my /etc/modprobe.d/blacklist-bcm43.conf file, and it shows the following:

```
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
```

So ssb was already there.

---

