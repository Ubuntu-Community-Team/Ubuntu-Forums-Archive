---
title: "Attempted SPDIF passthrough. No joy."
date: 2009-07-31
forum: Mythbuntu
---

### Post by AKADAP on 2009-07-31
I attempted to follow these instructions: [http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto)

All I ever got when attempting SPDIF pass through is noise.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I'm trying to use the SPDIF output, not the HDMI output, so I am attempting to use card 0, device 1.

I tried a bunch of variations of the /etc/asound.conf file. The last thing I tried was this:
```
  pcm.!default {
     type hw
     card 0
     device 1
  }
  pcm.!default {
     type plug
     slave {
        pcm "hw:0,1"
        format S32_LE
     }
  }
  pcm.!default {
     type plug
     slave.pcm "iec958"
  }
  pcm.!default {
     type plug
     slave.pcm "spdif"
  }

```
Originally, it did not exist.
When I went back to the original settings, I first left this file in place, but although other audio was working, mythTV audio volume was so low as to be incomprehensible.
Deleting that file got me back to where I was: weak but audible sound.

Since the wiki I tried to use does not work, what do I really need to do to get audio pass through from MythTV?

---

### Post by AKADAP on 2009-08-01
Should I take the lack of response to mean that getting spdif passthrough to work is impossible?

---

### Post by yonkiman on 2010-02-18
> **AKADAP said:**
> Should I take the lack of response to mean that getting spdif passthrough to work is impossible?

Spdif passthrough is possible - my Mythbuntu 9.10 and 8.04 had it.

But then I hosed something, and now I don't have it.  I've been trying off and on for months to get it back.

I think the lack of response is because this is really, really hard to troubleshoot.  At least that's been my experience.  For the last month I've just been hoping it gets fixed with one of the upgrades.    Maybe 10.04...

Good luck.

---

### Post by ktmom on 2010-02-18
You don't indicate what hardware you are dealing with or which Mythtv install.  The SPDIF is the only output I have ever used in Mythbuntu 9.04 and 9.10

My hardware is an Asus A8N SLI Premium with onboard SPDIF, Realtek ALC850 chip.

Not likely to be tons of help, but on my 64-bit 9.10 Mythbuntu install *all* I had to do was the audio system setup (frontend>settings>setup>general>page 4) as depicted in the attached MythtvAudioSystem.jpg image and on the next page uncheck  "use internal volume controls".  Then from the command line > alsamixer and page to the right and find the IEC958 toggle and unmute it using the "m" key. When muted it is a grey box with MM and a green box with 00 displayed when unmuted (see attached image).

I remember "fighting this with all sorts of frustration back for the 9.04 Mythbuntu install and finally - after a reinstall to get started right, ensuring the frontend was  configured (that version required the speaker setting to be stereo and not 5.1 due to a bug as I recall) and then unmuting the IEC958 in Alsa mixer, I was set.  This is similar to what the AllensDigitalAudioHowto link describes, but I ignored all of the other steps and kept it simple.

---

### Post by ian dobson on 2010-02-18
Hi,

I have SDPIF passthrough (on-board Audio -> NVidia 9600 graphic card -> HDMI to sony TV) working on my MythTV frontend.

Took abit of work it get it going but it's worth it.

When I get about of time (maybe over the weekend) I'll document how I've set it up.

Regards
Ian Dobson

---

### Post by toorima on 2010-02-19
My .asoundrc that I've been using since the very first version of mythbuntu looks like this

pcm.ice1724 {
    type hw
    card 0
}

pcm.!iec958 {
    type plug
    slave.pcm "hw:0,1"
}

pcm.!default {
    type plug
    slave.pcm "hw:0,1"
}

ctl.ice1724 {
    type hw
    card 0
}

the .asoundrc file should be in the home directory of the user you run mythtv with.

Hope its any help

---

