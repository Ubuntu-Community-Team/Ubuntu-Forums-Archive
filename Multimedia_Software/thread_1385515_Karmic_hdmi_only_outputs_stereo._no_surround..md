---
title: "Karmic: hdmi only outputs stereo. no surround."
date: 2010-01-19
forum: Multimedia Software
---

### Post by uncannybuzzard on 2010-01-19
i have an onboard hdmi output that works fine with karmic out of the box, including sound. however, i cannot successfully get it to output 5.1 surround to my receiver, only stereo.

i've attached screenshots of my available pulse audio devices. here's the aplay info:

```

ian@through ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
ian@through ~ $ aplay -L
front:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

```

---

### Post by sports.car.guy on 2010-01-19
Odds are your computer's HDMI is only capable of stereo. I hate to say it but most video cards are only 2.0 sound capable through HDMI. You have to specifically make sure the one you have is capable, or when buying a new video card make sure it has 5.1 if you want that capability.

Sorry to be the one to break that to you.

PS

I just noticed the pictures and with them along with your output, I can state without a doubt it is only stereo out only.

---

### Post by uncannybuzzard on 2010-01-19
if this is the case, the motherboard also has a optical audio port. if i picked up a cable for this, it would output to the analog devices listed in aplay -L correct? when i enable the analog device in the pulse audio manager, the different surround sound choices are available there.

---

### Post by sports.car.guy on 2010-01-19
> **uncannybuzzard said:**
> if this is the case, the motherboard also has a optical audio port. if i picked up a cable for this, it would output to the analog devices listed in aplay -L correct? when i enable the analog device in the pulse audio manager, the different surround sound choices are available there.


Sort of. The analogue devices are basically mappings for your speakers, the ones connected through the 2.5mm jacks that is. You would need analogue speakers connected to them. The digital out aka SPDIF, is a pass through connection. The audio you are listening to would have to be in AC3, PCM (aka Wave format), or converted to AC3 on the fly in order for it to come out the SPDIF connection.

Then you would want to consider the number of channels the audio is as well. I am assuming you are running pulseaudio and Ubuntu itself, not Kubuntu. Ubuntu and as far as I know all the derivatives of it except Kubuntu rely on pulseaudio for sound by default. Both upmixing and on the fly conversion of AC3 I am not too sure about in pulseaudio when it comes to using the SPDIF connection.

With Alsa there is a snippet you can put into your asound.conf for globally or asound.rc to enable AC3 transcoding on the fly for non PCM and PCM audio. The same is true for upmixing and such. Pulseaudio does upmixing internally and chooses the channels, how they are muxed, etc. You have no control over it either from what it looks like.

Are you trying to send the signal to an external 5.1 amplifier, like a home one?

---

### Post by uncannybuzzard on 2010-01-19
> **sports.car.guy said:**
> Sort of. The analogue devices are basically mappings for your speakers, the ones connected through the 2.5mm jacks that is. You would need analogue speakers connected to them. The digital out aka SPDIF, is a pass through connection. The audio you are listening to would have to be in AC3, PCM (aka Wave format), or converted to AC3 on the fly in order for it to come out the SPDIF connection.

Then you would want to consider the number of channels the audio is as well. I am assuming you are running pulseaudio and Ubuntu itself, not Kubuntu. Ubuntu and as far as I know all the derivatives of it except Kubuntu rely on pulseaudio for sound by default. Both upmixing and on the fly conversion of AC3 I am not too sure about in pulseaudio when it comes to using the SPDIF connection.

With Alsa there is a snippet you can put into your asound.conf for globally or asound.rc to enable AC3 transcoding on the fly for non PCM and PCM audio. The same is true for upmixing and such. Pulseaudio does upmixing internally and chooses the channels, how they are muxed, etc. You have no control over it either from what it looks like.

Are you trying to send the signal to an external 5.1 amplifier, like a home one?

yes, i just bought a sony bravia surround sound system. i'm looking to send the audio to that.

---

### Post by sports.car.guy on 2010-01-19
Yep, you can connect the SPDIF to the surround system. The thing is, you will need to enable on the fly trans-coding of your audio other then AC3, otherwise it won't be sent to your surround. I am assuming you are running pulseaudio and I am not too familiar with how it does it or if it even can. Not only that, I am not sure if it's internal up-mixing will work on the trans-coded AC3.

I know that you can set that up in Alsa, all of it. There is a bit of code as I said to add on the fly trans-coding and then you just need to make maps to take advantage of the trans-code. You do the up-mixing first then send it to the device you created with the code I am talking about.

AC3 you just tell it to pass through to the SPDIF in your media player. If it is 2 channel you can have the receiver up-mix it or decode up-mix and recode it in Alsa like I am talking about.

That is up to you

---

