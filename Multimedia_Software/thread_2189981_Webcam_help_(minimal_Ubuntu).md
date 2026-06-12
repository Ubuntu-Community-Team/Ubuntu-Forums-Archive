---
title: "Webcam help (minimal Ubuntu)"
date: 2013-11-25
forum: Multimedia Software
---

### Post by MibunoOokami on 2013-11-25
Hi all. I can't work out what driver/program to install to make my webcam work in minimal Ubuntu.
I've tried the codes listed below, which I think means mini knows there is a camera and it's perhaps just a matter of getting other programs to detect it?
Edit: Solution in post [#10]("http://ubuntuforums.org/showthread.php?t=2189981&p=12857859#post12857859")

```
ls /dev/video*
/dev/video0
ls /dev/audio*
ls: cannot access /dev/audio*: No such file or directory

```
```
lsmod
Module                  Size  Used by
binfmt_misc            13140  1 
joydev                 17097  0 
snd_hda_codec_idt      44605  1 
coretemp               13195  0 
arc4                   12536  2 
uvcvideo               71309  0 
ath9k                 135969  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
ath9k_common           13619  1 ath9k
ath9k_hw              429197  2 ath9k_common,ath9k
videodev              107508  2 uvcvideo,videobuf2_core
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
microcode              18830  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
mac80211              513247  1 ath9k
ath3k                  13110  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
psmouse                90642  0 
btusb                  23443  0 
bluetooth             323622  3 ath3k,btusb
snd_timer              24447  2 snd_pcm,snd_seq
serio_raw              13189  0 
cfg80211              401436  3 ath,ath9k,mac80211
snd                    60790  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                16864  0 
gma500_gfx            173595  2 
soundcore              12600  1 snd
drm_kms_helper         46867  1 gma500_gfx
drm                   242354  3 drm_kms_helper,gma500_gfx
wmi                    18590  1 hp_wmi
video                  18777  1 gma500_gfx
mac_hid                13037  0 
i2c_algo_bit           13197  1 gma500_gfx
lp                     13299  0 
parport                40795  1 lp
r8169                  61434  0 
ahci                   25579  3 
libahci                26554  1 ahci
mii                    13654  1 r8169


```
```
lsusb
Bus 001 Device 002: ID 04f2:b2a6 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0cf3:311d Atheros Communications, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

This next question is slightly off topic but still related to mini. I would like to know how to get the little battery icon that shows how much juice is left in laptop battery or how long until charged.

---

### Post by Kirboosy on 2013-11-25
The program I use for my webcams is cheese, but there are others out their too. I used minimal install for a while with fluxbox and conky on my netbook.

[ATTACH=CONFIG]248088[/ATTACH]

The line for conky that you would be interested in is as follows

```
 ${color #A548CC}Battery Left:${color} ${battery_time BAT1}
```

Of course you can change it to suit your taste.

Hope that helps!
~Caboose

---

### Post by MibunoOokami on 2013-11-25
Hi Caboose, I tried cheese but it won't/can't find the webcam. Full Ubuntu was able to make the camera work though the video wasn't very good when I had that installed.

---

### Post by papibe on 2013-11-25
Hi MibunoOokami.

If I remember correctly, I had to install this library in order for my USB webcam to work on a server (similar to minimal CD):
```
sudo apt-get install libv4l-0
```
Let us know if that makes a difference.
Regards.

---

### Post by MibunoOokami on 2013-11-25
Hi Papibe, it says I have the newest version ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libv4l-0 is already the newest version.
libv4l-0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Edit: Sorry, my webcam is build in.

---

### Post by papibe on 2013-11-25
Have you tried the preload trick? Take a look at post #6 [here]("http://ubuntuforums.org/showthread.php?t=2166421&highlight=LD_PRELOAD").

Regards.

---

### Post by MibunoOokami on 2013-11-25
I hadn't tried that before, just followed the instructions and rebooted. Unfortunately it didn't work, in cheese preferences the device box is greyed and skype says no device found.

---

### Post by papibe on 2013-11-25
I see.

(note that the preload trick is not permanent, the purpose is to force loading a library before you call the program).

I took a second look at your 1st post and I realized that you actually have both **/dev/video0 **and the **uvcvideo** driver loaded.

Could you post the result of these commands?
```
ls -lR /dev/v4l/

dmesg | grep -i uvc

```
Regards.

---

### Post by MibunoOokami on 2013-11-25
Here are the outputs.

```
 ls -lR /dev/v4l/
/dev/v4l/:
total 0
drwxr-xr-x 2 root root 60 Nov 26 11:29 by-id
drwxr-xr-x 2 root root 60 Nov 26 11:29 by-path

/dev/v4l/by-id:
total 0
lrwxrwxrwx 1 root root 12 Nov 26 11:29 usb-Chicony_Electronics_Co._Ltd._HP_Webcam-50_0x0001-video-index0 -> ../../video0

/dev/v4l/by-path:
total 0
lrwxrwxrwx 1 root root 12 Nov 26 11:29 pci-0000:00:1d.7-usb-0:4:1.0-video-index0 -> ../../video0


```
```
dmesg | grep -i uvc
[    9.210748] uvcvideo: Found UVC 1.00 device HP Webcam-50 (04f2:b2a6)
[    9.219664] usbcore: registered new interface driver uvcvideo
```

Thanks

---

### Post by papibe on 2013-11-25
It looks good.

It may be a permissions problem:
```
ls -l /dev/video0 
crw-rw----+ 1 root video 81, 0 Nov 25 19:23 /dev/video0

```
Add yourself to the video group:
```
sudo usermod -a -G video youruser
```
replace 'youruser' for your actual username.

Let us know how it goes.
Regards.

---

### Post by MibunoOokami on 2013-11-25
Hi Papibe,

That's done the trick thank you.

---

### Post by papibe on 2013-11-25
Great! :D

You may need to do the same for audio (replace 'video' for 'audio' in the previous command).

Glad you sorted it out.

---

### Post by MibunoOokami on 2013-11-25
> **Caboose885 said:**
> I used minimal install for a while with fluxbox and conky on my netbook.

[ATTACH=CONFIG]248088[/ATTACH]

The line for conky that you would be interested in is as follows

```
 ${color #A548CC}Battery Left:${color} ${battery_time BAT1}
```

Hope that helps!
~Caboose

Hi Caboose,

I installed conky, does that line get entered in a file? It doesn't do anything in terminal. For fluxbox, do I uninstall xfce4 and then install fluxbox, or is it at startup instead of typing startxfce4 type something like startfluxbox? Thanks

---

### Post by MibunoOokami on 2013-11-25
> **papibe said:**
> Great! :D

You may need to do the same for audio (replace 'video' for 'audio' in the previous command).

Glad you sorted it out.

Eep, I've got a buzzing sound coming out my speakers now which I can mute and unmute. Any idea what that might be?

---

### Post by Kirboosy on 2013-11-26
You can run conky on whatever desktop environment you choose. Just add conky to your start-up programs. If I remember correctly for XFCE it should be located under the following. Settings --> Session and Startup --> Application Autostart

The line that I listed is stored in your .conkyrc file. (Its stored under your home directory ~/.conkyrc) Here is the full copy of my .conkyrc

```
alignment bottom_right
double_buffer yes
own_window_transparent yes
own_window no
use_xft yes
maximum_width 270
default_color white
uppercase no
update_interval 3

TEXT
            ${color #FFCB48}The-Daemon
 ${color #A548CC}Date:${color}${font size=11} ${time %a %b %e, %G}${font}
 ${color #A548CC}Time:${color}${font size=11} ${time %I:%M:%p}${font}
 ${color #A548CC}Uptime:${color} ${uptime}
 ${color #A548CC}Battery Left:${color} ${battery_time BAT1}
 ${color #A548CC}CPU:${color} ${freq_g}GHz (${cpu}%)
 ${color #A548CC}RAM Usage:${color} $mem/$memmax - $memperc%
 ${color #A548CC}Disk Usage: ${color}${fs_free /} of ${fs_size /}

 ${color #FFCB48}Wi-Fi: ${color #FFCB48} ${wireless_essid wlan0}
 ${color #A548CC}Wireless signal: $color${wireless_link_qual wlan0}%
 ${color #A548CC}IP address: $color${addr wlan0}

 ${if_running mocp}${alignc}${execi 10 mocp -Q '%song\n%artist\n%album'}
 ${execbar mocp -Q '%cs/%ts*100' | bc -l}${endif}
```

Hope that helps!
~Caboose

PS. Please mark the thread as solved! (Under 'Thread Tools' on the top right of the top thread)

---

