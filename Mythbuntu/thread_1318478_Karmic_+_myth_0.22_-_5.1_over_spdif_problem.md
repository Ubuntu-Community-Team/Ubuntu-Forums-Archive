---
title: "Karmic + myth 0.22 - 5.1 over spdif problem"
date: 2009-11-07
forum: Mythbuntu
---

### Post by pootle1 on 2009-11-07
I've got a backend / frontend split setup, and have just build new front end to drive the big screen and hifi.  I can't get 5.1 (or anything other than stereo) out now.

Any idea what I can do to fix this?

I've used the very good guide [here ]("http://www.mythtv.org/wiki/AllensDigitalAudioHowto")and for the first time I get spdif output from youtube, bbc iplayer etc. which is good :)

but with the settings as in the guide I get digital hash whenever I have a DD source - sounds like something in the sound chain is scrambling the data.

PC is based on ASUS M2N SLi deluxe with Nvidia grapihcs card

Using copper SPDIF connection  to Panasonic amp

Music plays OK from Flac files on the backend server

with the settings defined in the link above 
(output default, passthrough default, DD5.1 and DTS passthrough enabled)
BBC1 is OK
BBC HD gives digital hash
playing DVD gives digital hash

any other setting in passthrough means I get silence on anything other than stereo

The amp always shows digital stereo as the input type.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```Here's what looks like the relevant bit of the mythfrontendlog
```
2009-11-07 21:01:45.584 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-11-07 21:01:45.895 AFD: Opened codec 0xa3c0580, id(H264) type(Video)
2009-11-07 21:01:45.895 AFD: codec MP2 has 2 channels
2009-11-07 21:01:45.895 AFD: Opened codec 0xab15d70, id(MP2) type(Audio)
2009-11-07 21:01:45.903 AFD: Opened codec 0xbaf8b50, id(DVB_SUBTITLE) type(Subtitle)
2009-11-07 21:01:45.903 AFD: codec AC3 has 6 channels
2009-11-07 21:01:45.903 AFD: Opened codec 0xbaf8f10, id(AC3) type(Audio)
2009-11-07 21:01:45.929 Opening audio device 'default'. ch 2(2) sr 48000
2009-11-07 21:01:45.930 Opening ALSA audio device 'default'.
2009-11-07 21:01:45.964 NVP(0): Enabling Audio
2009-11-07 21:01:45.967 Opening audio device 'default'. ch 2(2) sr 48000
2009-11-07 21:01:45.967 Opening ALSA audio device 'default'.
```

---

### Post by ZedThou on 2009-11-07
What is your frontend setting for maximum channels? I've found it had to be Stereo rather than 5.1 or I couldn't get spdif passthrough. This is counterintuitive, but ok. Another person was having the same problem and required the same solution.

See the thread here
[http://ubuntuforums.org/showthread.php?t=1315557](http://ubuntuforums.org/showthread.php?t=1315557)

---

### Post by pootle1 on 2009-11-08
I'm already set stereo ZedThou, have just checked again to make sure as well.

;) pootle

---

### Post by pootle1 on 2009-11-08
I have just rebuilt an old PC with an abit NF7 motherboard, while it has no hope of handling HD video, it did used to handle 5.1 OK, and still does with karmic and myth 0.22.  This is with the same settings as on the new PC as described above.

Looks like it must be an alsa - driver issue.  I'll see if I can update alsa later on today.

---

