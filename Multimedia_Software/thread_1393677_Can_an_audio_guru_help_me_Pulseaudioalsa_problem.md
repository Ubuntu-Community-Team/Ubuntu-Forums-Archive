---
title: "Can an audio guru help me? Pulseaudio/alsa problem"
date: 2010-01-29
forum: Multimedia Software
---

### Post by Phases on 2010-01-29
I've been having a number of issues with my audio since I upgraded to 9.10 (well, had some before too, 8.04). (fresh install)

-When I log in it skips and stutters
-I'll regularly lose Skype or VLC sound and have to log out/in to fix 
-When I'm recording a podcast (or maybe even just talking) on Skype and both of us talk at once it won't overlap them, it'll make us sound skippy...

I don't know if any amount of fixing will fix all or just some but anything will help. 

I upgraded pulseaudio to:

```
phases@phases78w1:~$ pulseaudio --version
pulseaudio 0.9.21

```

by following the first bit of [this]("http://ubuntuguide.net/make-sound-quality-better-in-ubuntu-9-10karmic-with-pulseaudio-equalizer").

and upgraded alsa to:
```

phases@phases78w1:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Jan 28 2010 for kernel 2.6.31-17-generic (SMP).
```

by following (after several failed tutorials.. this was great!) [this]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/").

..but still the problems persist. 

When I log in, I get this in my log file:

```
Jan 29 15:19:15 phases78w1 pulseaudio[12197]: module-alsa-card.c: Failed to find a working profile.
Jan 29 15:19:15 phases78w1 pulseaudio[12197]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
```

I also get an error msg when opening Gnome Alsa Mixer:

```
An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly.

Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash '/'
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash '/'

```

I don't know what the deal is but..any advice would be appreciated! 

p.s. Here is my mobo: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131540](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131540) I tried a sound card from Best Buy that was horrible, and after research, I don't think I can find locally a card that will be supported, I'll have to order - if that's my solution.

---

### Post by sports.car.guy on 2010-01-29
> **Phases said:**
> I've been having a number of issues with my audio since I upgraded to 9.10 (well, had some before too, 8.04). 

-When I log in it skips and stutters
-I'll regularly lose Skype or VLC sound and have to log out/in to fix 
-When I'm recording a podcast (or maybe even just talking) on Skype and both of us talk at once it won't overlap them, it'll make us sound skippy...

I don't know if any amount of fixing will fix all or just some but anything will help. 

I upgraded pulseaudio to:

```
phases@phases78w1:~$ pulseaudio --version
pulseaudio 0.9.21

```by following the first bit of [this]("http://ubuntuguide.net/make-sound-quality-better-in-ubuntu-9-10karmic-with-pulseaudio-equalizer").

and upgraded alsa to:
```

phases@phases78w1:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Jan 28 2010 for kernel 2.6.31-17-generic (SMP).
```by following (after several failed tutorials.. this was great!) [this]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/").

..but still the problems persist. 

When I log in, I get this in my log file:

```
Jan 29 15:19:15 phases78w1 pulseaudio[12197]: module-alsa-card.c: Failed to find a working profile.
Jan 29 15:19:15 phases78w1 pulseaudio[12197]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
```I also get an error msg when opening Gnoma Alsa Mixer:

```
An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly.

Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash '/'
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash '/'

```Any advice would be appreciated!


Was your moving from 8.04 an actual upgrade where the package manager updated or you wiped out the install you had in favor of a fresh one. If you did an upgrade I am betting somewhere, which I am clueless as to where it could be, there is some conflicting file or files making it happen. When 8.04 came out PulseAudio and it had a lot of issues.

---

### Post by Phases on 2010-01-29
> **sports.car.guy said:**
> Was your moving from 8.04 an actual upgrade where the package manager updated or you wiped out the install you had in favor of a fresh one. If you did an upgrade I am betting somewhere, which I am clueless as to where it could be, there is some conflicting file or files making it happen. When 8.04 came out PulseAudio and it had a lot of issues.

Thanks for the reply, it was a fresh install.. total wipe.

---

### Post by lidex on 2010-01-29
For that second error you could try removing gnome-alsamixer in synaptic or a terminal:
```
sudo apt-get remove gnome-alsamixer
```
then delete this directory using nautilus:
```
~/.gconf/apps/gnome-alsamixer
```
now re-install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by lidex on 2010-01-29
Can you post the output of these commands please:
```
head -n 1 /proc/asound/card0/codec*
```
```
gedit /etc/modprobe.d/alsa-base.conf
```
```
lspci | grep Audio
```
```
lsmod | grep snd*
```
```
aplay -l
```

