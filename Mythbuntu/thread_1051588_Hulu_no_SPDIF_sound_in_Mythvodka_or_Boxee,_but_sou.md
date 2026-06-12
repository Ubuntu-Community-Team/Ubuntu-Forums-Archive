---
title: "Hulu: no SPDIF sound in Mythvodka or Boxee, but sound ok in Firefox"
date: 2009-01-26
forum: Mythbuntu
---

### Post by larsolav on 2009-01-26
I am using SPDIF optical sound on a 8.04 system. In Firefox, the flash video has audio from CNN, Comedy Central, Hulu, etc. However, I get no sound from Hulu in Mythvodka or Boxee. I also get no sound from Comedy central in Boxee. In Boxee sound works for example for CNN and the podcasts. I have seen some posts about it in the Boxee forum ( [http://forum.boxee.tv/showthread.php?t=3511](http://forum.boxee.tv/showthread.php?t=3511) , [http://forum.boxee.tv/showthread.php?t=4766](http://forum.boxee.tv/showthread.php?t=4766) ), and some of the recommended solutions may seem to destroy sound in Mythtv.  Some links say to remove pulseaudio ( [http://forum.boxee.tv/showthread.php?t=5005&page=3](http://forum.boxee.tv/showthread.php?t=5005&page=3) , [http://forum.boxee.tv/showthread.php?t=1133&page=2](http://forum.boxee.tv/showthread.php?t=1133&page=2) ). _Will removing pulseaudio mess up sound in MythTV?_

It was a bit difficult for me to get SPDIF working in Mythtv, so I definitely don't want to mess up MythTV!
Some of the ordeal on my audio problem is mentioned here. ([http://ubuntuforums.org/showthread.php?t=857898](http://ubuntuforums.org/showthread.php?t=857898))
After combining hints from the links following links I got SPDIF running through mythtv:
[http://www.mythtv.org/wiki/Intel_HD_Audio_-_Realtek_ALC88x](http://www.mythtv.org/wiki/Intel_HD_Audio_-_Realtek_ALC88x)
[http://ubuntuforums.org/showthread.php?t=32213&page=3](http://ubuntuforums.org/showthread.php?t=32213&page=3)

To get sound in flash videos in Firefox, such as Hulu, CNN, and Comedy central I added this ./etc/asound.conf file:
> pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
                }
}

This is my alsa info : 
aplay --version
> aplay: version 1.0.15 by Jaroslav Kysela <perex@perex.cz>
aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
aplay -L
> front:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

Does anyone know why I can hear the audio on some streams when playing using Firefox but not when using Mythvodka or Boxee?

I am very confused.......

---

### Post by larsolav on 2009-01-28
Okidokili,
I tried some troubleshooting with Mythvodka.
I started mythfrontend from a terminal to see the output it gives me in the terminal. I then started mythvodka and tried a Hulu stream. Something interesting showed up. Here is the output from the terminal after I select a stream:

> 2009-01-28 20:44:22.139 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/Nip/Tuck
2009-01-28 20:44:26.668 UIImageType::LoadImage() - Cannot find image: /var/tmp/mythvod/Smile…You're Under Arrest!
2009-01-28 20:44:57.594 Running Command: /usr/local/bin/hulu [http://www.hulu.com/watch/53235](http://www.hulu.com/watch/53235) /var/tmp/iplayerdump.partial.mov
2009-01-28 20:44:57.595 Buffer Required: 1000000
2009-01-28 20:45:13.040 TV: Attempting to change from None to WatchingPreRecorded
2009-01-28 20:45:13.043 DPMS Deactivated 
2009-01-28 20:45:13.061 AFD: Opened codec 0x847cc10, id(Unknown Codec ID) type(Video)
2009-01-28 20:45:13.061 AFD: codec MP3 has 2 channels
2009-01-28 20:45:13.062 AFD: Opened codec 0x83228c0, id(MP3) type(Audio)
2009-01-28 20:45:13.119 Opening audio device 'digital'. ch 2(2) sr 44100
2009-01-28 20:45:13.119 Opening ALSA audio device 'digital'.
ALSA lib pcm.c:2145: (snd_pcm_open_noupdate) Unknown PCM digital
[B]2009-01-28 20:45:13.126 AudioOutput Error: snd_pcm_open(digital): No such file or directory
2009-01-28 20:45:13.126 NVP: Disabling Audio, reason is: snd_pcm_open(digital): No such file or directory[/B]
2009-01-28 20:45:13.159 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-01-28 20:45:13.180 OSD Theme Dimensions W: 640 H: 480
2009-01-28 20:45:13.633 TV: Changing from None to WatchingPreRecorded
2009-01-28 20:45:13.633 Realtime priority would require SUID as root.
greedyhdeint: size changed from 0 x 0 -> 480 x 368
2009-01-28 20:45:13.736 Video timing method: USleep with busy wait
^[Signal: Interrupt
Ungrabbing XVideo port: 355
Segmentation fault 


I tried to search for some results, but can't really find any thing telling me what to do... how can I fix the "NVP: Disabling Audio, reason is: snd_pcm_open(digital): No such file or directory" error?

Thanks!!!

---

### Post by superm1 on 2009-02-07
Did you have any luck with this?  I'm running into it too...

---

### Post by larsolav on 2009-02-13
> **superm1 said:**
> Did you have any luck with this?  I'm running into it too...

Hi there superm1!
Sorry about the late reply. I thought I had email notification set up if someone replied to this thread, but I guess I don't...

Anyway, I did not figure it out. So I gave up... :( 

I used the Google until I was green. when searching the term "snd_pcm_open" I came across this site: [http://qnxcs.unomaha.edu/help/product/neutrino/audio/libs/snd_pcm_open.html]("http://qnxcs.unomaha.edu/help/product/neutrino/audio/libs/snd_pcm_open.html"). I don't really understand this page or the pages you get to when you click on the "contents" button in this link.

Do you have a problem with mythvodka or boxee as I do? I thought maybe it was my audio chip that was weird, so that is why I gave up. 

Do you know if doing:
```
sudo apt-get install esound
```
would mess with the audio in Mythtv? This boxee forum site suggested it as a possible fix for boxee: [http://forum.boxee.tv/showthread.php?t=1133&page=2]("http://forum.boxee.tv/showthread.php?t=1133&page=2")

I hope you were able to fix the problem. You have helped me out before with my Mythbuntu setup, and if anyone can figure it out, you must be the one!:p

---

### Post by superm1 on 2009-02-13
> **larsolav said:**
> Hi there superm1!
Sorry about the late reply. I thought I had email notification set up if someone replied to this thread, but I guess I don't...

Anyway, I did not figure it out. So I gave up... :( 

I used the Google until I was green. when searching the term "snd_pcm_open" I came across this site: [http://qnxcs.unomaha.edu/help/product/neutrino/audio/libs/snd_pcm_open.html](http://qnxcs.unomaha.edu/help/product/neutrino/audio/libs/snd_pcm_open.html). I don't really understand this page or the pages you get to when you click on the "contents" button in this link.

Do you have a problem with mythvodka or boxee as I do? I thought maybe it was my audio chip that was weird, so that is why I gave up. 

Do you know if doing:
```
sudo apt-get install esound
```would mess with the audio in Mythtv? This boxee forum site suggested it as a possible fix for boxee: [http://forum.boxee.tv/showthread.php?t=1133&page=2](http://forum.boxee.tv/showthread.php?t=1133&page=2)

I hope you were able to fix the problem. You have helped me out before with my Mythbuntu setup, and if anyone can figure it out, you must be the one!:p
Well my issue was with boxee.  I managed to actually get it working.  I just renamed my ~/.asoundrc and things worked.  I used to always need that for myth to work and mplayer and xine in concert, but for some reason it works without it now!

---

### Post by efolse on 2009-03-07
if I may suggest. with accessories, terminal, type alsamixer.  using the right arrow move to pcm and use the up arrow.  I worked for me.

---