### Post by AKADAP on 2010-02-19
> **ktmom said:**
> You don't indicate what hardware you are dealing with or which Mythtv install.  The SPDIF is the only output I have ever used in Mythbuntu 9.04 and 9.10

My hardware is an Asus A8N SLI Premium with onboard SPDIF, Realtek ALC850 chip.

Not likely to be tons of help, but on my 64-bit 9.10 Mythbuntu install *all* I had to do was the audio system setup (frontend>settings>setup>general>page 4) as depicted in the attached MythtvAudioSystem.jpg image and on the next page uncheck  "use internal volume controls".  Then from the command line > alsamixer and page to the right and find the IEC958 toggle and unmute it using the "m" key. When muted it is a grey box with MM and a green box with 00 displayed when unmuted (see attached image).

I remember "fighting this with all sorts of frustration back for the 9.04 Mythbuntu install and finally - after a reinstall to get started right, ensuring the frontend was  configured (that version required the speaker setting to be stereo and not 5.1 due to a bug as I recall) and then unmuting the IEC958 in Alsa mixer, I was set.  This is similar to what the AllensDigitalAudioHowto link describes, but I ignored all of the other steps and kept it simple.

Wow, 6 months of nothing, then I finally start getting some response. I was sure this thread was dead.

I just attempted what you suggested. When I switched from stereo to 5.1, I got silence, go back to stereo I get sound again. IEC958 was already enabled.

I'm using the motherboard audio on an Asus P6T Delux. The video card has an HDMI output, but I can't use digital audio through that because I have nothing do decode that.

---

### Post by AKADAP on 2010-02-19
I went through that wiki again, it appears that it has been updated in the last six months.

I now have something working, but I'm not sure what.

I tried creating an asound.conf file with this in it: 
   pcm.!default {
       type hw
       card 0
       device 1
   }

but I still only got silence.

so I replaced it with:
  pcm.!default {
     type plug
     slave {
        pcm "hw:0,1"
        format S32_LE
     }
  }

The wiki is unclear if I should have replaced the first, or just added the second. I just did a replacement.
The wiki also neglects to mention that after changing this file, one must run "sudo /etc/init.d/alsa-utils restart" before it will take effect.

Anyway, once this was done, I now get sound when I select 5.1. What is confusing me is that stations that should be showing "Pro Logic" on my receiver are showing "Dolby D". In fact most stations are showing "Dolby D". I found one showing suround 6.1, but I did not hear any sound from the surround speakers.
I was unable to find anything on at this hour that had full surround sound, so I have no idea if this is working yet, I'll have to wait until prime time to check.

---

### Post by AKADAP on 2010-02-19
I did a bit more testing.
I found a station that was broadcasting surround on a different tuner, then went to the MythTV box and verified that I was getting surround on that station.

So, I am FINALLY (after more than a year) getting surround through the optical cable to my receiver.

A bit more experimenting shows that the output of the external tuner, and the MythTV match except when the tuner is receiving stereo audio. Somehow, MythTV is turning stereo into Dolby Digital.

---

### Post by AKADAP on 2010-02-19
Turning off the "up convert stereo to 5.1" checkbox got the two systems to match their audio behavior.

---

### Post by yonkiman on 2010-02-19
> **AKADAP said:**
> So, I am FINALLY (after more than a year) getting surround through the optical cable to my receiver.

Yay!  Now you are giving me new hope!  I've also only been able to get stereo sound through my optical output since I lost 5.1 sound a few months ago.

One question for you and anyone else watching this thread:  Does
[INDENT]speaker-test speaker-test -Dplug:iec958 -c6 -t wav -f40[/INDENT]
give you sound out of all 6 channels?  All I get is Front Left and Front Right - the others are silent.

I figure that until speaker-test works, there's no point in messing with  Myth settings, since if speaker-test isn't working my alsa config is fundamentally hosed.  Is that correct reasoning?

