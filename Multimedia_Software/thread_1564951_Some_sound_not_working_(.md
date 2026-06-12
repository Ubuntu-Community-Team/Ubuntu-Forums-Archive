---
title: "Some sound not working :("
date: 2010-08-31
forum: Multimedia Software
---

### Post by thirddeep on 2010-08-31
So, yet another sound problem.  I have read the "Comprehensive Sound Problem Solutions Guide" and it did solve some, but not all my sound problems.

Working : mp3 / ogg / test button from kde control settings
Not working : any of my games (gish / hedgewars / chromium / world of goo ...) and youtube.

I have checked that alsamixer has everything set to maximum.

Here is some of my system settings :

OS : Ubuntu 10.04.1
GUI : KDE
aplay -l output :

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any and all help would be much appreciated :-)

Thd.

---

### Post by thirddeep on 2010-08-31
Well, this board seems to move rather fast.

Surely someone must know the answer to such a simple question ? :-)

---

### Post by Yellow Pasque on 2010-08-31
Are you running Pulseaudio? It sounds like Phonon/KDE is grabbing the ALSA device directly and locking everything else out.

---

### Post by thirddeep on 2010-08-31
How do I check if I am running pulseaudio ?

Looking at the process tree, it certainly seems like it : 

```
thd       1598     1  1 19:06 ?        00:01:17 /usr/bin/pulseaudio --start --log-target=syslog
thd       1627  1598  0 19:06 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
```

---

### Post by tripmix on 2010-08-31
I'm gonna suggest that some of the things you run are trying to output to a device you are not using, a similar issue on my box causes flv files and some others not to output sound through HDMI in the xbmc built in player. To test you can try to run "mplayer -ao alsa:device=hw=0.3 filename" where 3 is the part of the device you want to output to. In your case 3 is hdmi 2 is digital and 1 is analog, analog would be the speakers built in to your computer digital if you pass it to an external receiver trough spdif or 3 minijacks or something and hdmi is obviously hdmi (your tv or whatever).

Edit: I just noticed that on your system to output to hdmi the device is 1.3 not 0.3 as it seems to be two separate devices.

---

### Post by thirddeep on 2010-08-31
Right,

mplayer -ao alsa:device=hw=0.1 how_do_you_do.ogg -- This works fine.
mplayer -ao alsa:device=hw=0.2 how_do_you_do.ogg -- No audio, mplayer is not complaining.
mplayer -ao alsa:device=hw=1.3 how_do_you_do.ogg -- No audio, mplayer is not complaining.

Thd.

p.s.
Don't bash Roxette :-)

---

### Post by tripmix on 2010-08-31
You have probably looked at System Settings>Multimedia in kde, you'll notice that it can be configured to use different devices for different types of applications like video, music or games. My guess was that games for example was configured to use 1.3 which you don't have plugged in when it should be using 0.1. mplayer should not be giving any errors as it is outputting the audio correctly, so if you connect your hdmi to a tv it should provide sound trough your tv speaker when using 1.3 but not the PC. It's just a guess though and your issue might be something completely different like a missing codec or something.

PS: Who is Roxette? The band?

EDIT: by the way the missing codec suggestion was just stupid, thats not it so don't bother investigating that, it was just the first thing that came too mind. I don't have any games to test with but I'm installing one now just to see if I can reproduce the issue as I have similar hardware. I doubt I can though so don't hold your breath.

---

### Post by thirddeep on 2010-08-31
Yes, it's a band :-)

Any case, under Audio Output (top level) I have the analogue output at the top.  The same goes for all the subsections, including games.

Thd.

---

### Post by tripmix on 2010-08-31
Do the games you have produce any output pertaining to sound when you launch them from a terminal? I couldn't reproduce the problem as we expected but it gave a lot of data on my sound setup when running from a terminal, does yours produce any errors? If so post them.

---

### Post by thirddeep on 2010-09-01
Ok, let's take chromium-bsu and see what it does.