---

### Post by sports.car.guy on 2010-01-29
Have you tried bypassing PulseAudio and sending the output directly to the hardware?

Set whatever you choose to use for audio playback to Alsa, then choose a specific device. 

You can get these from doing an aplay -L

Like VLC has a drop down with the default ones it detects from the system. Choose one of them and see how the sound is. If it is problem free, it is most likely something to do with PulseAudio alone. If it does the same thing that it has been it could be a driver or hardware issue besides the possibility of Pulse Audio.

---

### Post by Phases on 2010-01-30
Whoa, I did not know all these replies came in! Sorry! I read the email from the first but guess since I didn't actually come here to read it, it didn't tell me about all the rest!

Thanks for the responses guys. Ok here we go. 

> **lidex said:**
> For that second error you could try removing gnome-alsamixer in synaptic or a terminal:
```
..removed code to shorten.
```

^^ Just tried it, no change. 

> **lidex said:**
> Can you post the output of these commands please:
```
removed codes to shorten..
```

```
phases@phases78w1:~$ head -n 1 /proc/asound/card0/codec*
head: error reading `/proc/asound/card0/codec97#0': Is a directory
```

```

phases@phases78w1:~$ pico /etc/modprobe.d/alsa-base.conf 

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /s$
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-$
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-$
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist $
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist $
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist $

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-$
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

```
phases@phases78w1:~$ lspci | grep Audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
```

```
phases@phases78w1:~$ lsmod | grep snd*
snd_wavefront          38964  0 
snd_cs4236             28628  0 
snd_wss_lib            24380  2 snd_wavefront,snd_cs4236
snd_opl3_lib           10684  2 snd_wavefront,snd_cs4236
snd_hwdep               7392  2 snd_wavefront,snd_opl3_lib
snd_mpu401              6504  1 
snd_mpu401_uart         7196  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_intel8x0           30104  3 
snd_ac97_codec        101536  1 snd_intel8x0
ac97_bus                1596  1 snd_ac97_codec
snd_seq_dummy           2752  0 
snd_pcm_oss            37472  0 
snd_seq_oss            29216  0 
snd_mixer_oss          16220  1 snd_pcm_oss
snd_seq_midi            6656  0 
snd_pcm                76480  5 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            22336  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7036  2 snd_seq_oss,snd_seq_midi
snd_page_alloc          9124  3 snd_wss_lib,snd_intel8x0,snd_pcm
snd_seq                50896  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21540  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          7208  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    61188  27 snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_seq_dummy,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_seq_midi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
```

```
phases@phases78w1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


> **sports.car.guy said:**
> Have you tried bypassing PulseAudio and sending the output directly to the hardware?

Set whatever you choose to use for audio playback to Alsa, then choose a specific device. 

You can get these from doing an aplay -L

Like VLC has a drop down with the default ones it detects from the system. Choose one of them and see how the sound is. If it is problem free, it is most likely something to do with PulseAudio alone. If it does the same thing that it has been it could be a driver or hardware issue besides the possibility of Pulse Audio.

Well the prob is, its sporadic. It works sometimes then just stops working sometimes..  But I just dropped that drop down to alsa and will see..

---

### Post by lidex on 2010-01-31
Try this one:
```
head -n 1 /proc/asound/card0/codec97#0/codec*
```

---

### Post by lidex on 2010-01-31
OK. Right-click on this link and save to desktop:
[http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")
Open a terminal and:
```
cd ~/Desktop
sudo bash utils_alsa-info.sh
```

You can choose what to do with the results. If you save it locally, upload it here as a text file attachment.

More than you want to know here:
[http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")
[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems")
[http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA]("http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA")
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

From what I can see your card should be using the "snd_intel8x0" alsa driver.

---

### Post by Phases on 2010-01-31
```
phases@phases78w1:~$ head -n 1 /proc/asound/card0/codec97#0/codec*
head: cannot open `/proc/asound/card0/codec97#0/codec*' for reading: No such file or directory
```