Here's my aplay -l output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and aplay -L:
```
null
    Discard all samples (playback) or generate zero samples (capture)
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

in case anyone has any ideas.  I tried the above-mentioned 
```
pcm.!default {
type plug
slave {
pcm "hw:0,1"
format S32_LE
}
}
```
in /etc/asound.conf, but it had no effect.  Nothing I've ever done with .asoundrc or asound.conf has ever seemed to have an effect, though I wonder if the files are in the right directory - there seem to be a lot of places for them depending on which FAQ/wiki you read...

---

### Post by AKADAP on 2010-02-19
> **yonkiman said:**
> Yay!  Now you are giving me new hope!  I've also only been able to get stereo sound through my optical output since I lost 5.1 sound a few months ago.

Don't get your hopes up too soon. The sound stopped working with MythTV shortly after I posted.
I watched a show or two, shut down MythTV, did some web browsing (yes I viewed some videos, and the sound worked for them), went back to MythTV to watch a recording, and got no sound. Tried live TV, still no sound. logged out & back in, no sound. Reboot, no sound. Other sounds are working, just not MythTV. I tried setting back to sterio, and still no sound. The only thing left is that .conf file I added, so I must start messing with that.

> 

One question for you and anyone else watching this thread:  Does
[INDENT]speaker-test speaker-test -Dplug:iec958 -c6 -t wav -f40[/INDENT]
give you sound out of all 6 channels?  All I get is Front Left and Front Right - the others are silent.

I get the same.
> 
I figure that until speaker-test works, there's no point in messing with  Myth settings, since if speaker-test isn't working my alsa config is fundamentally hosed.  Is that correct reasoning?

No. What I am attempting is MythTV pass through, what the sound test is attempting is dolby digital encoding, NOT the same. What MythTV has is already encoded for surround. so there are no licensing problems, but you need a license to encode dolby digital (or any other multi (more than 2) channel audio) onto SPDIF. When SPDIF was defined they were very careful to exclude any free multi-channel encoding schemes. They did this to ensure they got paid.
> 
Nothing I've ever done with .asoundrc or asound.conf has ever seemed to have an effect, though I wonder if the files are in the right directory - there seem to be a lot of places for them depending on which FAQ/wiki you read...
There are really only two places /etc/asound.conf if you want the settings to apply to everyone or ~/.asoundrc if you only want them to apply to yourself.

make sure you run:
sudo /etc/init.d/alsa-utils restart
after making a change to those files to ensure they take effect.
I suspect that /etc/asound.conf is a better place, because I'm not sure that mythTV always runs as you, it may sometimes on some systems run as mythuser

---

### Post by AKADAP on 2010-02-19
I just ran
sudo /etc/init.d/alsa-utils restart
and now I have sound again. I did not change my /etc/asound.conf since the last time I had it working. Don't know why restarting it got it working again.

---

### Post by yonkiman on 2010-02-19
> **AKADAP said:**
> What I am attempting is MythTV pass through, what the sound test is attempting is dolby digital encoding, NOT the same. What MythTV has is already encoded for surround. so there are no licensing problems, but you need a license to encode dolby digital (or any other multi (more than 2) channel audio) onto SPDIF.

Wow.  I believe all that - it makes total sense - but it also seems to make the speaker-test utility INCREDIBLY misleading - it will NEVER work for SPDIF except for LF and RF channels.  It seems like there should be a warning when you are using it to test digital channels that it will NEVER send out a multichannel signal.  

That clears up a ton, though - thanks!

> There are really only two places /etc/asound.conf if you want the settings to apply to everyone or ~/.asoundrc if you only want them to apply to yourself.

That also clears up a lot.

> make sure you run:
sudo /etc/init.d/alsa-utils restart
after making a change to those files to ensure they take effect.
I suspect that /etc/asound.conf is a better place, because I'm not sure that mythTV always runs as you, it may sometimes on some systems run as mythuser

My alsa-utils file is not in /etc/init.d/.  It's in my path in /sbin/, so I can make the restart work with just "sudo alsa-utils restart".  Is the fact that it's not in /etc/init.d/ a sign of a wonky installation?  Should I worry about it?

Final question:  When I "sudo alsa-utils restart", it restarts with S/PDIF muted, so I have to go into alsamixer to unmute it.  Is there a way to force the default for S/PDIF to be unmuted?

Thanks for all your help!  I think the 5.1 is working now - just have to find some multichannel material to playback now...

-Fred

---

### Post by AKADAP on 2010-02-19
> **yonkiman said:**
> Wow.  It seems like there should be a warning when you are using it to test digital channels that it will NEVER send out a multichannel signal.

This is only true of SPDIF. If you have an analog hookup, (4 stereo cables between your computer & receiver) it does multichannel just fine.
> 
My alsa-utils file is not in /etc/init.d/.  It's in my path in /sbin/, so I can make the restart work with just "sudo alsa-utils restart".  Is the fact that it's not in /etc/init.d/ a sign of a wonky installation?  Should I worry about it?

I have no idea. I'm using Ubuntu 9.10 that has been upgraded multiple times to get there. My copy if alsa-utils is in the /etc/init.d directory and not in the path.
> 
Final question:  When I "sudo alsa-utils restart", it restarts with S/PDIF muted, so I have to go into alsamixer to unmute it.  Is there a way to force the default for S/PDIF to be unmuted?

This I also don't know. On my system it is not muted.
> 

Thanks for all your help!  I think the 5.1 is working now - just have to find some multichannel material to playback now...

-Fred

Good to hear.

---

### Post by AKADAP on 2010-02-21
The sound is extremely unstable. Sometimes it works, sometimes it doesn't.

I have not yet figured out what causes it to go away, nor have I found a reliable way to get it back.

I have recently added

  ctl.!default {
     type hw
     card 0
  }

to the /etc/asound.conf file.
This was the last change I did before the sound started working again, but I have no faith that that is what caused it to start working again.

---

### Post by AKADAP on 2010-02-22
> **AKADAP said:**
> The sound is extremely unstable. Sometimes it works, sometimes it doesn't.

I have not yet figured out what causes it to go away, nor have I found a reliable way to get it back.

I have recently added

  ctl.!default {
     type hw
     card 0
  }

to the /etc/asound.conf file.
This was the last change I did before the sound started working again, but I have no faith that that is what caused it to start working again.

That definitely did not fix it, still having random sound outages that usually, but not always, can be fixed by running:

sudo /etc/init.d/alsa-utils restart.

At this point, I'm not even sure /etc/asound.conf is necessary.

---

### Post by AKADAP on 2010-02-22
I have just proven to myself that the /etc/asound.conf file is in fact necessary.

My current file contains:
```

  pcm.!default {
       type hw
       card 0
       device 1
   }

  ctl.!default {
     type hw
     card 0
  }

