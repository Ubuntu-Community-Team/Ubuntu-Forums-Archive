---
title: "Distorted sound in Feisty with Asus P5B"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by niktheblak on 2007-05-12
I'm using Kubuntu 7.04 with a Core 2 Duo setup using Asus P5B Deluxe/WiFi motherboard. I'm having some problems with distorted sound when using the integrated AD1988 sound chip.

All sound that comes out from the system is distorted. The distortion is like clipping, as if something was set way too loud. But it isn't, my mixer settings are at comfortable 74% and I've muted everything except the line output. Changing the volume level does not affect the distortion. In fact, lower volume levels seem to make it worse.

The weirdest thing is that when I activate the 'Beep' output in KMix, the sound improves for a while. For a few seconds, the sound is completely distortion-free, but after a while the distortion comes back.

I've tried the latest ALSA drivers (1.0.14rc4), but unfortunately that didn't solve the problem. Does anyone have any suggestion regarding on what to do next, since this thing is driving me crazy. I'm a musician and I'm planning on using Kubuntu for sound recording. Actually I don't plan to use the AD1988 chip for recording, I have a Terratec EWX24/96 sound card for that. But the problem with that card is that it doesn't work at all in Kubuntu.

---

### Post by luctor on 2007-05-12
I had almost the same problem with my onboard soundcard which uses the snd_via82xx  driver.
A detailed solution is here[ http://alsa.opensrc.org/Via8233#Poor_sound_quality]("http://alsa.opensrc.org/Via8233#Poor_sound_quality")

I've checked the alsa site and i can't see a driver for your AD1988 sound chip
What driver does it use ?

please post the output of
 ```
lsmod | grep snd 
```

BTW If you are a musician:guitar:  you might wanna check out [UbuntuStudio]("http://ubuntustudio.org") (although the site is down at the moment:rolleyes: )

---

### Post by niktheblak on 2007-05-12
The integrated sound chip uses the hda-intel driver. I'll try the suggested solution and report back the findings.

Output 'lsmod | grep snd' is:

```

snd_ice1712            75296  1 
snd_ice17xx_ak4xxx      6144  1 snd_ice1712
snd_ak4xxx_adda        10496  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427             11904  1 snd_ice1712
snd_ac97_codec        121048  1 snd_ice1712
ac97_bus                4224  1 snd_ac97_codec
snd_i2c                 8064  2 snd_ice1712,snd_cs8427
snd_mpu401_uart        11392  1 snd_ice1712
snd_hda_intel         309792  4 
snd_pcm_oss            50176  0 
snd_pcm                93960  5 snd_ice1712,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq_oss            39040  0 
snd_seq_midi           11264  0 
snd_rawmidi            30208  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                63520  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27400  3 snd_pcm,snd_seq
snd_seq_device         10900  4 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71464  23 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         12944  2 snd_hda_intel,snd_pcm
soundcore              10272  1 snd

```

---

### Post by luctor on 2007-05-12
Furhter reading

[http://alsa.opensrc.org/Hda](http://alsa.opensrc.org/Hda)

---

### Post by niktheblak on 2007-05-12
I tried to configure XMMS to use only the PCM 1 device but that didn't help the distortion. The result is the same when using the default output vs. PCM 1. The only thing that has helped so far has been activating the 'Beep' channel in KMix.

I tried to modprobe the driver with different type=xxx options, but that didn't help either.

---

### Post by niktheblak on 2007-05-12
Apparently the hda-intel isn't really the way to go if one wants a probem-free Linux experience with with sounds enabled. What sound cards would people recommend that are guaranteed to work under Ubuntu? Besides normal gaming cards I'm also thinking about more professional sound cards, such as E-MU 1212M.

---

### Post by luctor on 2007-05-12
I think a good place to ask such questions is on the #ubuntustudio irc channel

also checkout [https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")

---

### Post by niktheblak on 2007-05-14
I just did some digging and the sound chip that Asus P5B Deluxe uses is Analog Devices AD1988, aka SoundMax HD Audio.

Don't Analog Devices chips usually use the intel8xx driver and not the hda-intel driver? Could this simply be a hardware misdetection issue? Or does ALSA support AD1988 at all?

---

### Post by luctor on 2007-05-22
google thinks that AD1988 needs the hda-intel :-)
but I think you need the new alsa drivers (not sure though)

check out this article
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by e30ernest on 2007-05-30
Upon installation of Ubuntu, the sound was fine.  I had to transfer my cpu so I had to shut it down.  When I rebooted my sound was just as the author of the thread described.  I am using a similar chipset.  

Using the code Luctor posted, I got:

```
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
```

I find it strange that it was working properly one day, and have problems the next day.  At first, I thought by speakers were to blame.  Only after booted into windows did I know that they were ok so I started searching here.  It's been two weeks since the problem started, so I can no longer remember any changes I made (if any) before the problem occurred.

---