```
phases@phases78w1:~$ sudo updatedb
[sudo] password for phases: 
phases@phases78w1:~$ locate codec | cat > /home/phases/Desktop/locatecodec

locatecodec:

/etc/alternatives/gstreamer-codec-install
/home/phases/Desktop/backup/workstation/home/phases/.local/share/Trash/files/stuff/Take home/ASL/klcodec345s.exe
/lib/modules/2.6.31-14-generic/kernel/drivers/media/video/zoran/videocodec.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.31-14-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-twl4030.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/media/video/zoran/videocodec.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.31-17-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-17-generic/kernel/sound/soc/codecs
/lib/modules/2.6.31-17-generic/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/usr/bin/gnome-codec-install
/usr/bin/gstreamer-codec-install
/usr/include/c++/4.4/bits/codecvt.h
/usr/include/c++/4.4/ext/codecvt_specializations.h
/usr/include/sound/ac97_codec.h
/usr/include/sound/ak4531_codec.h
/usr/lib/libavcodec.so.52
/usr/lib/libavcodec.so.52.20.0
/usr/lib/i686/cmov/libavcodec.so.52
/usr/lib/i686/cmov/libavcodec.so.52.20.0
/usr/lib/pymodules/python2.6/papyon/media/codec.py
/usr/lib/pymodules/python2.6/papyon/media/codec.pyc
/usr/lib/python2.6/codecs.py
/usr/lib/python2.6/codecs.pyc
/usr/lib/python2.6/encodings/base64_codec.py
/usr/lib/python2.6/encodings/base64_codec.pyc
/usr/lib/python2.6/encodings/bz2_codec.py
/usr/lib/python2.6/encodings/bz2_codec.pyc
/usr/lib/python2.6/encodings/hex_codec.py
/usr/lib/python2.6/encodings/hex_codec.pyc
/usr/lib/python2.6/encodings/quopri_codec.py
/usr/lib/python2.6/encodings/quopri_codec.pyc
/usr/lib/python2.6/encodings/uu_codec.py
/usr/lib/python2.6/encodings/uu_codec.pyc
/usr/lib/python2.6/encodings/zlib_codec.py
/usr/lib/python2.6/encodings/zlib_codec.pyc
/usr/lib/python2.6/lib-dynload/_codecs_cn.so
/usr/lib/python2.6/lib-dynload/_codecs_hk.so
/usr/lib/python2.6/lib-dynload/_codecs_iso2022.so
/usr/lib/python2.6/lib-dynload/_codecs_jp.so
/usr/lib/python2.6/lib-dynload/_codecs_kr.so
/usr/lib/python2.6/lib-dynload/_codecs_tw.so
/usr/lib/python2.6/lib-dynload/_multibytecodec.so
/usr/lib/qt4/plugins/codecs
/usr/lib/qt4/plugins/codecs/libqcncodecs.so
/usr/lib/qt4/plugins/codecs/libqjpcodecs.so
/usr/lib/qt4/plugins/codecs/libqkrcodecs.so
/usr/lib/qt4/plugins/codecs/libqtwcodecs.so
/usr/lib/totem/plugins/bbc/installablecodecs.py
/usr/lib/totem/plugins/bbc/installablecodecs.pyc
/usr/lib/vlc/codec
/usr/lib/vlc/codec/liba52_plugin.so
/usr/lib/vlc/codec/libadpcm_plugin.so
/usr/lib/vlc/codec/libaes3_plugin.so
/usr/lib/vlc/codec/libaraw_plugin.so
/usr/lib/vlc/codec/libavcodec_plugin.so
/usr/lib/vlc/codec/libcc_plugin.so
/usr/lib/vlc/codec/libcdg_plugin.so
/usr/lib/vlc/codec/libcmml_plugin.so
/usr/lib/vlc/codec/libcvdsub_plugin.so
/usr/lib/vlc/codec/libdts_plugin.so
/usr/lib/vlc/codec/libdvbsub_plugin.so
/usr/lib/vlc/codec/libfaad_plugin.so
/usr/lib/vlc/codec/libfake_plugin.so
/usr/lib/vlc/codec/libflac_plugin.so
/usr/lib/vlc/codec/libinvmem_plugin.so
/usr/lib/vlc/codec/liblibass_plugin.so
/usr/lib/vlc/codec/liblibmpeg2_plugin.so
/usr/lib/vlc/codec/liblpcm_plugin.so
/usr/lib/vlc/codec/libmpeg_audio_plugin.so
/usr/lib/vlc/codec/libpng_plugin.so
/usr/lib/vlc/codec/librawvideo_plugin.so
/usr/lib/vlc/codec/libschroedinger_plugin.so
/usr/lib/vlc/codec/libsdl_image_plugin.so
/usr/lib/vlc/codec/libspeex_plugin.so
/usr/lib/vlc/codec/libspudec_plugin.so
/usr/lib/vlc/codec/libsubsdec_plugin.so
/usr/lib/vlc/codec/libsubsusf_plugin.so
/usr/lib/vlc/codec/libsvcdsub_plugin.so
/usr/lib/vlc/codec/libt140_plugin.so
/usr/lib/vlc/codec/libtelx_plugin.so
/usr/lib/vlc/codec/libtheora_plugin.so
/usr/lib/vlc/codec/libtwolame_plugin.so
/usr/lib/vlc/codec/libvorbis_plugin.so
/usr/lib/vlc/codec/libx264_plugin.so
/usr/share/dblatex/lib/dbtexmf/dblatex/texcodec.py
/usr/share/dblatex/lib/dbtexmf/dblatex/texcodec.pyc
/usr/share/dblatex/lib/dbtexmf/dblatex/xetex/codec.py
/usr/share/dblatex/lib/dbtexmf/dblatex/xetex/codec.pyc
/usr/share/doc/gnome-codec-install
/usr/share/doc/libavcodec52
/usr/share/doc/alsa-base/driver/hda_codec.txt.gz
/usr/share/doc/gnome-codec-install/AUTHORS
/usr/share/doc/gnome-codec-install/README
/usr/share/doc/gnome-codec-install/TODO
/usr/share/doc/gnome-codec-install/changelog.gz
/usr/share/doc/gnome-codec-install/copyright
/usr/share/doc/libavcodec52/CREDITS
/usr/share/doc/libavcodec52/MAINTAINERS.gz
/usr/share/doc/libavcodec52/README.Debian.gz
/usr/share/doc/libavcodec52/TODO
/usr/share/doc/libavcodec52/changelog.Debian.gz
/usr/share/doc/libavcodec52/changelog.gz
/usr/share/doc/libavcodec52/copyright
/usr/share/doc/libavcodec52/formats.txt.gz
/usr/share/empathy/codec-preferences
/usr/share/icons/hicolor/16x16/apps/gnome-codec-install.png
/usr/share/icons/hicolor/22x22/apps/gnome-codec-install.png
/usr/share/icons/hicolor/24x24/apps/gnome-codec-install.png
/usr/share/icons/hicolor/scalable/apps/gnome-codec-install.svg
/usr/share/lintian/overrides/libavcodec52
/usr/share/pyshared/papyon/media/codec.py
/usr/share/pyshared-data/gnome-codec-install
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-ac97-codec.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-analog.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-atihdmi.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-ca0110.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-cirrus.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-cmedia.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-conexant.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-idt.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-intelhdmi.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-nvhdmi.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-realtek.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-si3054.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec-via.mod
/usr/src/alsa/alsa-driver-1.0.22.1/.tmp_versions/snd-hda-codec.mod
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/Documentation/hda_codec.txt
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/Documentation/soc/codec.txt
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/aoa/codecs
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/aoa/codecs/Kconfig
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/aoa/codecs/Makefile
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/aoa/codecs/onyx.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/aoa/codecs/onyx.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/aoa/codecs/tas-basstreble.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/aoa/codecs/tas-gain-table.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/aoa/codecs/tas.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/aoa/codecs/tas.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/aoa/codecs/toonie.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/include/ac97_codec.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/include/ak4531_codec.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/pci/ak4531_codec.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/pci/ac97/ac97_codec.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/pci/hda/hda_codec.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/pci/hda/hda_codec.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/Kconfig
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/Makefile
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ac97.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ac97.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ad1836.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ad1836.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ad1938.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ad1938.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ad1980.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ad1980.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ad73311.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ad73311.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ads117x.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ads117x.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ak4104.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ak4104.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ak4535.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ak4535.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ak4642.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ak4642.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ak4671.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ak4671.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/cs4270.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/cs4270.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/cx20442.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/cx20442.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/da7210.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/da7210.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/l3.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/max9877.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/max9877.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/pcm3008.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/pcm3008.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/spdif_transciever.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/spdif_transciever.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ssm2602.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/ssm2602.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/stac9766.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/stac9766.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/tlv320aic23.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/tlv320aic23.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/tlv320aic26.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/tlv320aic26.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/tlv320aic3x.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/tlv320aic3x.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/tlv320dac33.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/tlv320dac33.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/tpa6130a2.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/tpa6130a2.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/twl4030.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/twl4030.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/uda134x.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/uda134x.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/uda1380.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/uda1380.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8350.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8350.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8400.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8400.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8510.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8510.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8523.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8523.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8580.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8580.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8711.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8711.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8727.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8727.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8728.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8728.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8731.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8731.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8750.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8750.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8753.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8753.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8776.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8776.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8900.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8900.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8903.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8903.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8904.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8904.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8940.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8940.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8955.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8955.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8960.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8960.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8961.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8961.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8971.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8971.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8974.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8974.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8988.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8988.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8990.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8990.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8993.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm8993.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm9081.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm9081.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm9705.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm9705.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm9712.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm9712.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm9713.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm9713.h
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm_hubs.c
/usr/src/alsa/alsa-driver-1.0.22.1/alsa-kernel/soc/codecs/wm_hubs.h
/usr/src/alsa/alsa-driver-1.0.22.1/aoa/codecs
/usr/src/alsa/alsa-driver-1.0.22.1/aoa/codecs/Makefile
/usr/src/alsa/alsa-driver-1.0.22.1/aoa/codecs/onyx.c
/usr/src/alsa/alsa-driver-1.0.22.1/aoa/codecs/onyx_old_i2c.c
/usr/src/alsa/alsa-driver-1.0.22.1/aoa/codecs/tas.c
/usr/src/alsa/alsa-driver-1.0.22.1/aoa/codecs/tas_old_i2c.c
/usr/src/alsa/alsa-driver-1.0.22.1/aoa/codecs/toonie.c
/usr/src/alsa/alsa-driver-1.0.22.1/include/sound/ac97_codec.h
/usr/src/alsa/alsa-driver-1.0.22.1/include/sound/ac97_codec.patch
/usr/src/alsa/alsa-driver-1.0.22.1/include/sound/ak4531_codec.h
/usr/src/alsa/alsa-driver-1.0.22.1/isa/sb/sb16_csp_codecs.h
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-ac97-codec.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-analog.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-atihdmi.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-ca0110.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-cirrus.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-cmedia.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-conexant.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-idt.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-intelhdmi.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-nvhdmi.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-realtek.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-si3054.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec-via.ko
/usr/src/alsa/alsa-driver-1.0.22.1/modules/snd-hda-codec.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/.ak4531_codec.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ak4531_codec.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ak4531_codec.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/.ac97_codec.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/.snd-ac97-codec.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/.snd-ac97-codec.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/.snd-ac97-codec.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/ac97_codec.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/ac97_codec.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/ac97_codec.patch
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/snd-ac97-codec.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/snd-ac97-codec.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/snd-ac97-codec.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/ac97/snd-ac97-codec.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.hda_codec.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-analog.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-analog.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-analog.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-atihdmi.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-atihdmi.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-atihdmi.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-ca0110.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-ca0110.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-ca0110.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-cirrus.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-cirrus.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-cirrus.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-cmedia.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-cmedia.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-cmedia.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-conexant.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-conexant.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-conexant.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-idt.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-idt.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-idt.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-intelhdmi.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-intelhdmi.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-intelhdmi.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-nvhdmi.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-nvhdmi.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-nvhdmi.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-realtek.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-realtek.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-realtek.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-si3054.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-si3054.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-si3054.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-via.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-via.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec-via.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/.snd-hda-codec.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/hda_codec.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/hda_codec.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-analog.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-analog.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-analog.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-analog.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-atihdmi.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-atihdmi.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-atihdmi.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-atihdmi.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-ca0110.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-ca0110.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-ca0110.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-ca0110.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-cirrus.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-cirrus.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-cirrus.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-cirrus.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-cmedia.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-cmedia.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-cmedia.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-cmedia.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-conexant.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-conexant.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-conexant.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-conexant.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-idt.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-idt.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-idt.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-idt.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-intelhdmi.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-intelhdmi.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-intelhdmi.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-intelhdmi.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-nvhdmi.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-nvhdmi.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-nvhdmi.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-nvhdmi.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-realtek.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-realtek.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-realtek.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-realtek.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-si3054.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-si3054.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-si3054.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-si3054.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-via.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-via.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-via.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec-via.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec.ko
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/pci/hda/snd-hda-codec.o
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/.snd-soc-wm-hubs.ko.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/.snd-soc-wm-hubs.mod.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/.snd-soc-wm-hubs.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/.wm_hubs.o.cmd
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/Makefile
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/ac97.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/ad1836.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/ad1938.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/ad1980.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/ad73311.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/ak4104.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/ak4535.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/cs4270.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/cx20442.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/l3.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/max9877.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/modules.order
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/pcm3008.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/snd-soc-wm-hubs.ko
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/snd-soc-wm-hubs.mod.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/snd-soc-wm-hubs.mod.o
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/snd-soc-wm-hubs.o
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/spdif_transciever.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/ssm2602.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/stac9766.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/tlv320aic23.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/tlv320aic26.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/tlv320aic3x.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/twl4030.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/uda134x.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/uda1380.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8350.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8400.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8510.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8523.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8580.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8728.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8731.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8750.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8753.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8776.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8900.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8903.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8940.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8960.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8961.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8971.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8974.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8988.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8990.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm8993.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm9081.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm9705.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm9712.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm9713.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm_hubs.c
/usr/src/alsa/alsa-driver-1.0.22.1/soc/codecs/wm_hubs.o
/usr/src/linux-headers-2.6.31-14/include/linux/ac97_codec.h
/usr/src/linux-headers-2.6.31-14/include/sound/ac97_codec.h
/usr/src/linux-headers-2.6.31-14/include/sound/ak4531_codec.h
/usr/src/linux-headers-2.6.31-14/scripts/decodecode
/usr/src/linux-headers-2.6.31-14/sound/aoa/codecs
/usr/src/linux-headers-2.6.31-14/sound/aoa/codecs/Kconfig
/usr/src/linux-headers-2.6.31-14/sound/aoa/codecs/Makefile
/usr/src/linux-headers-2.6.31-14/sound/soc/codecs
/usr/src/linux-headers-2.6.31-14/sound/soc/codecs/Kconfig
/usr/src/linux-headers-2.6.31-14/sound/soc/codecs/Makefile
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/ac97/codec.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/analog.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/atihdmi.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/ca0110.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/cmedia.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/conexant.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/intelhdmi.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/nvhdmi.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/realtek.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/si3054.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/sigmatel.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/hda/codec/via.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/soc/all/codecs.h
/usr/src/linux-headers-2.6.31-14-generic/include/linux/ac97_codec.h
/usr/src/linux-headers-2.6.31-14-generic/scripts/decodecode
/usr/src/linux-headers-2.6.31-17/include/linux/ac97_codec.h
/usr/src/linux-headers-2.6.31-17/include/sound/ac97_codec.h
/usr/src/linux-headers-2.6.31-17/include/sound/ak4531_codec.h
/usr/src/linux-headers-2.6.31-17/scripts/decodecode
/usr/src/linux-headers-2.6.31-17/sound/aoa/codecs
/usr/src/linux-headers-2.6.31-17/sound/aoa/codecs/Kconfig
/usr/src/linux-headers-2.6.31-17/sound/aoa/codecs/Makefile
/usr/src/linux-headers-2.6.31-17/sound/soc/codecs
/usr/src/linux-headers-2.6.31-17/sound/soc/codecs/Kconfig
/usr/src/linux-headers-2.6.31-17/sound/soc/codecs/Makefile
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/ac97/codec.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/analog.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/atihdmi.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/ca0110.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/cmedia.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/conexant.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/intelhdmi.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/nvhdmi.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/realtek.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/si3054.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/sigmatel.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/hda/codec/via.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/snd/soc/all/codecs.h
/usr/src/linux-headers-2.6.31-17-generic/include/linux/ac97_codec.h
/usr/src/linux-headers-2.6.31-17-generic/scripts/decodecode
/var/cache/apt/archives/libavcodec52_4%3a0.5+svn20090706-2ubuntu2_i386.deb
/var/lib/dpkg/alternatives/gstreamer-codec-install
/var/lib/dpkg/info/gnome-codec-install.list
/var/lib/dpkg/info/gnome-codec-install.md5sums
/var/lib/dpkg/info/gnome-codec-install.postinst
/var/lib/dpkg/info/gnome-codec-install.preinst
/var/lib/dpkg/info/gnome-codec-install.prerm
/var/lib/dpkg/info/libavcodec52.list
/var/lib/dpkg/info/libavcodec52.md5sums
/var/lib/dpkg/info/libavcodec52.postinst
/var/lib/dpkg/info/libavcodec52.postrm
/var/lib/dpkg/info/libavcodec52.shlibs
```

