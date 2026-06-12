---
title: "Digital Stereo Duplex sound on an optical 5.1 output.."
date: 2010-05-11
forum: Multimedia Software
---

### Post by Yionel on 2010-05-11
Hi everybody,

Sorry I'm french so I have to explain my problem simply.
I have an optical output connected to an ampli but this output is always in stereo.
My pc is a notbook Acer 7730G and it's specified :
> True5.1-channel surround sound output
High-definition audio support
S/PDIF (Sony/Philips Digital Interface) support for digital
speakersBut under Ubuntu I have digital stereo duplex
[IMG]http://www.yionel.fr/vrac/sound.png[/IMG]
Of course, I would have surround effect !
I think it's about passthrought option but I don't know where I can modified it.

```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

```
[yo@yo-laptop:~] $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
[yo@yo-laptop:~] $ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC888 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, NVIDIA HDMI
    HDMI Audio Output

```

Can you help me ?
Thanks a lot !!

---

### Post by Yionel on 2010-05-13
Nobody for my problem ? :-(:-(:-(

---

### Post by isledur on 2010-05-15
Same problem - no good leads :(

---

### Post by Yionel on 2010-05-16
I have found the solution \o/

[http://www.yionel.com/?p=297]("http://www.yionel.com/?p=297")

It's my blog, sorry it's in french ;)

---

### Post by neilfeld on 2010-05-26
Hello,

I have encountered the same issue and your webpage is not loading.  Can please post your findings?

Merci

---

### Post by Yionel on 2010-05-27
Yes of course. I'm stupid because the page can't be loaded now because my server is out !

So you had to : check is system > preference > sound > hardware > Analog Stereo Duplex

After, with command alsamixer : demute (m) spdif output

And in the software like VLC
  -> use SPDIF when avalaible
  -> output module : ALSA audio output
  -> ALSA : check the good output optical (HDA Intel : ALC888 Digital (hw:0,1) for exemple

;)

---

### Post by codefu on 2010-06-03
Thanks! that helped.

---

### Post by neilfeld on 2010-06-05
Sorry I am new to using ubuntu.  Where do you enter the alsamixer information?

---

### Post by neilfeld on 2010-06-05
Ok I was able to get the sound working through the instructions you posted, but I still cannot get the subwoofer to work.  Do you have any suggestions for that?

---

### Post by neilfeld on 2010-06-05
Sorry for all of my previous posts I guess you need to plug your subwoofer into the correct output if you want it to work at all.  Thanks for all of your help.

---

### Post by molder on 2010-07-02
I am confused on the eact topic here.  Is this thread to get 5.1 optical output?  If si I would really like that but only have been able to get stereo with my optical output.

aplay -L
```

andrew@MythTV-Zeus:~/alsa/alsa-driver$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=XFi
    Creative X-Fi, Front/WaveIn
    Default Audio Device
front:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    Front speakers
rear:CARD=XFi,DEV=0
    Creative X-Fi, Surround
    Rear speakers
center_lfe:CARD=XFi,DEV=0
    Creative X-Fi, Center/LFE
    Center and Subwoofer speakers
side:CARD=XFi,DEV=0
    Creative X-Fi, Side
    Side speakers
surround40:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    4.0 Surround output to Front and Rear speakers
surround41:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=XFi,DEV=0
    Creative X-Fi, IEC958 Non-audio
    IEC958 (S/PDIF) Digital Audio Output


```
Aplay -L
```
andrew@MythTV-Zeus:~/alsa/alsa-driver$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=XFi
    Creative X-Fi, Front/WaveIn
    Default Audio Device
front:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    Front speakers
rear:CARD=XFi,DEV=0
    Creative X-Fi, Surround
    Rear speakers
center_lfe:CARD=XFi,DEV=0
    Creative X-Fi, Center/LFE
    Center and Subwoofer speakers
side:CARD=XFi,DEV=0
    Creative X-Fi, Side
    Side speakers
surround40:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    4.0 Surround output to Front and Rear speakers
surround41:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=XFi,DEV=0
    Creative X-Fi, IEC958 Non-audio
    IEC958 (S/PDIF) Digital Audio Output
andrew@MythTV-Zeus:~/alsa/alsa-driver$ alsamixer
andrew@MythTV-Zeus:~/alsa/alsa-driver$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

