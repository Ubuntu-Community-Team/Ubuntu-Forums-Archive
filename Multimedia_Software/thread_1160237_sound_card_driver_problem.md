---
title: "sound card driver problem"
date: 2009-05-15
forum: Multimedia Software
---

### Post by andypearce on 2009-05-15
Hi all,
after extensive screaming and banging my head against the wall I now suspect I have a problem with my sound/graphics card driver. It takes up to six boot ups to get on to my laptop with the sound, flash and dvd player etc working at the right speed. The log in prompt or start tune can be distorted or run at half speed or a note at a time for several goes before the start works normally.
I am using a toshiba laptop satellite pro L100. Someone has previously advised me how to see what hardware I have (ishw.txt is its name) and I think the bit that is relevant is one of the bits that mention ATI and it could be a RC410 radeon xpress 200m.....? I do not know I am guessing but learning all the time! However, this laptop did have the evil microsoft on it previously before I purged it and downloaded ubuntu. Do you think it is a driver problem and if it is how do I fix it.... (warning I am not very computer literate and do not understand a lot of the jargon but am on an exponential learning curve).
Ta for now Andy

---

### Post by harrypottergw on 2009-06-22
yeah, i have the same problem. I have a toshiba nb205... the sound worked when i had xp. PLEASE HELP!

---

### Post by Silent Warrior on 2009-06-23
Now, I'm not particularly Linux-literate myself, but I may be able to suggest a thing or two that'll make trouble-shooting easier:
Try this command and note its output:
lspci | grep Audio (I tested this running Mint 7, actually, so you might need a different filter - you might also want to try 'lspci -v')
Next try:
lsmod (I think there's some sense in running a '| grep' for something here as well, buut I have no clue as to what to filter for)

(You should, of course, post the output of these commands.)

---

### Post by harrypottergw on 2009-06-23
i got this for the first command:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by harrypottergw on 2009-06-23
This is the second command

Module                  Size  Used by
nls_iso8859_1          12032  0 
nls_cp437              13696  0 
vfat                   18816  0 
fat                    58272  1 vfat
usb_storage            99520  0 
snd_cs4236             22924  0 
snd_opl3_lib           18560  1 snd_cs4236
snd_hwdep              15108  1 snd_opl3_lib
snd_cs4236_lib         22656  1 snd_cs4236
snd_wss_lib            33920  2 snd_cs4236,snd_cs4236_lib
snd_mpu401_uart        15104  1 snd_cs4236
i915                   65668  3 
drm                    96296  4 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_cs4236_lib,snd_wss_lib,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               63240  0 
psmouse                61972  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
snd_timer              29704  4 snd_opl3_lib,snd_wss_lib,snd_pcm,snd_seq
snd_seq_device         14988  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13316  0 
pcspkr                 10496  0 
v4l1_compat            21764  2 uvcvideo,videodev
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    62628  21 snd_cs4236,snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_wss_lib,snd_mpu401_uart,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              34108  1 
soundcore              15200  1 snd
agpgart                42696  3 drm,intel_agp
snd_page_alloc         16904  3 snd_wss_lib,snd_hda_intel,snd_pcm
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by Odemia on 2009-06-23
Try starting here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
If you are still having trouble after going through that guide, then post the outputs of aplay, lspci -v, etc here.

---

### Post by andypearce on 2009-11-28
Hi all upgraded to 9.10 and it now works perfectly
Thanks
Andy

---