```

I'm not sure the "ctl" section is required, but I am sure the "pcm" section is.

---

### Post by yonkiman on 2010-02-22
I'm still following, but I'm afraid I don't have any ideas to offer.  My 5.1 has been working pretty reliably (except for the occasional glitch that makes my receiver go silent for a second or two while it resyncs - usually when under heavy CPU load) since you helped me understand hot the heck this is all supposed to work.

Good luck!

---

### Post by pootle1 on 2010-02-23
I had 2 front ends, the one with the intel sound card I spent many, many hours trying to get working properly over SPDIF (for tv, dvd and web video, with stereo and multichannel.  I could never get everything working.

In the end I gave up and bought an nvidia chipset motherboard, and had it all working in 30 minutes.  It did stop a couple of weeks ago after an update, but I found something in the update had muted the spdif output in alsamixer, so it was easily fixed once I found it.

And yes, speaker-test only works with analogue outputs and stereo spdif, that sent me down a rabbit hole for a while until I realised.

---

### Post by nickrout on 2010-02-23
> **pootle1 said:**
> I had 2 front ends, the one with the intel sound card I spent many, many hours trying to get working properly over SPDIF (for tv, dvd and web video, with stereo and multichannel.  I could never get everything working.

In the end I gave up and bought an nvidia chipset motherboard, and had it all working in 30 minutes.  It did stop a couple of weeks ago after an update, but I found something in the update had muted the spdif output in alsamixer, so it was easily fixed once I found it.

And yes, speaker-test only works with analogue outputs and stereo spdif, that sent me down a rabbit hole for a while until I realised.

There are test ac3 and dts files floating around the net, which can be used with mplayer or other software to test your system.

One I found was all in german, and I don't really know my links from my rechts.

---

### Post by tomeq on 2010-05-11
I'm having the same problem with the same hardware here. Tried tons of tricks without success. 

Funniest thing is that I get sound only whenever I open "Audio preferences" panel on Gnome  :) It works then. It works even after closing the panel but until I seek through a movie (using VLC for example).

So, to get any 5.1 audio working (no matter, ac3 or dts) I have to open Audio Preferences panel. It triggers the audio! 

Anyway it is unstable. It crashes my amp. I'm getting speakers indicator constantly flashing which means "signal-no signal-signal-no signal".

---

### Post by AKADAP on 2010-05-11
Updating to 10.04 broke the "sudo /etc/init.d/alsa-utils restart" method of getting sound working since alsa-utils was removed.

I did find that opening the alsa mixer and toggling the mute for the main volume control on and off got the sound working again.

---

### Post by tomeq on 2010-05-12
> **AKADAP said:**
> Updating to 10.04 broke the "sudo /etc/init.d/alsa-utils restart" method of getting sound working since alsa-utils was removed.

I did find that opening the alsa mixer and toggling the mute for the main volume control on and off got the sound working again.

Anyway all of this is really pathetic..I'm more than tired with searching for solution. Is there any official bugreport/workaround? Is this hardware specific (Intel HDA) or software? 

I know that trying to get sound output via Pulseaudio doesn't work too. It outputs only stereo. Someone filled a bug report but no reaction at all.

---

### Post by AKADAP on 2010-05-12
> **tomeq said:**
> Anyway all of this is really pathetic..I'm more than tired with searching for solution. Is there any official bugreport/workaround? Is this hardware specific (Intel HDA) or software? 

I know that trying to get sound output via Pulseaudio doesn't work too. It outputs only stereo. Someone filled a bug report but no reaction at all.

If you follow the mailing lists, you will find that they are working on a complete rewrite of the audio for MythTV. I suspect that is why there is no interest in fixing bugs in code they plan to scrap anyway.

---

### Post by winewood on 2010-05-17
I recently worked out a solution to get my SPDIF passthrough to work.
 
My SPDIF was hardwired from the motherboard. However due to settings and a missing .asoundrc file it wasn't able to play.
 
To adjust settings the EASIEST way I have found was to bring up VLC media player and play and .mpg that you just recorded in mythtv. While its playing, bring up a terminal window and type alsamixer. This will allow you to see results of changes as you do them.
I turned off any external mixer, set to 2 channel (I still have 5.1 going to my box), I set SPIDF P to PCM, and lowered the volume to -0-, unmuted SPDIF, and turned the unnecessary channels to mute (m). While testing I found as I added volume to some options it decreased my volume and degraded my output. 
 
The only thing I have in my .asoundrc is as follows, and I derived the card and device ID from my ' aplay -l ' command.
```
winewood@mythtv:~$ cat .asoundrc
pcm.!default {
        type hw
        card 0
        device 0
}
winewood@mythtv:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
aplay -L
 
iec958:CARD=ICH,DEV=0
    Intel ICH, Intel ICH - IEC958
    IEC958 (S/PDIF) Digital Audio Output

 

```
 
I how have ALSA:Default set in Myth with 5.1
Under that, upgrade to 5.1 is not checked, Digital output device: default while DTS and DD have checkmarks

---

