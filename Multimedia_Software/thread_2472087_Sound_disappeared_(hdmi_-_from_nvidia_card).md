---
title: "Sound disappeared (hdmi - from nvidia card)"
date: 2022-02-17
forum: Multimedia Software
---

### Post by linuux on 2022-02-17
I've had it with this distro.   Sound just disappeared suddenly.   I am currently getting sound from the computer's internal speakers - unacceptable.

Nvidia driver is installed.   I was getting sound via the hdmi audio output.   Which has disappeared.   There is usually an 'extra' setting that is available that has disappeared.

I shouldn't have to troubleshoot this stuff!   I didn't touch sound.   I didn't make any change in the settings.   I can only assume an update has modified something.

---

### Post by linuux on 2022-02-17
I thought of rebooting - and the sound setting returned.   Is that buggy?  Why is that?   

Playback Device now lists (again) HDMI / DisplayPort GP108 High Definition Audio Controller Digital Stereo (HDMI) 

Profile drop down menu displays Digital Stereo (HDMI) - expected as I have to use TV speakers.

Not sure why it disappeared in the first place or why a reboot suddenly 'brought it back.'   I was just hoping someone reading this knows why this happened.   Is it a bug?   Did some audio program restart (this is a PulseAudio 'thing' - isn't it)?   I have hated PulseAudio for a while - it is very problematic in my experience and has been horrible for years.   But, I notice that no one ever talks about it.   I am not sure why Linux devs are not addressing how awful it is.

---

### Post by CharlesA on 2022-02-17
It would probably have helped to specify which Nvidia card you are using, what TV you are using and what version of Ubuntu you are using instead of just saying it "stopped working" with no other information.

With that said, there are a bunch of different ways to troubleshoot an issue like this but I usually start at looking at the output of dmesg to see if anything funky is going on.

You can run that from a terminal via:

```
sudo dmesg
```

---

### Post by linuux on 2022-02-17
> **CharlesA said:**
> It would probably have helped to specify which Nvidia card you are using, what TV you are using and what version of Ubuntu you are using instead of just saying it "stopped working" with no other information.

With that said, there are a bunch of different ways to troubleshoot an issue like this but I usually start at looking at the output of dmesg to see if anything funky is going on.

You can run that from a terminal via:

```
sudo dmesg
```

You're RIGHT!   My bad!   The sound did return and the hdmi option/setting returned.   I just don't know why that happened.

It's a GT 1030 card, using the Nvidia ver. 470 driver that is part of the repo package.   It's a 4K Roku Smart TV.   I am forced to use the hdmi audio for sound (from the graphics card) since I don't have any computer speakers or Audio Receiver (or other options) - so the speakers of the TV is preferred over the old Dell Optiplex 3020 sff speakers/audio out option (doesn't have hdmi/audio).  

Summary info:   i5-4570, Dell Optiplex 3020 sff, GT 1030 using hdmi for both video/audio, DDR3 8gb, Kubuntu 22.04, kernel 5.15, Nvidia driver ver. 470, 4k TV Roku, 4k resolution

I forgot to try dmesg.   Thanks.   If it happens again, I will try to think of this first.

I might be switching distros soon, though.

---

### Post by QIII on 2022-02-17
Please keep your language family- and workplace-friendly.

In response to your basic query:  It is entirely possible that the update DID cause the upset temporarily until you loaded an updated module when you rebooted.

It is a bit hasty to assume that an OS is buggy and problematic based on your sample size of one.  In Logic, there is a term for that:  Hasty Generalization.

Please remain calm when something happens unexpectedly, avoid such a histrionic outburst and understand that for millions of us the OS works perfectly fine.

By the way, there is absolutely nothing wrong with using a different distro.  In fact, I encourage it.  Find what works for ***you***.  You won't hurt our feelings.

---

### Post by #&amp;thj^% on 2022-02-17
> **QIII said:**
> Please keep your language family- and workplace-friendly.

In response to your basic query:  It is entirely possible that the update DID cause the upset temporarily until you loaded an updated module when you rebooted.

It is a bit hasty to assume that an OS is buggy and problematic based on your sample size of one.  In Logic, there is a term for that:  Hasty Generalization.

Please remain calm when something happens unexpectedly, avoid such a histrionic outburst and understand that for millions of us the OS works perfectly fine.

By the way, there is absolutely nothing wrong with using a different distro.  In fact, I encourage it.  Find what works for ***you***.  You won't hurt our feelings.

Thanks Qlll, this kind of talk sets a tone we don't encourage.

---

### Post by linuux on 2022-02-17
I can provide a substantial list of people posting various kde/kubuntu-based problems if desired.

---

### Post by SeijiSensei on 2022-02-18
Recently I upgraded to Kubuntu 22.04.  Yesterday I discovered I had no sound and remembered that I hadn't installed the nvidia module, 470 in my case.  I checked the audio control panel in System Settings and saw the GP108 audio controller was marked "off."  When I installed the module, the card was recognized upon reboot, and the sound came back.

However this morning I have no sound again despite the module being loaded.  

```
$ lsmod  | grep nvidia
nvidia_uvm           1179648  0
nvidia_drm             65536  7

nvidia_modeset       1200128  21 nvidia_drm
nvidia              35328000  1309 nvidia_uvm,nvidia_modeset
drm_kms_helper        307200  1 nvidia_drm
drm                   606208  11 drm_kms_helper,nvidia,nvidia_drm

```

Browsing dmesg didn't show any problems. 
```

[   18.530469] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input20
[   18.530507] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input21
[   18.530550] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input22
[   18.530589] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input23
[   18.530620] input: HDA NVidia HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input24

```
KDE reports the card as "inactive."

I hate things that work one day and not the next.

---

### Post by CharlesA on 2022-02-18
> **SeijiSensei said:**
> Recently I upgraded to Kubuntu 22.04.  Yesterday I discovered I had no sound and remembered that I hadn't installed the nvidia module, 470 in my case.  I checked the audio control panel in System Settings and saw the GP108 audio controller was marked "off."  When I installed the module, the card was recognized upon reboot, and the sound came back.

However this morning I have no sound again despite the module being loaded.  

```
$ lsmod  | grep nvidia
nvidia_uvm           1179648  0
nvidia_drm             65536  7

nvidia_modeset       1200128  21 nvidia_drm
nvidia              35328000  1309 nvidia_uvm,nvidia_modeset
drm_kms_helper        307200  1 nvidia_drm
drm                   606208  11 drm_kms_helper,nvidia,nvidia_drm

```

Browsing dmesg didn't show any problems. 
```

[   18.530469] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input20
[   18.530507] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input21
[   18.530550] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input22
[   18.530589] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input23
[   18.530620] input: HDA NVidia HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input24

```
KDE reports the card as "inactive."

I hate things that work one day and not the next.

Interesting. Have you tried to remove the kernel module and add it in again? I don't have any Nvidia gear, running under Linux, so I haven't run into that problem, but I have run into issues where a kernel module is loaded, but the thing it's loaded for is nowhere to be found. Unloading it and then loading it again via modprobe would usually fix it for me.

---

### Post by SeijiSensei on 2022-02-19
I have rebooted a couple of times since installing the module. Sound never comes up. KDE continues to report the device as "inactive."

I'm probably just going to go back to 20.04 for the time being.

Windows 10 finds and uses the card.

---

