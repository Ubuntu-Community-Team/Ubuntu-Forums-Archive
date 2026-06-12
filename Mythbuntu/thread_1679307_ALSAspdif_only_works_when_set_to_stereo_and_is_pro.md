---
title: "ALSA:spdif only works when set to stereo and is prologic, not digital 5.1"
date: 2011-01-31
forum: Mythbuntu
---

### Post by ubnewbie2 on 2011-01-31
I have an nvidia motherboard with spdif to my amp (see aplay -L output below) and I am trying to get mythtv recordings from digital TV to play with digital surround sound.

When I configure the frontend to use ALSA:spdif it only outputs sound if I set it to stereo.  The amp reports a prologic signal, only, being received from the mythtv box.  The 5.1 setting produces silence.

How can I get mythtv recordings to play back with digital surround?



```
aplay -L
default:CARD=NVidia
    HDA NVidia, ALC883 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output

```

---

### Post by BicyclerBoy on 2011-01-31
S/PDIF only supports discrete 2ch (up to 96KHz afaik) or matrix encoded multi-channel 5.1.
That only allows DTS & AC3 5.1.
Normally it also excludes the use of any volume control & mixers.

Prologic is just some analogue tricks with the stereo signals.

To get 5.1 over S/PDIF you can:
-  digital pass-thru of AC3 & DTS
-  encode on the fly to AC3 (a52 plug-ins in alsa)

The MythTV up-mix to 5.1 is discrete multi-channel & does not encode to AC3.
The alsa a52 allows volume & mixer controls (non-trival setup).

Real HD audio over HDMI is a different beast again ..it supports discrete multi channel LPCM

Does that make sense/explain..

---

### Post by ubnewbie2 on 2011-02-01
> **BicyclerBoy said:**
> S/PDIF only supports discrete 2ch (up to 96KHz afaik) or matrix encoded multi-channel 5.1.
That only allows DTS & AC3 5.1.
Normally it also excludes the use of any volume control & mixers.

Prologic is just some analogue tricks with the stereo signals.

To get 5.1 over S/PDIF you can:
-  digital pass-thru of AC3 & DTS
-  encode on the fly to AC3 (a52 plug-ins in alsa)

The MythTV up-mix to 5.1 is discrete multi-channel & does not encode to AC3.
The alsa a52 allows volume & mixer controls (non-trival setup).

Real HD audio over HDMI is a different beast again ..it supports discrete multi channel LPCM

Does that make sense/explain..

Yes, I see what you're saying.  I just checked and I do have the passthru to spdif ticked for both AC3 and DTS.  The passthrough device is set to ALSA:iec958:{ AES0 0x02 }  - the choices are different to the audio output device selection, so is this correct?   

Still if I change the max audio channels to 5.1 I get silence, it only works on stereo.

---

### Post by BicyclerBoy on 2011-02-01
Disclaimer: Not using mythbuntu but MythTV 0.24.
But I think your settings are correct, much same as me.

IMO Stereo is best left as is, AC3 5.1 is best down-mixed in the AV receiver.
Down-mix is broken in most linux audio apps.

Do you have the "up-convert stereo to 5.1 surround" selected with 5.1 speaker config ?
That may be why..
It does not work with 5.1 up-convert because you do not have 5.1 digital pass thru' device..that would be HDMI or analogue 5.1 outputs

S/PDIF is stereo + digital pass thru' over-ride.

So play a DVD or TV recording with DTS/AC3 5.1..that's the only (easy) way to get 5.1 over S/PDIF..

The hard way is to use alsa modules plug-in a52 (AC3) encoder then all your multi-channel audio, real or psuedo can be output matrix encoded AC3.

---

### Post by ubnewbie2 on 2011-02-01
> Do you have the "up-convert stereo to 5.1 surround" selected with 5.1 speaker config ?
That may be why..

Where's that setting?  I can't find it.

> So play a DVD or TV recording with DTS/AC3 5.1..that's the only (easy) way to get 5.1 over S/PDIF..

The hard way is to use alsa modules plug-in a52 (AC3) encoder then all your multi-channel audio, real or psuedo can be output matrix encoded AC3. 

I am a bit confused in this area.  These are digital TV recordings and I thought they all used AC3 (here in Australia), so as far as I can see I AM playing "a DVD or TV recording with DTS/AC3 5.1"

---

### Post by BicyclerBoy on 2011-02-01
I using MythTV 0.24 so the audio config has changed..So can't quite remember.

Your digital OTA dvb stuff is likely same as NZ so mpeg2-ts mpeg4/10 H264AVC with AAC & maybe AC3. (AAC likely LOAS LATM AAC).

In NZ
AFAIK 2ch AAC stream must be present.
To date all the AAC is 2ch but it could be 5.1 6.1 etc..
Only some broadcasters have choosen to use extra AC3 stream.

Only US has to have AC3 digital TV (because DD sponsered the university report).

Maybe your digital pass thru' is broken.
Myth 0.23 from memory...
Must turn off internal volume control, no up-mixer.

Note: correct some errors previous.
DTS is 5.1 discrete encoded  
DTS-ES can be 6.1 discrete or matrix.

But I do not know of any DTS encoder for linux/alsa so not much use.

---

### Post by BicyclerBoy on 2011-02-08
I need to correct the previous about MythTV & AC3 encoding...

MythTV 0.24 (+ fixes only AFAIK) has AC3 encoding built in..
So you can have volume control, up-mixing & S/PDIF multi-channel audio..

I believe you need 0.24+fixes, this is available in Aussie 3rd party ppa.

---

### Post by nickrout on 2011-02-08
You need to update to 0.24, use mythbuntu repos (google it).

---

### Post by ubnewbie2 on 2011-02-08
> **nickrout said:**
> You need to update to 0.24, use mythbuntu repos (google it).


Thanks for the info.  I'll start planning the upgrade.

---

