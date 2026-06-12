---
title: "Ax1700 spdif"
date: 2009-05-09
forum: Multimedia Software
---

### Post by vapor0 on 2009-05-09
Does anyone out there own an Acer AX1700-E3751A with working spdif output? I've tried all kinds of tutorials, and couldn't get it to work. I ended up breaking my audio and having to reinstall. I don't want to have to do that again!

---

### Post by vapor0 on 2009-05-11
Bump

---

### Post by vapor0 on 2009-05-12
bump

---

### Post by vapor0 on 2009-05-15
Come on, please. I tried every online tutorial I could find, and totally wrecked my sound on my HTPC last time. I know someone out there knows how to do this.](*,)

---

### Post by xzero1 on 2009-05-15
Try this, it should at least play a 5.1 dvd:
 mplayer -ao alsa:device=spdif -channels 6 -ac hwac3 -aspect 16:10 dvd://

It works with the latest (SVN-r29274-4.3.3) mplayer and might need to be tweaked for older ones.

---

### Post by vapor0 on 2009-05-18
Ok, I'll give that a try. Thanks.

---

### Post by vapor0 on 2009-05-18
It says alsa: no sound device.

---

### Post by xzero1 on 2009-05-20
I don't have your soundcard but the tutorials should help. What is the output of aplay -l?

---

### Post by vapor0 on 2009-05-26
No, I don't think the tutorials will necessarily help, because I followed all those tutorials but only succeeded in borking my audio.
 
The output of aplay -l is:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by xzero1 on 2009-05-27
You aplay -l output says there is no digital (spdif) audio device installed. Does your soundcard driver support digital audio output? If this is a newer soundcard the answer may be no or not yet. You say that the tutorial has borked your soundcard. Which tutorial did you use that caused this and how do you think it happened?

---

### Post by vapor0 on 2009-05-27
The digital output shows in aplay -l, and in alsamixer when I compile the alsa packages from source, using the "auto" option. But there was never any sound coming out of the speakers, maybe because I could never get the digital output to unmute in alsamixer, or any other sound configuration tool. I also tried different asoundrc and asoundconf files, using the instructions of others using the same kind of audio driver. Another reason it might not be working is that I am using hdtv output. I tried the "Ultimate Ubuntu Multimedia Setup" or whatever it was called, and made all the suggested changes to PulseAudio, and all of the compile options for alsa.

---

### Post by xzero1 on 2009-05-27
For testing, if possible, I would not use your tv (some are designed to mute sound if there is no video).
Get back to the point where the digital device shows up (compile and install the packages as before). From a terminal, run alsamixer, there should be something like IEC958 output, unmute this by selecting the output and pressing "m" to toggle the mute on and off. Make sure pcm and master are also unmuted in the same way.  Run aplay -L, there should be your digital device listed here. As an example see below:

```
aplay -L
front:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI DAC/ADC
    Front speakers
rear:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    Rear speakers
surround40:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI 2nd DAC
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CMI8768,DEV=0
    C-Media CMI8768, C-Media PCI DAC/ADC
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
kdog@kdog-desktop:~/temp$ 

```Find the name of the digital device on the list. In my case it is "iec958". Now get some 'wav' file for testing or convert an mp3 file using ffmpeg: 

```
ffmpeg -i name.mp3  name.wav
```.
Now try to play the wav file to your digital device (in my case):

aplay -D iec958 name.wav

Do you hear any sound?

---

### Post by vapor0 on 2009-05-27
Alsamixer won't let me unmute it, although I can easily mute or unmute everything else.

---

### Post by xzero1 on 2009-05-27
Ok, follow this...
> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0says my device is card 0

> $ amixer controls
numid=1,iface=MIXER,name='Master Playback Volume'
numid=2,iface=MIXER,name='3D Control - Switch'
numid=3,iface=MIXER,name='PCM Playback Switch'
numid=41,iface=MIXER,name='PCM Playback Volume'
numid=4,iface=MIXER,name='PCM Capture Switch'
numid=6,iface=MIXER,name='Synth Playback Switch'
numid=5,iface=MIXER,name='Synth Playback Volume'
numid=7,iface=MIXER,name='Synth Capture Route'
numid=12,iface=MIXER,name='Line Playback Switch'
numid=11,iface=MIXER,name='Line Playback Volume'
numid=13,iface=MIXER,name='Line Capture Route'
numid=28,iface=MIXER,name='Line-In Mode'
numid=9,iface=MIXER,name='CD Playback Switch'
numid=8,iface=MIXER,name='CD Playback Volume'
numid=10,iface=MIXER,name='CD Capture Route'
numid=26,iface=MIXER,name='Mic Boost Capture Switch'
numid=21,iface=MIXER,name='Mic Boost Playback Switch'
numid=15,iface=MIXER,name='Mic Playback Switch'
numid=14,iface=MIXER,name='Mic Playback Volume'
numid=16,iface=MIXER,name='Mic Capture Switch'
numid=22,iface=MIXER,name='Mic Capture Volume'
numid=40,iface=MIXER,name='Mic-In Mode'
numid=24,iface=MIXER,name='Phone Playback Switch'
numid=23,iface=MIXER,name='Phone Playback Volume'
numid=25,iface=MIXER,name='PC Speaker Playback Switch'
numid=17,iface=MIXER,name='PC Speaker Playback Volume'
numid=19,iface=MIXER,name='Aux Playback Switch'
numid=18,iface=MIXER,name='Aux Playback Volume'
numid=20,iface=MIXER,name='Aux Capture Switch'
numid=32,iface=MIXER,name='IEC958 5V'
numid=31,iface=MIXER,name='IEC958 Copyright'
numid=34,iface=MIXER,name='IEC958 In Monitor'
numid=39,iface=MIXER,name='IEC958 In Phase Inverse'
numid=38,iface=MIXER,name='IEC958 In Select'
numid=30,iface=MIXER,name='IEC958 In Valid'
numid=33,iface=MIXER,name='IEC958 Loop'
numid=29,iface=MIXER,name='IEC958 Output Switch'
numid=27,iface=MIXER,name='Four Channel Mode'
numid=36,iface=PCM,name='IEC958 Playback Con Mask',device=2
numid=35,iface=PCM,name='IEC958 Playback Default',device=2
> $ amixer -c 0 cset numid=29 on
numid=29,iface=MIXER,name='IEC958 Output Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=onhere -c 0 is for card 0
get the idea?