```
Output of script:

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Sun Jan 31 07:50:04 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.31-17-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.22.1
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_intel8x0
snd_mpu401


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 22
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10


!!PCI Soundcards installed in the system
!!--------------------------------------

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:04.0 0401: 10de:0059 (rev a2)
	Subsystem: 1043:812a


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10 power_save_controller=N


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : <NULL>
	buggy_irq : Y
	buggy_semaphore : N
	enable : N
	id : <NULL>
	index : -1
	joystick : 0
	spdif_aclink : 0
	xbox : N

!!Module: snd_mpu401
	enable : Y,N,N,N,N,N,N,N
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -2,-2,-2,-2,-2,-2,-2,-2
	irq : 10,65535,65535,65535,65535,65535,65535,65535
	pnp : Y,Y,Y,Y,Y,Y,Y,Y
	port : 816,1,1,1,1,1,1,1
	uart_enter : Y,Y,Y,Y,Y,Y,Y,Y


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Realtek ALC850 rev 0

PCI Subsys Vendor: 0x1043
PCI Subsys Device: 0x812a

Flags: 80020
Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0xffff
Subsys. ID       : 0xffff

Capabilities     :
DAC resolution   : 16-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         : +20dB [+20dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Double rate slots: 7/8
Extended ID      : codec=0 rev=2 LDAC SDAC CDAC DSA=0 SPDIF DRA
Extended status  : SPCV LDAC SDAC CDAC SPDIF=3/4 SPDIF
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=48kHz

0:00 = 0000
0:02 = 0000
0:04 = 0000
0:06 = 0018
0:08 = 0000
0:0a = 801e
0:0c = 0015
0:0e = 0054
0:10 = 1f1f
0:12 = 0808
0:14 = 0000
0:16 = 1515
0:18 = 0808
0:1a = 0000
0:1c = 0808
0:1e = 0000
0:20 = 0400
0:22 = 0000
0:24 = 0000
0:26 = 800f
0:28 = 09c6
0:2a = 05c4
0:2c = bb80
0:2e = bb80
0:30 = bb80
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2824
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0808
0:66 = 0808
0:68 = 0a0a
0:6a = 8000
0:6c = 0000
0:6e = 0017
0:70 = c5a0
0:72 = 00c0
0:74 = 8388
0:76 = 0a90
0:78 = 148e
0:7a = 20d2
0:7c = 414c
0:7e = 4790
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 Jan 28 17:47 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 32 Jan 28 17:47 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 40 Jan 28 17:47 /dev/snd/midiC1D0
crw-rw----+ 1 root audio 116, 24 Jan 30 16:01 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 Jan 31 01:49 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 25 Jan 28 17:47 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116, 18 Jan 28 22:19 /dev/snd/pcmC0D2p
crw-rw----+ 1 root audio 116,  1 Jan 28 17:47 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 28 17:47 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan 28 17:47 .
drwxr-xr-x 3 root root 240 Jan 28 17:47 ..
lrwxrwxrwx 1 root root  12 Jan 28 17:47 pci-0000:00:04.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 1: Intel ICH - MIC ADC [NVidia CK804 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [CK804]

Card hw:0 'CK804'/'NVidia CK804 with ALC850 at irq 22'
  Mixer name	: 'Realtek ALC850 rev 0'
  Components	: 'AC97a:414c4790'
  Controls      : 42
  Simple ctrls  : 27
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 7 [23%] [-36.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [on] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 11 [35%] [-18.00dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Front Input',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 10 [32%] [-19.50dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'Analog In' 'IEC958 In'
  Item0: 'PCM'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 10 [32%] [-19.50dB] [on] Capture [off]
  Front Right: Playback 10 [32%] [-19.50dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 8 [53%] [12.00dB] [on]
  Front Right: Capture 8 [53%] [12.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch' '8ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

!!-------Mixer controls for card 1 [UART]

Card hw:1 'UART'/'MPU-401 UART at 0x330, irq 10'
  Mixer name	: ''
  Components	: ''
  Controls      : 0
  Simple ctrls  : 0


!!Alsactl output
!!-------------

--startcollapse--
state.CK804 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 31
		value.1 31
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 31
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 31
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 31
		value.1 31
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 7
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Beep Playback Switch'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'Beep Playback Volume'
		value 0
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value true
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Phone Playback Volume'
		value 10
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value true
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value 11
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost (+20dB)'
		value true
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Playback Switch'
		value true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD Playback Switch'
		value true
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 23
		value.1 23
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Aux Playback Switch'
		value true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 10
		value.1 10
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value true
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 23
		value.1 23
	}
	control.26 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Mic
		value.1 Mic
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
	control.28 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 8
		value.1 8
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.30 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.31 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.32 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.33 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.35 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		iface MIXER
		name 'IEC958 Playback AC97-SPSA'
		value 0
	}
	control.36 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Duplicate Front'
		value false
	}
	control.37 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Front Input Switch'
		value true
	}
	control.38 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Shared
		comment.item.1 Independent
		iface MIXER
		name 'Surround Jack Mode'
		value Shared
	}
	control.39 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '2ch'
		comment.item.1 '4ch'
		comment.item.2 '6ch'
		comment.item.3 '8ch'
		iface MIXER
		name 'Channel Mode'
		value '2ch'
	}
	control.40 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
	}
	control.41 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 PCM
		comment.item.1 'Analog In'
		comment.item.2 'IEC958 In'
		iface MIXER
		name 'IEC958 Playback Source'
		value PCM
	}
	control.42 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value false
	}
}
state.UART {
	control {
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
snd_wavefront
snd_cs4236
snd_wss_lib
snd_opl3_lib
snd_hwdep
snd_mpu401
snd_mpu401_uart
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_seq_dummy
snd_pcm_oss
snd_seq_oss
snd_mixer_oss
iptable_filter
snd_seq_midi
snd_pcm
ns558
snd_rawmidi
snd_seq_midi_event
ip_tables
snd_page_alloc
x_tables
gameport
lp
snd_seq
nvidia
ppdev
i2c_nforce2
asus_atk0110
parport_pc
agpgart
snd_timer
snd_seq_device
snd
soundcore
parport
k8temp
usbhid
usb_storage
skge
floppy
ohci1394
ieee1394
forcedeth


!!ALSA/HDA dmesg
!!------------------

```

