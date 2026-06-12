---
title: "HDMI and XBMC"
date: 2010-12-09
forum: Multimedia Software
---

### Post by sydbat on 2010-12-09
Not sure if anyone here can help. I have no problems with sound over HDMI. Even 5.1 surround works perfectly with VLC for DVD's.

However, I decided to try out XBMC for our HTPC. It seems to work great, except for the fact that it does not play DVD's with anything resembling surround sound. I have Googled and searched the XBMC forum (which I will likely sign up to and post my problem there too) with no joy. 

As I stated, complete digital sound over HDMI works perfectly on my 10.04 desktop / HTPC with NVidia GT 220. 

Having tested everything I can think of, I have found the potential problem - XBMC wants to use hw:03 as the sound default when playing digital content. My NVidia card only plays sound via hw:0,7. 

All I want to find out is  - what XBMC specific file I need to manipulate, and what to change, to get it to recognize the correct HDMI hardware port (using the audio settings while in XBMC only create errors).

So, has anyone else run into this problem with XBMC? If so, any solutions?

---

### Post by sydbat on 2010-12-10
I wonder if trying another HTPC software package might help...like Myth. Any other suggestions?

---

### Post by BULLIT22 on 2010-12-10
Hello,

See if this helps. In the XBMC preferences. change default sound to digital, Change both passthrough and default sound to hdmi. Hope it helps.

---

### Post by BULLIT22 on 2010-12-10
This may help as well,

[http://forum.xbmc.org/showthread.php?t=73247](http://forum.xbmc.org/showthread.php?t=73247)

Hope you get it sorted out.

---

### Post by sydbat on 2010-12-10
> **BULLIT22 said:**
> Hello,

See if this helps. In the XBMC preferences. change default sound to digital, Change both passthrough and default sound to hdmi. Hope it helps.Thanks. But I have tried that, and several other combos too.

And the XBMC folks have not been able to help so far either. Nice community over there.

---

### Post by BULLIT22 on 2010-12-10
Are you running the HDMI into a receiver? Or straight into the TV?

---

### Post by bogoliubov on 2010-12-10
I've had similar problems. But it was solved by choosing (or writing) the correct name in the XBMC sound config menu.

---

### Post by sydbat on 2010-12-10
> **BULLIT22 said:**
> Are you running the HDMI into a receiver? Or straight into the TV?TV then receiver. As I mentioned, 5.1 Dolby and DTS work perfectly in VLC, so it is definitely a config issue with XBMC.

> **bogoliubov said:**
> I've had similar problems. But it was solved by choosing (or writing) the correct name in the XBMC sound config menu.I have tried a bunch of combinations found via Google/XBMC forums. However, I might have mistyped something or not used the correct syntax. Can you provide the exact way you did it so I can give it another try??

---

### Post by BULLIT22 on 2010-12-10
This page may help with that config.

[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller)

Not sure what HW you are running. It may help though....

---

### Post by sydbat on 2010-12-10
> **BULLIT22 said:**
> This page may help with that config.

[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller)

Not sure what HW you are running. It may help though....I suppose you are correct! HDMI through NVidia GT 220.

I'll check the link.

---

### Post by BULLIT22 on 2010-12-10
Hope you get it going. Let us know what the outcome is.

---

### Post by sydbat on 2010-12-10
I will.

On the XBMC forum, they have asked for aplay -l and aplay -L. I'll post them here too, just in case.

aplay -l```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
aplay -L```
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=NVidia
    HDA NVidia, HDMI 0
    HDMI Audio Output
front:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
```

---

### Post by markast on 2011-01-03
Morning,
I am no Linux or XBMC expert but have been struggling with this over the last few days.

I had an on board HDMI connection from the onboard Nvidia 7100 and had added a GT220 and i just could not get the sound running through the HDMI (just to my 2 speaker TV) using either of the HDMI outputs.

I have since removed the GT220 and updated the Nvidia drivers and the 7100 seems to be doing fine, but while it had worked before i couldn't get the onboard HDMI working again.

I am still running  the Ubuntu 9.10 version of XBMC live installed to a HD so the menus may be a little different as i cant get 10.1 to play sound at present....

But if given sound works on hw:0,7 have you changed the sound device to custom and typed in hw:0,7 ? As i found out last night i needed to set the passthrough  to custom too and the same setting and then as i was running it just to my TV i had to unclick the option to say it was an AC3 device.
I have yet to find, but am looking for the config file to alter these settings on the command line...

I hope this kind of makes and maybe even helps!

Mark

---

