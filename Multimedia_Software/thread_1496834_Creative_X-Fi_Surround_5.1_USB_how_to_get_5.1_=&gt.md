---
title: "Creative X-Fi Surround 5.1 USB: how to get 5.1 =&gt; home theater system with optical?"
date: 2010-05-29
forum: Multimedia Software
---

### Post by The Bright Side on 2010-05-29
Hi!

I bought the Creative X-Fi 5.1 Surround USB card today and it works flawlessly with my 5.1 speaker set that I use for my computer. However, in the next few days, I'm getting a 5.1 home theater system to which I want to hook up both my new SACD player and my PC.

I got the Creative because it has an optical output, so it should allow me to send 5.1 audio to the receiver. I'm a bit confused, though, because when I look at my hardware tab in the Sound Preferences, I only have the options that I attached to choose from. There is no digital/optical multichannel profile in there.

I'm asking now because I'm sure I will struggle with this when I have the home theater system: do you know from your own experience which of these profiles I need to choose to play back 5.1 from my computer with my home theater system?

Thanks!
M.

---

### Post by The Bright Side on 2010-05-29
Screenshot attached :-) Thanks!

---

### Post by The Bright Side on 2010-05-30
Nobody? I have the 5.1 sound system now, and I want to get digital 5.1 sound! Please, it must be possible! That's why I bought this whole setup in the first place!

Is there nobody out there that uses the Creative X-Fi Surround 5.1 USB card to play back digital 5.1 through optical cable?

Thanks!

---

### Post by The Bright Side on 2010-05-30
YES!!!!

This did it:
[http://ohioloco.ubuntuforums.org/showthread.php?t=1480529](http://ohioloco.ubuntuforums.org/showthread.php?t=1480529)

To summarize (for my system):

[LIST]
[*]In Sound Preferences, select "Analog Stereo Duplex"
[*]In VLC preferences, select "All" in "Show Settings" and go to audio options
[*]Enable "Use S/PDIF when available"
[*]Set "Force Detection of Dolby Surround" to "Off" (should be standard)
[*]In "Output Modules", select ALSA
[*]In the "ALSA" tree node, I selected "SB X-Fi Surround 5.1: USB Audio #1 (hw:1,1)"
[/LIST]

Basically, Ubuntu can't manage S/PDIF, so you're setting up VLC to access and manage it by itself. What an amazing program.

---

### Post by molder on 2010-07-02
I have an X-Fi Music Extreme installed in my HTPC system.  I can get the optical digital out to work in stereo but not 5.1.  I have tried these steps but have not been able to get anything more than stereo.  In fact, following the advice of the previous post all I can get is noise from XBMC

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

aplay -l
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

I also tried to install the alsa-driver  snapshot package and got a make ERROR 2 Message

```
andrew@MythTV-Zeus:~/alsa/alsa-driver$ make
make dep
make[1]: Entering directory `/home/andrew/alsa/alsa-driver'
make[2]: Entering directory `/home/andrew/alsa/alsa-driver/include'
make -C sound prepare
make[3]: Entering directory `/home/andrew/alsa/alsa-driver/include/sound'
make prepare2
...
...
make[3]: Leaving directory `/home/andrew/alsa/alsa-driver/pcmcia/vx'
make[2]: Leaving directory `/home/andrew/alsa/alsa-driver/pcmcia'
make[2]: Entering directory `/home/andrew/alsa/alsa-driver/misc'
make[2]: Leaving directory `/home/andrew/alsa/alsa-driver/misc'
make[1]: Leaving directory `/home/andrew/alsa/alsa-driver'
make -C  SUBDIRS=/home/andrew/alsa/alsa-driver  CPP="gcc -E" CC="gcc" modules
make: *** SUBDIRS=/home/andrew/alsa/alsa-driver: No such file or directory.  Stop.
make: *** [compile] Error 2

```

The idea of purchasing the X-Fi sound card was to use the digital optical outputs to connect to my home theater system.

---

### Post by The Bright Side on 2010-07-03
I really get the impression that Ubuntu's support for this is far from ideal yet. Indeed, in the system's sound settings, there is no way in hell to get 5.1 optical output going.

For me, the only way to get Surround is by using the VLC Media Player and configuring it to handle sound settings itself. The player will recognize the S/PDIF and use it when the medium you're playing back has a multichannel track.

Are you trying VLC?

---

### Post by molder on 2010-07-04
Tried VLC, XBMC, and mPlayer.  None of them worked.  Trying to get it going with windows XP, no luck.  Then I upgraded XP to Windows 7 and everything magically worked, including my MCE remote.  I really wanted Ubuntu to work but in this case it seems as of Windows 7 is the operating system that just works.  I am thinking that the kernel may lack the capability to recognize the DTS processor.  From what I have read the support for the X-Fi driver is not mature yet, some 4 years after the release of the card.

---

### Post by Kheops_74 on 2011-03-23
Saw this post. It solve the problem in VLC. Any people have idea to make Boxee work too? I have 3.0 sound but not 5.1. 

In MythTV it works well (5.1).

En résumé
Working :
MythTV
VLC

Not working:
TOTEM
Xine
Boxee

---

### Post by Kheops_74 on 2011-03-24
I went to the BIOS and disable the onboard sound card. All software that was 3.0 are 5.0 now. The only thing that didn't work everywhere is the subwoofer. Any idea?

Thanks

---

### Post by Kheops_74 on 2011-03-27
Anybody know why i have no control in alsamixer? I only see this message : "This sound device does not have any control"

---

