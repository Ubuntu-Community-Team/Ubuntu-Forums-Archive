---
title: "Problem: 5.1 Audio, NVIDIA, HDMI Passthrough"
date: 2013-10-24
forum: Multimedia Software
---

### Post by vmnrao on 2013-10-24
Hi All,

I'm running 13.04, I have an NVIDIA GTX 670 Graphics card, and I'm trying to get 5.1 Audio over HDMI to my Yamaha receiver. So far I have not been successful. 

In sound settings, I see 3 different options for HDMI Audio (5.1), and when I select each of them and try to do the sound test, the front left and front right channels work fine, but nothing else (center, rear, sub). I've read many prior threads, but have found nothing hat has helped me so far. I've checked alsamixer and I see 4 SPDIFs on the NVIDIA, but the volume is stuck at 0 (not adjustable).

Any suggestions would be greatly appreciated!

Output of aplay -L is the following:
> 
aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, AD198x Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct sample mixing device
dmix:CARD=Intel,DEV=2
    HDA Intel, AD198x Headphone
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=2
    HDA Intel, AD198x Headphone
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=2
    HDA Intel, AD198x Headphone
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=2
    HDA Intel, AD198x Headphone
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 2
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 3
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Hardware device with all software conversions
sysdefault:CARD=DAC
    USB Audio DAC, USB Audio
    Default Audio Device
front:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    Front speakers
surround40:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    Direct sample mixing device
dsnoop:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    Direct sample snooping device
hw:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    Direct hardware device without any conversions
plughw:CARD=DAC,DEV=0
    USB Audio DAC, USB Audio
    Hardware device with all software conversions


---

### Post by vmnrao on 2013-10-25
Any suggestions on this would be greatly appreciated.

---

### Post by vmnrao on 2013-10-26
bump

---

### Post by warp99 on 2013-10-26
Silly question but do you have an SPDIF cable from the motherboard/soudboard connected to the video card?

---

### Post by warp99 on 2013-10-26
I did a little more digging and found out that card has a internal audio input for HDMI. This mini sound card is controlled by the Nvidia graphics card, not the sound chip on the motherboard:

>  Finally, newer NVIDIA GPUs such as the GeForce G210, GeForce GT220 or GeForce GTX 480 have added an internal HD audio codec. This is like having an internal sound controller built right into the graphics card. The NVIDIA internal HD audio codec can only be used to output to an HDMI (or DisplayPort) display. It does not support analog audio. If you require analog audio (i.e. for headphones or PC speakers), you must continue to use your PC's sound controller. The NVIDIA internal HD audio codec is superior to analog audio or S/PDIF signal. While S/PDIF is limited to compressed 5.1 multi-channel, the NVIDIA HD audio codec can support additional audio channels and also support more advanced audio formats used with Blu-ray movies. If you have a graphics card with internal NVIDIA HD audio codec, simply plug the HDMI audio cable from your graphics card to your HDTV and it will carry both video and audio. No other internal or external cables are needed from your sound card for audio.

[http://nvidia.custhelp.com/app/answers/detail/a_id/2593](http://nvidia.custhelp.com/app/answers/detail/a_id/2593)

So unless Nvidia supports this feature through its proprietary drivers the answer is you can't do this.

---

### Post by warp99 on 2013-10-27
A little bit more digging and I found this:

[ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)

You should be able to gain the information you need here to make it work.

---

### Post by vmnrao on 2013-10-27
warp99- wow thanks for all your replies. That last one looks very helpful- will get started on it and post back my findings. Thanks!

---

### Post by vmnrao on 2013-10-27
warp (and others),

Well, unfortunately, the nvidia guide is more focused on getting ANY audio out of your nvidia card via HDMI, versus getting 5.1 audio working specifically. I can get stereo audio out just fine, just not 5.1. And my sound settings show both Digital stereo and 5.1 via HDMI, but selecting 5.1 doesn't produce anything more than stereo. I was looking to see if anyone has 5.1 working via HDMI on their NVIDIA cards. I'm pretty sure there are people out there, just waiting for one of them to see this. I've spoken with NVIDIA tech support and they say 5.1 is supported via HDMI on their cards w/ the driver I'm using (313.30).

On a side-note, after reading some posts about pulse-audio's interaction w/ alsa possibly being the culprit, I tried uninstalling pulse-audio to see if that would help (it didn't) and, upon reinstallation of pulse-audio, the settings > sound > "test speakers" functionality in the GUI doesn't seem to work anymore. It used to work on Front R/L speakers, but nothing out of center/rear. Now it doesn't work on any of them. I am still getting stereo sound out through pulseaudio and alsa, just not this test speaker functionality via sounds settings GUI. Any tips there?

---

### Post by vmnrao on 2013-10-29
bump

---

### Post by Rawit on 2013-10-30
Did you check with a 5.1 video or audio file to see if you can get any sound from the other channels? I had problems with the Ubuntu sound test before, but not with the actual output in movies and games.

---

### Post by vmnrao on 2013-10-30
Rawit- yup, have tried VLC many times w/ files that play in Dolby Digital 5.1 via my Mac. The same files produce strange audio in Linux VLC via alsa or pulseaudio. Front L/R only, no vocals, makes me think maybe the channel mapping is messed up, but, based on other posts I've read, I think it would still show 5.1 in this case. Funny thing is aplay -D plays through my center channel.

---

### Post by Rawit on 2013-10-30
Have you tried this:

[FONT=Courier New]sudo gedit /etc/pulse/daemon.conf[/FONT]

Then make sure the following line is uncommented and set to 6

[FONT=Courier New]default-sample-channels = 6 [/FONT]

also uncomment and edit the following line to yes

[FONT=Courier New]enable-lfe-remixing = yes[/FONT]

---

### Post by vmnrao on 2013-11-02
> **Rawit said:**
> Have you tried this:

[FONT=Courier New]sudo gedit /etc/pulse/daemon.conf[/FONT]

Then make sure the following line is uncommented and set to 6

[FONT=Courier New]default-sample-channels = 6 [/FONT]

also uncomment and edit the following line to yes

[FONT=Courier New]enable-lfe-remixing = yes[/FONT]

Rawit- thanks for the helpful info. I did not have the modifications you listed above in my daemon.conf. However, performing the modifications did not solve my problem, or change it in any way. And I did reboot after making the changes. I still get stereo audio out of pulseaudio, and speaker-test only plays out of front left and front right. Again, aplay seems to play out of the center channel so I know it must be possible. I tried VLC playing via pulseaudio and alsa and content I know is in 5.1 does not get decoded as such. Any other ideas?

---

### Post by Yellow Pasque on 2013-11-03
I doubt it will fix the issue, but it's worth a try to test the latest sound driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