So, from command line, it just launch like normal plays fine, but there is of course no sound.  Looking at the terminal for any output, none.

Looking at the man page, we can run chromium in debug mode.  The only part pertaining to sound is as follow :

```
AudioOpenAL::initSound() begin...
-OpenAL-----------------------------------------------------
Vendor     : OpenAL Community
Renderer   : OpenAL Soft
Version    : 1.1 ALSOFT 1.12.854
Extensions :
AL_EXTX_buffer_sub_data         AL_EXT_DOUBLE                   
AL_EXT_EXPONENT_DISTANCE        AL_EXT_FLOAT32                  
AL_EXT_IMA4                     AL_EXT_LINEAR_DISTANCE          
AL_EXT_MCFORMATS                AL_EXT_MULAW                    
AL_EXT_MULAW_MCFORMATS          AL_EXT_OFFSET                   
AL_EXTX_sample_buffer_object    AL_EXT_source_distance_model    
------------------------------------------------------------
AudioOpenAL::setSoundVolume(0.900000)
Music volume = 0.500000
alAttenuationScale == 0. Kludge it.
AudioOpenAL::Audio done
WARNING: could not read score file (/home/thd/.chromium-bsu-score)
AudioOpenAL::setMusicMode(SoundType mode)
...startup complete.
```

That looks just fine.

Warzone2100 does however chuck errors :

```
warzone2100 --debug
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

```

