---
title: "Toshiba NB200 Audio Problem"
date: 2010-04-29
forum: Multimedia Software
---

### Post by cemzafer on 2010-04-29
Hi all,

Here is my configuration file and lspci output but sound doesnt work or I cant figure it out. So any idea would be appreciated, thanks.

lspci output

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Here is the lsmod output

Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1660  2 
ecb                     2524  2 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ath9k                 258744  0 
mac80211              181140  1 ath9k
led_class               4096  1 ath9k
ath                     8060  1 ath9k
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
serio_raw               5280  0 
cfg80211               93052  3 ath9k,mac80211,ath
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52768  1 
r8169                  32064  0 
i915                  226120  3 
mii                     5212  1 r8169
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

---

### Post by P4man on 2010-04-29
open a terminal and run

alsamixer

use arrow keys to navigate and up/down key to adjust mixers. M key to mute/unmute. Make sure its not just a muted channel (like PCM).

---

### Post by lidex on 2010-04-29
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by cemzafer on 2010-05-01
Sorry for the late response, here is the output of the commands. Anyway I tried the first post and there are not any mute channels.
Thanks.

cemzafer@ubuntu:~$ uname -a
Linux ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
cemzafer@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
cemzafer@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
cemzafer@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC272

---

### Post by lidex on 2010-05-01
Go here and work through the steps for debugging karmic audio:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Make sure to install the alsa-backports. Report your results here.

---

### Post by cemzafer on 2010-05-02
I executed the following command, ubuntu-bug -p alsa-base
I think thats the command to report the debug.
By the way, headphone output is working just the speaker isnt working.
Thanks

---

### Post by lidex on 2010-05-02
Did you install the alsa-backports? If not, install them and reboot, then check alsamixer. ```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by lidex on 2010-05-02
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-hda-intel model=auto
```
Save. Close. Reboot. Check your levels in alsamixer.
```
alsamixer
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by msknight on 2010-05-02
Wow. NB-200, Lucid Netbook Remix - that worked a treat for me. Many thanks!

---

### Post by cemzafer on 2010-05-04
Thanks, it is working now.

---

### Post by hatalar205 on 2010-05-04
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-hda-intel model=auto
```
Save. Close. Reboot. Check your levels in alsamixer.
```
alsamixer
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

Thanks it is working now. I have been looking for this for a while.

---

### Post by nolster12 on 2010-05-04
Brilliant this worked no problem.  Added the one line to the config file rebooted and then turned up the volume!!!  Time to look into Plymouth to make things perfect.

---

### Post by ATJ on 2010-05-04
The installation of alsa-backports worked great for me as well :)

---

### Post by micheut on 2010-05-10
This just worked perfectly fine for me!
Don't know what this think did, but my speakers work better than ever. Tried the OpenOS method, installed Jolicloud but now my speakers are way more loud! Perfect!
Thanks a million.

---

### Post by lidex on 2010-05-11
> **cemzafer said:**
> Thanks, it is working now.

Great. It would help others with the same issue if you marked the thread as solved. Thanks.

---

### Post by filxy on 2011-09-28
i also have toshiba NB200 and the speaker is not working headphone's are working but the voice is not clear it sounds like the the voice is hanging when i use rynga or skype and built in mic of the laptop does work but if i use a mic of a microphone it does not works please help me out with this problem

---

