---
title: "Ubuntu 11.04 no microphone input"
date: 2011-06-26
forum: Multimedia Software
---

### Post by kettenheinz on 2011-06-26
Hey folks,

after upgrading to Ubuntu 11.04 from 10.10 my microphone on my headset stopped working. I mainly want to use it for things like Skype or Teamspeak. The problem has been narrowed down a bit as I have no problem playing sounds and the microphone was tested on other machines and worked fine.

I already looked up a lot of threads and solutions but none have helped yet. Here is what I tried:

Use arecord in the terminal to record a .wav and listen to it. No sound was recorded. I tried various settings in the pavucontrol and alsamixer and since I have a mono-mic I set the front-right input channel to 0 and the left one to 75%. I checked that nothing was muted or turned off, that the hardware was recognized, that the system was set to analog stereo duplex and that the headset was set as input device. I also reinstalled the alsa packeages (util, base, etc) and made sure there is no conflict with OSS. Still no sound is recorded.

Here is the lshw -c sound :

  *-multimedia            
       description: Audio device
       product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:d9000000-d9003fff

So I think the hardware is alright, it is just some software problem. I hope you guys have some ideas. Thanks in advance for any help,

Kettenheinz

---

### Post by lidex on 2011-06-26
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by kettenheinz on 2011-06-26
Here is the link. 

[http://www.alsa-project.org/db/?f=3a9b74ad30c014a923c1fc627a747737847a55f1](http://www.alsa-project.org/db/?f=3a9b74ad30c014a923c1fc627a747737847a55f1)

Thanks for the quick reply.

---

### Post by lidex on 2011-06-26
Try this using a Terminal
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by kettenheinz on 2011-06-26
I executed the command and rebooted, still no sound being recorded.

---

### Post by lidex on 2011-06-27
Lets see the dmesg output now:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by kettenheinz on 2011-06-27
Ok, here is the last part of it:

[   33.758934] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.765062] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.765072] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.765681] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.765689] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.766196] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.766203] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.766833] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.766841] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.768056] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.768067] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.768656] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.768665] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.769179] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.769187] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.770025] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.770035] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.771258] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.771266] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.771809] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.771818] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.772398] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.772407] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.773053] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.773062] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.774251] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.774259] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.774798] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.774806] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.775319] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.775327] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.775968] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.775976] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.777249] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.777258] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.777799] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.777807] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.778319] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.778327] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.778963] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.778971] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.780392] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   33.780402] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   33.787522] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[   33.787753] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[   33.796272] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[   33.797243] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[   33.799338] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x3c00, format=0x11
[   33.799352] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x15, stream=0x1, channel=0, format=0x11
[   33.799371] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x3c00, format=0x11
[   33.799377] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x15, stream=0x1, channel=0, format=0x11
[   33.799413] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[   33.799433] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[   33.809583] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   33.809597] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   33.816070] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[   33.824075] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[   33.824091] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[   33.824100] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[   33.843450] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   33.843463] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x15, stream=0x1, channel=0, format=0x11
[   33.843482] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   33.843488] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x15, stream=0x1, channel=0, format=0x11
[   34.027687] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   38.926129] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[   38.926164] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[   38.930572] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   38.936072] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   38.944107] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[   38.944118] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[   39.267988] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
--
[   41.785748] padlock_aes: VIA PadLock not detected.
[   46.816234] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   46.816247] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x15, stream=0x1, channel=0, format=0x11
[   46.816266] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   46.816272] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x15, stream=0x1, channel=0, format=0x11
[   52.448018] wlan0: no IPv6 routers present
[   70.979317] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[   70.979353] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[   95.807092] show_signal_msg: 21 callbacks suppressed
[   95.807108] apt-check[1817]: segfault at 0 ip 00eda5c6 sp bfd66ca8 error 6 in libc-2.13.so[e65000+15a000]
[   99.308622] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   99.308648] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x15, stream=0x1, channel=0, format=0x11
[   99.308676] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x11
[   99.308688] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x15, stream=0x1, channel=0, format=0x11
[  109.349883] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[  109.349961] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[  111.740735] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  111.740761] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  111.748064] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[  111.756135] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  111.756154] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  111.756166] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[  122.847882] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[  122.856050] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[  122.864135] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[  122.864148] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[  268.174022] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  268.174048] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  268.180077] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[  268.188176] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[  268.188197] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[  268.188209] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[ 4055.407847] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[ 4055.412091] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[ 4055.420141] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[ 4055.420154] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[28536.127683] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[28541.031209] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x11
[28541.031233] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x15, stream=0x1, channel=0, format=0x11
[28541.031262] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x11
[28541.031273] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x15, stream=0x1, channel=0, format=0x11
[28541.361597] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[28541.361624] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[28541.368141] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[28541.376147] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[28541.376167] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[28541.376180] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[28546.332694] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[28546.332762] ALSA hda_codec.c:1358: hda_codec_cleanup_stream: NID=0x15
[28546.396632] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[28546.404129] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[28546.412231] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[28546.412250] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[29763.896173] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[29763.896203] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[29763.904080] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[29763.912106] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[29763.912123] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[29763.912135] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[29772.037212] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[29772.044055] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[29772.052131] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[29772.052144] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[29823.790641] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[29823.790668] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[29823.796111] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[29823.804187] ALSA hda_intel.c:1700: azx_pcm_prepare: bufsize=0x10000, format=0x4011
[29823.804208] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[29823.804220] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x5, channel=0, format=0x4011
[29830.839182] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[29830.844125] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0
[29830.852212] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x10, stream=0x0, channel=0, format=0x0
[29830.852231] ALSA hda_codec.c:1295: hda_codec_setup_stream: NID=0x13, stream=0x0, channel=0, format=0x0

