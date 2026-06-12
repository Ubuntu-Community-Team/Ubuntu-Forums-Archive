---
title: "HDMI no audio ONLY in XBMC"
date: 2008-11-14
forum: Multimedia Software
---

### Post by sexus6 on 2008-11-14
- I have Asus M3A78-EM Motherboard that have ATI HD3200 graphic card.
- I use HARDY HERON to xbmc (Intrepid has bugs with my ATI HD3200 card in fullscreen modes for xbmc). I enabled HDMI sound, umutting IEC958 device. In Preferences=>Sound, I test HDMI ATI, and there is sound by HDMI (at my HDTV). If I use rythmbox, totem, or any software that has sound playing,  is listened by the HDTV speakers.
- The problem is only at XBMC. I use ppa xbmc packages for hardy. There is no sound inside xbmc.No sound effects, no sound for playing music, no sound in videos. If I choose in Sound Hardware DIGITAL or ANALOGIC there is no change. 
- After this problem, I made some tests. This motherboard has 2 soundcard devices. The first primary soundcard, with common 6 outputs, and HDMI soundcard device. For tests, I disable first soundcard device. I start system, and only 1 device was. alsamixer shows me only HDMI audio, and Preferencies=> Sound too. But XBMC no sound. I choose at xbmc sound hardware options, digital and analogic too, and:
default sound device = default
passthrough = iec958
I try some combos => default/default, default/iec958, iec958/default, iec958/iec958... I try analogic, digital... inside xbmc.

Only xbmc is the problem, all apps and sounds works by hdmi, before disable first sound card and after.
What's the problem?

---

### Post by ToeKing on 2008-12-18
This is 4 weeks old, but it's the same problem I'm having.  I the hw isn't exactly the same, but it's very similar.  HDMI output with an ATI Radeon x1200 series.  Only error I see is in the console when I exit:

```
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ScreenSaver was not provided by any .service files
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
CRITSEC[0x8cfa384]: Trying to enter destroyed section.
CRITSEC[0x8cfa384]: Trying to leave destroyed section.
Segmentation fault (core dumped)
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ScreenSaver was not provided by any .service files

```

I tried looking into the ALSA issue and didn't come up with much.  Running aplay with a .wav creates a similar problem:

```
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
aplay: main:583: audio open error: No such file or directory
```

Not sure where to go from here.  Sound does work fine for programs like VLC and when doing an audio test.

---

### Post by mr_raider on 2008-12-26
Try going into teh xbmc preferences, audio setup screen. Set sound to digital, and for output as well as passthrough device, type "hdmi" in lowercase.

---

### Post by abrown1982 on 2009-03-31
Thought I would reply to this since it sorted the problem for me!

HDMI sound only, all apps work in Ubuntu 8.10 with sound through HDMI but not XBMC, change default sound to digital, and change both passthrough and default sound device to hdmi and I now have sound.  Great fix, should be in more places!

---

### Post by gallen50 on 2009-04-09
> **sexus6 said:**
> - I have Asus M3A78-EM Motherboard that have ATI HD3200 graphic card.
- I use HARDY HERON to xbmc (Intrepid has bugs with my ATI HD3200 card in fullscreen modes for xbmc). I enabled HDMI sound, umutting IEC958 device. In Preferences=>Sound, I test HDMI ATI, and there is sound by HDMI (at my HDTV). If I use rythmbox, totem, or any software that has sound playing,  is listened by the HDTV speakers.
- The problem is only at XBMC. I use ppa xbmc packages for hardy. There is no sound inside xbmc.No sound effects, no sound for playing music, no sound in videos. If I choose in Sound Hardware DIGITAL or ANALOGIC there is no change. 
- After this problem, I made some tests. This motherboard has 2 soundcard devices. The first primary soundcard, with common 6 outputs, and HDMI soundcard device. For tests, I disable first soundcard device. I start system, and only 1 device was. alsamixer shows me only HDMI audio, and Preferencies=> Sound too. But XBMC no sound. I choose at xbmc sound hardware options, digital and analogic too, and:
default sound device = default
passthrough = iec958
I try some combos => default/default, default/iec958, iec958/default, iec958/iec958... I try analogic, digital... inside xbmc.

Only xbmc is the problem, all apps and sounds works by hdmi, before disable first sound card and after.
What's the problem?

@sexus6
I have the same mobo and get the test sounds out of the HDMI under Preferences>Sound but can't get anything to play through the HDMI. Any suggestions what setting I could have wrong that is messing things up for me?

---

### Post by jngrim on 2009-04-20
I changed my settings as you suggested(ditigal and change to hdmi/hdmi  but it still does not work...when I go to play shoutcast or an mp3, it tells me the the audio device failed to initialize.  I appears that xbmc might be not seeing the alsa driver. I really want to get this working becuase i hate windows...

---

### Post by kdiddy on 2009-05-09
thank you so much ! been searching for weeks, this worked for me 
Jaunty 64bit,xbmc


kevin

---

### Post by zosky on 2009-06-02
i am ONLY using XMBC on Ubuntu Jaunty Minimal
i managed to get sound on HDMI from XBMC 
[by forcing alsa default to hw 1:3 as posted here]("http://ubuntuforums.org/showpost.php?p=6690552&postcount=4")

***YMMV ... i'm using an HTPC for my HDTV in the living room ***

---

### Post by skdevnath on 2009-08-18
> **jngrim said:**
> I changed my settings as you suggested(ditigal and change to hdmi/hdmi  but it still does not work...when I go to play shoutcast or an mp3, it tells me the the audio device failed to initialize.  I appears that xbmc might be not seeing the alsa driver. I really want to get this working becuase i hate windows...


I too get exact same error.

---

### Post by skdevnath on 2009-08-19
> **zosky said:**
> i am ONLY using XMBC on Ubuntu Jaunty Minimal
i managed to get sound on HDMI from XBMC 
[by forcing alsa default to hw 1:3 as posted here]("http://ubuntuforums.org/showpost.php?p=6690552&postcount=4")

***YMMV ... i'm using an HTPC for my HDTV in the living room ***

I have motherboard M3A78-EM and I installed Jaunty. I can hear sound over HDMI, if I use VLC. I can't hear  music, Video sound from XBMC. However I can hear clicking, shuffling sound on my TV via HDMI on XBMC.

I tried above trick and it seems it worked, however next day morning I turn ON my PC and I see my sound issues are back :(

Please help me to fix this issue. My media center PC investment (time+money) is going to drain. ( worse case I will be back to Freevo, but I will miss XBMC's user interface)

Please note, I am using TV for sound not any receiver.

---

### Post by jamesdew on 2011-01-24
this solved it for me (well mostly)

[http://forum.xbmc.org/showthread.php?t=71885](http://forum.xbmc.org/showthread.php?t=71885)

---

### Post by dannield on 2011-04-11
i'm using my TV via HDMI as well running ubuntu 10.10.
not sure this is the same case, but i had DTS enabled under setting --> system settings --> audio
disabled that and sound was back

---