### Post by uncannybuzzard on 2010-01-20
> **sports.car.guy said:**
> Yep, you can connect the SPDIF to the surround system. The thing is, you will need to enable on the fly trans-coding of your audio other then AC3, otherwise it won't be sent to your surround. I am assuming you are running pulseaudio and I am not too familiar with how it does it or if it even can. Not only that, I am not sure if it's internal up-mixing will work on the trans-coded AC3.

I know that you can set that up in Alsa, all of it. There is a bit of code as I said to add on the fly trans-coding and then you just need to make maps to take advantage of the trans-code. You do the up-mixing first then send it to the device you created with the code I am talking about.

AC3 you just tell it to pass through to the SPDIF in your media player. If it is 2 channel you can have the receiver up-mix it or decode up-mix and recode it in Alsa like I am talking about.

That is up to you

i'm only really concerned about xbmc, which i have set up to bypass pulse audio and send to alsa directly (i.e., custom audio device plughw:1,3). i am assuming you could do something similar with the analog outputs specified in aplay -L and you mentioned something about modifying .asoundrc
how would i go about doing this exactly?

---

### Post by komasoftware on 2010-02-24
@sports.car.guy

I read that NVIDIA Ion is capable of sending out 5.1 surround sound under Windows but my sound preferences show the same - stereo only.

Any ideas ?

---

### Post by cozmicharlie on 2010-02-24
> **sports.car.guy said:**
> Sort of. The analogue devices are basically mappings for your speakers, the ones connected through the 2.5mm jacks that is. You would need analogue speakers connected to them. The digital out aka SPDIF, is a pass through connection. The audio you are listening to would have to be in AC3, PCM (aka Wave format), or converted to AC3 on the fly in order for it to come out the SPDIF connection.

Then you would want to consider the number of channels the audio is as well. I am assuming you are running pulseaudio and Ubuntu itself, not Kubuntu. Ubuntu and as far as I know all the derivatives of it except Kubuntu rely on pulseaudio for sound by default. Both upmixing and on the fly conversion of AC3 I am not too sure about in pulseaudio when it comes to using the SPDIF connection.

With Alsa there is a snippet you can put into your asound.conf for globally or asound.rc to enable AC3 transcoding on the fly for non PCM and PCM audio. The same is true for upmixing and such. Pulseaudio does upmixing internally and chooses the channels, how they are muxed, etc. You have no control over it either from what it looks like.

Are you trying to send the signal to an external 5.1 amplifier, like a home one?

Pulse audio should be capable of doing this.  Make sure you install the proper codecs.  Install the medibuntu repository and the Ubuntu Restricted Extras (from synaptic or apt-get) and you should be good to go.  You can also install the audio AC3 encoder called "Aften" - it is in synaptic (in the universe repository).    

sports.car.guy - thanks for the info in your posts.  I know how to get everything to work but not why so your post was very informative (and short).

komasoftware - you may want to start a new thread since your issue is probably not related to the original OP's issue.  You have a better chance of getting help for your specific problem.  I have a new Zotac Mag (ion) and I have the same issue in Windows 7 (only 2 ch via HDMI or SPDIF) and it is capable of 5.1.   I read on the Zotac forum it may be a problem with the NVIDIA drivers ([http://www.zotacusa.com/forum/index.php?/topic/2206-only-2-channel-through-hdmi/](http://www.zotacusa.com/forum/index.php?/topic/2206-only-2-channel-through-hdmi/)) - though it does state it is a conflict with the operating system.  I don't have Ubuntu installed on that machine yet so I don't know if it is also a problem in Ubuntu or specific to Windows 7. Post a new thread and I am sure some knowlegdable person will be able to help you.

---

### Post by komasoftware on 2010-02-25
@cozmicharlie: I wonder why I should start a new thread when "HDMI only outputs stereo, no surround" is EXACTLY the issue I am facing. And I read in more than one forum that NVIDIA ION is capable of sending this out on Windows 7.

The output of aplay -L is similar to what uncannybuzzard is seeing, surround is only reported on analog, not HDMI.

From what I have been reading on ALSA wiki ([http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)), I think this is the key :

"When referring to a digital output, setting it to "PCM Out" instructs the card to pass through the audio bytestream exactly as it is received from an application without applying any mixer settings. This is important, since a main point of having a digital audio output is to extract raw data from the PC to a device that may be more capable. Many people, apparently including hardware designers, my regard digital outputs purely as a noise-free version of analog outputs. However, the interface is really a separate (if unidirectional) interface. This is important to keep in mind when passing AC3 surround data streams through the card to an external decoder. In that case, modifications of the stream would make it completely invalid."

The "more capable" device is my new shiny Denon AV Receiver. Playing a DTS file for instance through HDMI does not light up DTS on my receiver, which IMO means that it has been mixed before being sent out. 

This is all guess work from my part, I still have to acquire a deeper understanding and I am looking for peers to help me figure this out.

K.

---

### Post by komasoftware on 2010-02-26
Here's the solution !!! :popcorn:

[http://forum.xbmc.org/showthread.php?t=59877](http://forum.xbmc.org/showthread.php?t=59877)

---

