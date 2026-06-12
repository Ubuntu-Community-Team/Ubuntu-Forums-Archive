---
title: "Audacity recordings are slow"
date: 2013-09-14
forum: Multimedia Software
---

### Post by motorcity909 on 2013-09-14
Hi all

I've used Audacity to record streamed audio for many years.  A few weeks ago I recorded two programmes and when I listened to them on my iPod in the car they were clearly slow - it was like a throwback to a cassette Walkman with the batteries running down!

I've tried it again this morning and still the same.  I removed and reinstalled Audacity - still the same.

A thirty second sample MP3 can be heard here - [http://ubuntuone.com/1bOUYMEIicRFUZrChWBclU](http://ubuntuone.com/1bOUYMEIicRFUZrChWBclU) 

which, for comparison, is the opening thirty seconds of this BBC Radio 2 prog - [http://www.bbc.co.uk/programmes/b039d3jp](http://www.bbc.co.uk/programmes/b039d3jp)

The output from editing an existing (correct speed) audio file is absolutely fine.

Any assistance will be very much appreciated.

Cheers
Dave

---

### Post by motorcity909 on 2013-09-14
As a workaround, I've installed Audio-Recorder   [http://www.omgubuntu.co.uk/2011/03/audio-recorder-for-linux-easily-record-audio-streams-to-mp3](http://www.omgubuntu.co.uk/2011/03/audio-recorder-for-linux-easily-record-audio-streams-to-mp3) 

Seems to work absolutely fine, no sloooowness.

One criticism is that MP3s are only recorded at 32kbps and I can't find any way to change it.  Suppose that's okay for speech recordings but music would need to be higher - so would record in Wav format, then convert to a 192kbps MP3 afterwards.

But if anyone does have any clue about the Audacity slowness, it'll be great.

Cheers
Dave

---

### Post by ajgreeny on 2013-09-14
I had the same problem when using Lubuntu 12.04 on an old Acer Travelmate 2200 laptop.  The answer to that was to install pulseaudio in Lubuntu, which is not installed in the default OS, and use it as default on the system so that it was in control when recording and playing audacity recordings.

However, Xubuntu 13.04 already has pulse as default, as far as I'm aware, I'm pretty sure it was in my 12.04 installation, so I would have expected that to work fine for you, unless, of course, you have disabled it or removed it from your system.

I have just recorded a file to mp3 cd quality using my system and the (short) test recording I made shows as below when I use mediainfo on it
```
mediainfo rec-20130914-17\:07\:08.mp3 
General
Complete name                            : rec-20130914-17:07:08.mp3
Format                                   : MPEG Audio
File size                                : 144 KiB
Duration                                 : 12s 251ms
Overall bit rate mode                    : Variable
Overall bit rate                         : 95.3 Kbps

Audio
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Mode extension                           : MS Stereo
Duration                                 : 12s 251ms
Bit rate mode                            : Variable
Bit rate                                 : 96.0 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 142 KiB (99%)
``` ie better quality than you are getting, so perhaps you either need to change some configuration, or make sure you have all the appropriate gstreamer codecs.  However, as you can encode to mp3 already, I assume you must have all that is necessary for that, so I'm baffled as to why your mp3 is of such low quality.

---

### Post by tgalati4 on 2013-09-14
What are your default settings in audacity?  It seems to be a sampling speed difference.  Many streams are pushed at 22KHz, but when recorded at 44KHz and played back at 44KHz will resulted in 1/2 the speed.  So make sure your default speed is 22KHz in preferences.

---

### Post by motorcity909 on 2013-09-15
Thanks both for your replies.  I do have Pulse Audio, not disabled or removed.

I changed the sample rate in Audacity to 22000 and tried a test recording, still slow unfortunately.  

I've never changed that setting before and recordings have been fine - just checked some BBC Radio 4 recordings from mid-August - all done at 44100 and no slowness.

Out of interest, why would sample rate differences make any difference?  Isn't Audacity just meant to be recording any sound from my computer?  I remember years ago, when still on Windows, Audacity recordings had the occassional beep on them - mystified me for ages until I realised it was the Outlook email ping sound!

I don't do a vast amount of recording like this, just those documentaries/plays that can't be downloaded as podcasts anyway.

I can't find any config files for Audio-Recorder to change the mp3 bit-rate.

I think I'll just use Audio-Recorder in WAV format (file size will be bigger but I've got the space), then convert down to MP3 afterwards.

Cheers
Dave

---

### Post by tgalati4 on 2013-09-15
If you install *sox*, you can use the *play* command with switches to speed up or slow down audio.  

```
sudo apt-get install sox
man sox
```

See if you can figure out what the speed factor is.

---

### Post by osmoma on 2013-09-16
Hello [COLOR=#000000]Dave (motorcity909), and others.

About Audio-Recorder:
[/COLOR][COLOR=#000000]The audio profiles (encoders, bitrates, and other attributes) are hard-coded in the source code. You cannot change them during runtime.

Please study src/media-profiles.c and its [/COLOR][COLOR=#000000][FONT=UbuntuBeta Mono]DefaultProfiles[/FONT][/COLOR][COLOR=#000000][FONT=UbuntuBeta Mono][] [/FONT][/COLOR]structure:
[http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/media-profiles.c](http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/media-profiles.c)

In earlier versions of A.r we could simply edit the audio profiles (and their attributes) in the GConf-registry (by gconf-editor). 
But this hasn't been possible since the "[COLOR=#808080][FONT=UbuntuBeta Mono]libgnome-media-profiles" [/FONT][/COLOR]was removed from Ubuntu. GConf has also been replaced DConf (by dconf-editor).

Please give your comments on how to expose and program the media-profiles (audio settings, bitrates, etc) in A.r.
Some users seem to change the code (altering the vals in [COLOR=#000000][FONT=UbuntuBeta Mono]DefaultProfiles[][/FONT][/COLOR]) and recompile A.r from source. This is rather easy to do, but the application should provide a better solution.

Ref: gnome-media-profiles removed from Ubuntu.
[https://bugs.launchpad.net/audio-recorder/+bug/1121376](https://bugs.launchpad.net/audio-recorder/+bug/1121376)

Ref: Personalized non-system pipelines
[https://bugs.launchpad.net/audio-recorder/+bug/734395](https://bugs.launchpad.net/audio-recorder/+bug/734395)

Ref: Compiling A.r from source (instructions in INSTALL and README files).
[http://ubuntuforums.org/showthread.php?t=2165484&p=12756338#post12756338](http://ubuntuforums.org/showthread.php?t=2165484&p=12756338#post12756338)

**EDIT: It would be great if someone starts thinking ([SUP]developing)[/SUP] a NEW audio-recorder using QT/QML for Ubuntu-Touch (incl. **Ubuntu Phone, Tablet, PC, TV, etc[B]). 
[/B]GStreamer 1.0 has already been ported to Ubuntu-Touch platform!

I may not add new features to the current audio-recorder. It is a GTK+3 based application.  I merely recompile it for new versions of Ubuntu-desktop. And that's it.

Kindly
 Osmo (Moma) Antero
Palmela, Portugal.

---

### Post by motorcity909 on 2013-09-16
Hi Osmo

Many thanks for your great post.  To be honest, I'm not one for delving into source code so I shall be perfectly happy to use A-R recording Wav files, then convert them down to mp3 afterwards, either with Sound Convertor or Audacity.

Cheers
Dave

---

### Post by shantiq on 2013-09-17
or you can record to mp3 with sox so no need for conversion



 read here for settings  [from   ]("http://ubuntuforums.org/showthread.php?t=1805550")



> sudo apt-get install pavucontrol sox libsox-fmt-all




> rec   -C 256 nameyouwant.mp3


---

