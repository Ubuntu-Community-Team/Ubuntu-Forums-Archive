---
title: "Getting sound from new sound card"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by Hanj on 2006-12-25
I just replaced my old soundcard with an M-Audio Audiophile 24/96, but I'm having some trouble getting it to work properly. 
I can choose the card as 'device' in xfce sound settings, but when I do this, the 'useful controls' field becomes blank, and there's no sound coming from the speakers.
This is the output from 'aplay -l':
```

 $> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And this is from lspci:
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)

```

When I boot from the live cd, the card is autodetected and works just fine, so I'm guessing all I have to do is to somehow reconfigure alsa. I'm at a loss on how to do this though.


[EDIT] I used apt-get to remove all alsa packages and installed them again. Now after a reboot jack seems to recognize the card. Applications that connect to jack produce sound properly. However, I still can't get other applications to recognize it. The xfce volume control window is completely blank when I select the card.[/EDIT]

---

### Post by Hanj on 2006-12-26
I gave up and reinstalled Ubuntu, and now everything works except for one problem:

Sound works perfectly everywhere until I start up Jack (which is configured to use alsa). As soon as jack starts, only applications which connect to jack (hydrogen, ardour etc) get any sound. Also, jack will only start if I kill all other applications that make use of the sound card, which is pretty annoying. 

I tried installing alsa-oss and picked oss for 'Sound playback' in Sound preferences, but when I test it, it says the resource is busy. The same happens if I choose alsa instead.

Any help would be greatly appreciated.

---

### Post by Hanj on 2006-12-27
*Bump* 

Please?

---

### Post by majoridiot on 2006-12-27
although i haven't gotten into jack yet, i've had similar experiences where apps will not play
nicely with each other sound-wise.  i haven't found a way to get a system-wide sound mixer
like windows, where you can literally have sound on sound on sound from different apps
playing at the same time.  mythtv, in particular, seems to demand total control of alsa.

my (limited) understanding is that one of the reasons for jack was to have better sound
interoperability between apps.  i *believe* that jack would want total control of alsa so that
it could mix and meter out the sound as needed.  what you are now describing makes sense
to me, with my limited knowledge.

if nobody else chimes in, try giving this thread a bump again after the holidays.

---

### Post by Hanj on 2006-12-27
> my (limited) understanding is that one of the reasons for jack was to have better sound
interoperability between apps. i *believe* that jack would want total control of alsa so that
it could mix and meter out the sound as needed. what you are now describing makes sense
to me, with my limited knowledge.Yes, but I'm pretty certain I had it all working with the old soundcard, so it *should* be possible.

> if nobody else chimes in, try giving this thread a bump again after the holidays.Thanks for the tip :)

---