Try the aplay -D.... command again on the wav file.
If still no sound what is the output of each amixer command?

Even if this stuff works, there seems to be a bug that you need to report (unmute in alsamixer).

Another thing to consider is if your computers bios has control of the digital output, that could explain a lot.

---

### Post by vapor0 on 2009-05-28
Hey, thanks a lot, man. I actually have SPDIF working now, by following [this tutorial]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

Btw, I was mistaken. It wasn't that I couldn't unmute it in alsamixer, it was that I couldn't turn it up. I guess that's normal, though. I don't know why it worked this time, maybe it was the --kernel option on the alsa compile.

The sound is only coming out in stereo, even though surround sound is turned up in alsamixer. Following [this tutorial]("https://help.ubuntu.com/community/SurroundSound") and changing /etc/pulse/daemon.conf resulted in a complete loss of sound, but I put the semi-colon back in front of the line, and it was fixed on reboot. (Stereo.) More research is necessary.

Still, I'm marking this one as SOLVED.:-({|=

---

### Post by vapor0 on 2009-05-28
"speaker-test -Dplug:surround51 -c6 -l1 -twav foo.wav" gives:
speaker-test 1.0.20

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 5440
Period size range from 32 to 2720
Using max buffer size 5440
Periods = 4
was set period_size = 1088
was set buffer_size = 5440
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.523167

But there is no sound. Maybe it's impossible unless you edit /pulse/daemon.conf, but that results in sound loss too.

---

### Post by xzero1 on 2009-05-29
> speaker-test -Dplug:surround51 -c6 -l1 -twav foo.wavSends sound through the analog outputs not spdif. 

For true 6 channel sound, the source must be encoded as such. Try the mplayer line from my earlier post on a 5.1 dvd. Here, the pre-encoded 6 channel signal is sent through spdif to be decoded by your 5.1 receiver.

---

### Post by vapor0 on 2009-05-29
Thanks, that works awesome. All six speakers have output.

Is there a way I can set up the computer to always use 5.1 when available?

---

### Post by xzero1 on 2009-05-29
> **vapor0 said:**
> Thanks, that works awesome. All six speakers have output.

Is there a way I can set up the computer to always use 5.1 when available?

Not with Jaunty's default pulse audio as far as I know. This might be possible with the new pulse audio.

---

### Post by vapor0 on 2009-05-30
Well, that's too bad, isn't it?:(

---

### Post by vapor0 on 2009-05-31
Ok, so another question, if you're still following this thread. Is it possible to pump sound out of all 5 speakers via SPDIF when there isn't true 5.1 available? Through rythmbox, for example?

---

### Post by xzero1 on 2009-05-31
[LEFT]The sound must be encoded first. There is an a52 alsa plugin you might look into but getting it to work in Jaunty with pulse might be difficult. This link might help:[ http://www.gentoo-wiki.info/HOWTO_Dolby_Digital_and_DTS#On-the-fly_Dolby_Digital_Encoding]("http://www.gentoo-wiki.info/HOWTO_Dolby_Digital_and_DTS#On-the-fly_Dolby_Digital_Encoding").
[/LEFT]

---

### Post by vapor0 on 2009-06-03
I think I'm going to try this. If I get it working, I'll let you know how I did it.

Thanks again.:D

---

### Post by redrecordplayer on 2009-07-02
Hey man, kinda out of topic. But I'm planning on buying that ACER AX1700. This is the computer that you have I think, did everything work fine on Ubuntu? Except for the sound of course. Thanks in advance.

---

### Post by jehozadakk on 2009-12-11
I know the post is a little old, but thought I'd reply in case you're still out there.  I am running an Acer 1700.  Its a decent, budget line PC with enough power to do most things better than average.  I have problems with compiz v-sync, but full screen video (overlay mode) works great and clear.  The laser-scribe drive was never able to work as a labeler, but as a dvd/cd burner its still great.  It runs 720p video well but struggles sometimes with a 1080p mkv file.  I use analog output for most sound, but for any DTS or DD sound (VCL movie player) my optical out works great.  Hooked up to a 52 inch Sharp with a 7.1 surround sound system, cordless keyboard and mouse and I'm in multimedia heaven.  Dual monitor set up works well too, one dvi and one hdmi.  I think most people would be very happy with ubuntu on this computer, but its wet my lips for something even better.

---