New info.  I found posts that said pulse audio is not used in Kubunu (true ?).  Then I found this : [http://www.ogre3d.org/addonforums/viewtopic.php?f=10&t=11539#p65611](http://www.ogre3d.org/addonforums/viewtopic.php?f=10&t=11539#p65611)

Removed the bluez-alsa package and now the debug output change, but still no sound : 

```
warzone2100 --debug
info    |09:49:14: [seq_Play] unable to open 'sequences/titles.ogg' for playback
info    |09:49:14: [seq_Play] unable to open 'sequences/devastation.ogg' for playback
info    |09:49:22: [rebuildSearchPath] * Failed to remove path /home/thd/.warzone2100-2.2/ again
info    |09:49:22: [rebuildSearchPath] * Failed to remove path /usr/data/ again
info    |09:49:22: [rebuildSearchPath] * Failed to remove path /usr/share/warzone2100/ again
info    |09:49:22: [rebuildSearchPath] * Failed to remove path /usr/share/games/warzone2100/ again
AL lib: ALc.c:1818: alcCloseDevice(): deleting 1 Buffer(s)
```

I'm not sure if that is progress or not :-)

Thd.

---

### Post by thirddeep on 2010-09-01
Well, I made (limited) progress.  If I run pavucontrol I can see what application is using audio.

Now, running a game (chromium) I can see it appear and I can see that from pavucontrol's perspective everything is just fine.

So now my question is, what stopping me from hearing the sound that pavucontrol see ?

Thd.

---

### Post by thirddeep on 2010-09-01
Ha, I think I found something !

I ran winecfg, clicked on audio and I had immediate output on the console :

```
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
```

But, that is not the right device, I want it to use HDA ATI SB (which is 0.0).  So how do I do that ?  Maybe if I fix this problem for one application all the others will be fixed.

Thd.

---

### Post by Yellow Pasque on 2010-09-01
> I have read the "Comprehensive Sound Problem Solutions Guide" and it did solve some, but not all my sound problems.

So what exactly did you do to change the stock configuration?
If you compiled ALSA from source (manually or using the ALSA upgrade script, then you will need this): [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by thirddeep on 2010-09-01
Absolutely no custom compile, or even changing configuration files.  Simply making sure all the required packages are installed.

This just seem like such a simple problem.  Some things have sound (UT2k4, playing ogg files, KDE startup / shutdown) and some don't have sound (youtube, chromium, warzone, hedgewars ..)

The most interesting thing was winecfg complaining about the wrong device.  So how do I tell application which device to use ?

I am certainly going to try what that thread suggest, and see what happens ;-)

Thd.

---

### Post by thirddeep on 2010-09-02
So I created the /etc/asound.conf with the required entries, nothing changed.

Perhaps related to my problem, is that every time KDE starts, it asks me if I want to permanently forget about a specific sound device (HD-Audio Generic, ATI HDMI).  If I say yes and restart, it asks me again, if I say no and restart, it asks me again.

Thd.

---

### Post by tripmix on 2010-09-02
If you are not gonna use the hdmi sound and since it's on a separate card you might want to try and blacklist its module. You can run "cat /proc/asound/modules", "lspci" and "lsmod" to help find out which module your using and blacklist it by editing files in /etc/modprobe.d/ usually blacklist.conf or something. That will stop it from loading at boot and should at least get rid of the message you get when you start kde.

EDIT: Have a look at this page  [http://kubuntuforums.net/forums/index.php?topic=3106282.0](http://kubuntuforums.net/forums/index.php?topic=3106282.0)  it seems to be the same problem with two sound cards and no sound on youtube/firefox and some apps. EDIT2: The same info as the first link only without all the useless stuff  [http://forum.vectorlinux.com/index.php?topic=4888.0](http://forum.vectorlinux.com/index.php?topic=4888.0)

---

### Post by thirddeep on 2010-09-02
Damn, that is nice information, why did I not find it ? :)

Alas, it's for nothing :

```
cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

```

I can't blacklist the only sound module there is.

I tried some of the other things that was mentioned, but no go.

Thd.

---

### Post by tripmix on 2010-09-02
Try this thread  [http://forums.opensuse.org/english/get-help-here/hardware/432571-disable-one-two-soundcards-using-same-module.html](http://forums.opensuse.org/english/get-help-here/hardware/432571-disable-one-two-soundcards-using-same-module.html)  it seem to have the info your looking for.

EDIT: Basically it says to add this to /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=3stack-dig enable=1 index=0
options snd-hda-intel enable=1 index=1
options snd slots=snd-hda-intel,snd-hda-intel

# FVI2.LIkXaQ7lzkE:VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
alias snd-card-0 snd-hda-intel

# 2Oa+.qWSfLhLFky3:Radeon HD 3870 Audio device
alias snd-card-1 snd-hda-intel
```
Your obviously gonna need to modify it to suite you, you might have to change or remove "model=3stack-dig" and maybe try messing around with setting enable=0 and such. The devices it reference in the comments are probably different for you too although not really relevant. It should have had some more info on how he went about figuring this out, that mess at the beginning of his comments look like udev IDs.

---

### Post by thirddeep on 2010-09-02
aaa, this did something, though not right.

I added : 

```
options snd-hda-intel model=3stack-dig enable=1 index=0
options snd-hda-intel enable=1 index=1
options snd slots=snd-hda-intel,snd-hda-intel

alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hda-intel

```

right at the end of alsa-base.conf.  It is not 100% exactly what that link say, but I think there where some typo's.

Now what we have, is that :

a) alsamixer shows the wrong device by default.  This is the HDMI device.
b) aplay -l now has the HDMI device at the top, where it used to be last.
c) still no sound on games.

It's clear that the HDMI device can move, but just need to figure out the right magic string for alsa-base.conf and hope that is the problem :-)

Thd.

---

### Post by tripmix on 2010-09-02
Hopefully it's on the right track as I really can't think of anything else that might help. As I understand these options (and I don't really) is index= refers to its position while I assume enable=1 means enabled so enable=0 would mean disabled, the rest don't really make sense to me so I would have just messed around with those first and see what happens. Also make sure there is nothing else wrong with what your trying to test with, maybe a youtube video would be a better choice than a game for testing. Good luck!

---

### Post by thirddeep on 2010-09-02
Enough is enough.

Reinstall system, problem gone.  Now I have to figure out why skype is not getting sound from my mic, but that's for another thread perhaps on skype's forums ;-)

Thanks for your help, it's always appreciated.

Thd.

---

