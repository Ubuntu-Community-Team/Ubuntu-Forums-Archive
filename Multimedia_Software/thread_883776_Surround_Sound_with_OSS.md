---
title: "Surround Sound with OSS"
date: 2008-08-08
forum: Multimedia Software
---

### Post by andho on 2008-08-08
Hi!

I have an Intel High Definition Audio (ICH7) STAC9221 A onboard soundcard

I installed Ubuntu 8.04 and my sound wasn't working right. It worked on 7. So i searched around the forum and messed around and atlast got sound to work using [this thread]("http://ubuntuforums.org/showthread.php?t=780961")

So sound is working and when i run osstest: sound is coming from where it should. Surround sound ok :)

My problem is actually using surround sound practically. I download [Elephants Dream]("http://orange.blender.org/") to check if surround sound works and played it with VLC.
The sound only comes from the front speaker.

Can you please help me get this working :)
Thanks

---

### Post by dipuz on 2009-07-05
any1

---

### Post by boo-boo on 2009-12-23
sorry that this is no answer to ur question but i have the same problem.

Installed 9.10 64bit and sound was allways crashing ... tried several workarrounds, killed my apt reinstalled ... and so on... then i found oss and removed every other sound (alsa and pulse) 

now i got a working stereo sound ... even with vlc and pidgin, 
firefox = nosound ,
and i've got a 7.1 soundchip onboard. i think its maybe the same chip...
running with a 5.1 sorround system. worked well with pulse/alsa before but crashing and sometimes stucking and screwed sounds.

ossinfo says ->
```

Version info: OSS 4.2 (b 2002/200912240049) (0x00040100) OSS_HG
Platform: Linux/x86_64 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 (boo-desktop)

Number of audio devices:    9
Number of audio engines:    13
Number of MIDI devices:        0
Number of mixer devices:    1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 nVidia HD Audio interrupts=3302046 (3347135)
    HD Audio controller nVidia HD Audio
    Vendor ID    0x10de0774
    Subvendor ID 0x1043836c
     Codec  0: Unknown (0x11060397/0x1043836c)
     Codec  3: Unknown (0x10de0002/0x10de0101)

MIDI devices (/dev/midi*)

Mixer devices
 0: High Definition Audio 0x1106039 (Mixer 0 of device object 1)

Audio devices
HD Audio play pcm1                /dev/oss/oss_hdaudio0/pcm0  (device index 0)
HD Audio play pcm2                /dev/oss/oss_hdaudio0/pcm1  (device index 1)
HD Audio play pcm3                /dev/oss/oss_hdaudio0/pcm2  (device index 2)
HD Audio play pcm4                /dev/oss/oss_hdaudio0/pcm3  (device index 3)
HD Audio play spdifout1           /dev/oss/oss_hdaudio0/spdout0  (device index 4)
HD Audio play spdifout2           /dev/oss/oss_hdaudio0/spdout1  (device index 5)
HD Audio play spdifout4           /dev/oss/oss_hdaudio0/spdout2  (device index 6)
HD Audio rec select1              /dev/oss/oss_hdaudio0/pcmin0  (device index 7)
HD Audio rec jack6                /dev/oss/oss_hdaudio0/pcmin1  (device index 8)

Nodes
  /dev/dsp -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_in -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_out -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_ac3 -> /dev/oss/oss_hdaudio0/spdout0
  /dev/dsp_mmap -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_hdaudio0/pcm0


```i am next to using my old windows again but giving up is no solution for me :P 

getting some sleep right now. hope for some more answers in here now ;)

---