---

### Post by kettenheinz on 2011-06-29
I do not mean to be impolite, but have there been any new ideas for solving this problem?

---

### Post by marcalj on 2011-07-02
> **kettenheinz said:**
> I do not mean to be impolite, but have there been any new ideas for solving this problem?

I found today a weird solution:

pulseaudio -k && pulseaudio

Reference: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/557421](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/557421)

:)

---

### Post by kettenheinz on 2011-07-03
I am not sure if i executed this correctly, here is the result from the terminal:

$ pulseaudio -k && pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

The command temporarily disabled my sound output, but did not fix the input.


I also discovered, independantly from this command, my sound starts to get worse as soon as I use firefox to display sound (e.g. youtube). I get a lot of distortions and cracking sounds, especially when using skype at the same time. And while my sound output works aside from that, I can not hear the test sound in the Skype options menu (which only offers local pulseaudio support). Might pulseaudio be the problem?

---

### Post by marcalj on 2011-07-03
The result is the same in my case, and after that I can use my input to record. Sound output is working as expected.

Note that I need to restart Skype, and after that I can do the test call successfully.

In other post recommend to use "pavucontrol" to unmute or set one input source as the default source. And remember to set the duplex Pulseaudio profile in the sound settings.

---

### Post by kettenheinz on 2011-07-04
That did the trick for me. Had to tweak the sound settings a bit, but that was no big deal. Very important if you have a normal headset like me, check your microphone type. If your input is just mono, you have to deactivate one (I used the right one) input channel and set it to mute.

Thanks a lot for all the help, I owe you a cup of Ubuntu.

---

### Post by marcalj on 2011-08-16
I don't know why but now I need to disable duplex profile in the main sound card. Now it works perfect :S

Now profile is basic analog output.

---

### Post by Simon_WM on 2011-08-16
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/731706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/731706)

Look at post #19

                 After having done some more research  about it - and having access to an actual machine - it seems the easiest  way to solve this bug would be to edit /etc/modprobe.d/alsa-base.conf and adding the line:


 options snd-hda-intel model=dell-m6-dmic


 Then reboot.  That will remove one internal mic and leave the correct one still there.
For reference, this was used on PCI SSID 1028:0413.


____

Open up terminal and type in


> sudo gedit  /etc/modprobe.d/alsa-base.conf
then add: >  options snd-hda-intel model=dell-m6-dmicto the ver bottom and reboot..

_____
_____

Or try post #14


Following these steps to enable your internal microphone:
1. start alsamixer in a terminal
2. Hit "tab" or "F4" to switch to capture configuration
3. Hit right arrow key 3 times to select "<Input Source>"
4. Hit Up/Down arrow key several times to select "Input Source [Internal Mic 1]" as your current input source.
 This is just a temporary solution and you will have to do this gain once you reboot your machine :(
We will have to wait till ubuntu engineers solve this bug. Hopefully soon.

---

### Post by marcalj on 2011-08-16
Now I don't need to call any script or change configuration on every boot. And I don't have this specific model of snd-hda-intel module.

Seems that some update fixes something and the problem was fixed setting sound card on another profile.

I use the microphone from a USB webcam, so I don't know if it's solved with normal mini-jack microphone.

Thanks anyway.

---