Thanks for the replies. Interesting script!! I will check out those links you posted, let me know of any of this^^ helps.

---

### Post by lidex on 2010-01-31
It appears that the correct  alsa module is being loaded, although not in the location I would expect to see it. Since you do have audio I would suggest commenting out this line in /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel power_save=10 power_save_controller=N
```
Just put a "#" in front of it. You'll need to reboot to see any changes.
VLC, I noted, doesn't have an option to select PA output but you might try selecting ALSA in Tools/Preferences/Audio/Output. For Skype have a look here:
[http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")

---

### Post by Thomas Garman on 2010-01-31
I reinstalled 9.04 for no other reason than 9.10 never worked very well with audio for me.  Now that I have gone back to 9.04 even LMMS works the way it is supposed to.  In 9.10 it literally crashed the system every time I tried to use it and made me feel like I was using Windows all over again.

I don't know if I will ever "upgrade" from 9.04 again.

So, I ask... is there something specific that 9.10 is giving you that you feel like 9.04 doesn't make available?

---

### Post by sports.car.guy on 2010-01-31
> **Thomas Garman said:**
> I reinstalled 9.04 for no other reason than 9.10 never worked very well with audio for me.  Now that I have gone back to 9.04 even LMMS works the way it is supposed to.  In 9.10 it literally crashed the system every time I tried to use it and made me feel like I was using Windows all over again.

I don't know if I will ever "upgrade" from 9.04 again.

So, I ask... is there something specific that 9.10 is giving you that you feel like 9.04 doesn't make available?

Updates for one. In a few months, I think October, all supporting 9.04 will cease by developers. That means no more updates, patches, security fixes. You might as well have a sieve act as your firewall to the machine.

---

### Post by Phases on 2010-02-01
> **lidex said:**
> It appears that the correct  alsa module is being loaded, although not in the location I would expect to see it. Since you do have audio I would suggest commenting out this line in /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel power_save=10 power_save_controller=N
```
Just put a "#" in front of it. You'll need to reboot to see any changes.
VLC, I noted, doesn't have an option to select PA output but you might try selecting ALSA in Tools/Preferences/Audio/Output. For Skype have a look here:
[http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")

Thanks, tried that and rebooted. It sounds a little better on startup sound but still skips a little. Won't know about the rest of the sound stuff 'till I can get a chance to use it. 

While at work today I will dig through the links you've passed to me, I've only skimmed so far. What I saw seemed not relevant to me or something I've tried but I'll look closer today.

Thanks for takin' the time to try to help, do appreciate it.


> **Thomas Garman said:**
> ...So, I ask... is there something specific that 9.10 is giving you that you feel like 9.04 doesn't make available?

Nah not really, but the sound isn't much different than it was in 8.04, I'm not sure I think it'd be too different in 9.04.. also not sure I care to go through to restore process again, heh..

(LMMS?)

---

