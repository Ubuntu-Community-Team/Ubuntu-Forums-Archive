---
title: "ALSA, PulseAudio and 5.1 surround sound"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by cogadh on 2007-10-28
I finally got surround sound working properly with ALSA on my machine when I discovered that ESD couldn't handle sound properly with some games. I found that using the PulseAudio ESD compatibility package would fix that problem, but it broke the surround sound functions. I haven't been able to find anything definitive about using PulseAudio in a surround sound situation, so I hope someone here can help.

Basically to get surround sound working originally, I created an .asoundrc file with the following:
```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```
After doing this, I was able to get the stereo sound replicated across all 6 channels for normal audio playback and I can get applications to use the "surround51" plug for audio from 5.1 sources (DVD movies and the like).

After installing the pulseaudio and pulseaudio-esound-compat packages, stereo sound is back to only coming from the front two channels instead of replicated across all 6 channels and running the ALSA speaker test produces results like this: 
```
cogadh@ubuntu-desktop:~$ speaker-test -Dplug:surround51 -c6 -l1 -twav

speaker-test 1.0.14

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy

```
The playback open error occurs repeatedly until I kill the speaker test. The PulseAudio documentation at [http://pulseaudio.org/](http://pulseaudio.org/) did not help at all, as it doesn't seem to cover any situation involving surround sound. Anybody have any suggestions on how to fix this?

---

### Post by cogadh on 2007-10-28
Well, I have partially corrected this in that I now can run the speaker test correctly, but stereo sound is still not replicated across all six channels. What I did was create a .pulse directory in my home directory and created a default.pa file in that directory. The content of that file was this:
```
load-module module-alsa-sink device=hw:0 channels=6 channel_map=front-left, front-right, front-center, rear-left, rear-right, lfe
load-module module-alsa-source device=hw:0
```
Still looking for a solution to the stereo replication problem though.

---

### Post by cogadh on 2007-10-28
One last update. 
I tried following the instructions [here](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server) and [here](http://pulseaudio.org/wiki/PerfectSetup) to try and get this working right, but all I ended up doing was hosing my sound completely so that none of it worked at all. I have now removed all of the changes I made and restored ESD as the default sound mixer, along with all the game problems that led me down the PulseAudio path to begin with. Hopefully someone somewhere has a clue on how to get PulseAudio working correctly with surround sound, 'cause I'm completely out of ideas now...

---

### Post by cogadh on 2007-10-29
Excuse me while I rant for a minute...

**THIS IS FREAKING RIDICULOUS!! I have tried every possible combination of configurations I can find and none of them work properly! My choices are either get crappy sound in everything or get good sound in one or two things while everything else produces sound server errors plus no surround sound! The documentation for PulseAudio sucks, the server defaults to two channel sound, nothing I have found will change that and it breaks nearly everything that used to work before I installed it! This kind of thing never happened before my Gutsy upgrade, what the hell did they change to screw this up so badly!? Is this what we have to look forward to as the default sound mixer in future Ubuntu releases? ](*,)**

/END RANT

So I decided to give it one more try and if I don't do any customizations of ALSA or PulseAudio, basic sound works (system sounds, login/logout, etc.) but I am still stuck with two channel stereo sound only, even when the audio source is 6 channel. I cannot run the speaker test because of the device busy error, and now that same error is affecting anything I try to run through Wine. This is obviously a problem with the PulseAudio configuration, but no configuration changes I make seem to correct the problem. In fact, most of the changes only seem to make things worse, such as eliminating sound entirely. No matter what I do, if PulseAudio is installed, ALSA is prevented from working correctlyI have tried the following:
[LIST=1]
[*]Adding an .asoundrc entry for Pulse devices. Results in no difference at all or a complete elimination of sound when Pulse is set as the default
[*]Modifying the /etc/pulse/default.pa file so that the ALSA module is manually loaded with arguments for 6 channel sound and a device map for the speakers. This leaves basic sound functional, but the sound server still defaults to 2 channel sound and the speaker test still reports that the device is busy. The same thing occurs if I do the same with a per user config file.
[*]Only installing the basic PulseAudio and Esound compatibility packages, but none of the additional Pulse packages. Again, basic sounds still work, but 6 channel will not.
[*]Adding channel and speaker map arguments to PulseAudio's module autoloading function in default.pa. This does absolutely nothing, but apparently the HAL module now has 6 channel sound. :)
[/LIST]
Any combination of the above just produces more of the same, no working sound.

I think all I need is some way to change the PulseAudio sound server's default from 2 channel sound to 6 channel sound, but there are no configuration files or server arguments that seem to allow you to do this. Someone has to have figured this one out, whoever you are, wherever you are, please help!

---

### Post by grunjol on 2007-11-02
The problem is you have a crappy driver sound card (me too) and PA don't  recognize all the channels in your card.

So, try this:

in the alsa config (.asoundrc) add a custom plug like this
```

# my shared device with 5.1 upmix 

pcm.shared_surround {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

# make the default device use pulse (all alsa apps will use it and mix)

pcm.!default {
    type pulse
}

ctl.!default {
    type pulse
}
```

And here is the key, dont use hardware id in the pulse module, just use the alsa.plug 
```

load-module module-alsa-sink device=shared_surround channels=6 channel_map=front-left, front-right, front-center, rear-left, rear-right, lfe
```


This way you will have a 5.1 pulse device with stereo upmix using alsa. I think there is a simple way to do this, but it works for me.

---

### Post by nstamoul on 2007-11-05
No didn' t do the trick for me.Stuck with 2 front speakers playing
My sound card is Audigy on my mobo.
Disabled HAL detection in /etc/pulse/default.pa and tried a bunch of stuff.

Currently i 'm on :

load-module module-alsa-sink device=hw:0,0 sink_name=front rate=48000 
load-module module-alsa-sink device=hw:0,1 sink_name=rear rate=48000 
load-module module-alsa-sink device=hw:0,2 sink_name=center rate=48000 
load-module module-alsa-sink device=hw:0,3 sink_name=side rate=48000 
load-module module-alsa-source device=hw:0,0
load-module module-alsa-source device=hw:0,1
load-module module-alsa-source device=hw:0,2
load-module module-alsa-source device=hw:0,3
 
Works fine,i can switch the audio source between sinks but cannot combine them in order to play surround sound.

Any help would be great :)

---

### Post by nstamoul on 2007-11-05
Changed that to 
load-module module-alsa-sink device=surround71 rate=48000

All the channels appear in the sinks but in the source it still only finds 2 channels

---

### Post by nstamoul on 2007-11-06
Ok got everything working.

Gstreamer,xine and mplayer work alright.I have multichannel sound equal to the sources channels.

I can 't get upmix working but thats allright :).

---

### Post by F-3582 on 2007-12-30
About your six-channel routing methods: There is a [guide]("http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml") you might want to look at. Doesn't address anything Pulseaudio-related, but it will address the channels correctly, at least.

---

### Post by mael on 2008-02-22
nstamoul  what did you do to make it work? but i need upmix to 7.1 anyway :\

i installed hardy alpha and some applications show the same problem. i switched amarok back to alsa which works fine with 7.1. vlc didn't need a change. totem-xine is now stuck with 2.0

what do i need to configure for 7.1? it seems that PA does recognize my 7.1 sound card if the "8" represents the number of channels::
> cat .pulse/default-sink 
alsa_output.pci_1102_8_sound_card_0_alsa_playback_0


---

### Post by Hknuckles on 2008-04-20
I installed the Hardy RC today and had similar problems with my 5.1, all I needed to do was uncomment the line 'default-sample-channels' in the file /etc/pulse/daemon.conf and set the value from 2 to 6 for this line.  Then I just set everything to use PulseAudio in System>Preferences>Sound.

Cheers

---

### Post by mael on 2008-04-21
Thanks! this worked. 

i'm using an audigy2 card.
and btw, if you don't know the tool pavucontrol yet, take a look at it, you can modify the volume of each application with it.

---

### Post by jhnphm on 2008-04-21
Has anyone who has had this problem filed a bug yet?

Seems to be a major problem, but as it doesn't affect me as I only have two speakers I figure someone who actually has problems should file it.

---

### Post by rockin_goliath on 2008-04-22
> **Hknuckles said:**
> I installed the Hardy RC today and had similar problems with my 5.1, all I needed to do was uncomment the line 'default-sample-channels' in the file /etc/pulse/daemon.conf and set the value from 2 to 6 for this line.  Then I just set everything to use PulseAudio in System>Preferences>Sound.

Cheers

Thanks Hknuckles, your a lifesaver! However, I also have an Audigy2 card, and setting everything to PulseAudio in System>Preferences>Sound was not necessary for me, all I had to do what uncomment that line line 'default-sample-channels' in the file /etc/pulse/daemon.conf and set the value from 2 to 6. It took effect after I restarted X.

Hardy is now fully running as my production environment!

---

### Post by MemoryDump on 2008-04-22
> **Hknuckles said:**
> I installed the Hardy RC today and had similar problems with my 5.1, all I needed to do was uncomment the line 'default-sample-channels' in the file /etc/pulse/daemon.conf and set the value from 2 to 6 for this line.  Then I just set everything to use PulseAudio in System>Preferences>Sound.

Cheers
I have a 4.1 setup with my Audigy2 card. Would it be the same settings for my setup?

thxs
-MD

---

### Post by Iznogood on 2008-04-24
no, yours would be 5 not 6

---

### Post by marlonbr on 2008-04-25
As I was testing, it gave me some problems to redo everything here on my Hardy final, but in the end, all I had to do was uncomment the line on /etc/pulse/daemon.conf !

(I'm with a 7.1 sound system)

Thanks **Hknuckles**!!!

:guitar:

---

### Post by xjgnsdof on 2008-04-25
HKnuckles' advice worked for me in Hardy (final) with an Audigy SE, except I, too, didn't have to change from ALSA to Pulse. Restarting X made the changes final.

---

### Post by Guitar John on 2008-04-27
> **Hknuckles said:**
> I installed the Hardy RC today and had similar problems with my 5.1, all I needed to do was uncomment the line 'default-sample-channels' in the file /etc/pulse/daemon.conf and set the value from 2 to 6 for this line.  <snip>

Cheers

This worked for me.

> Then I just set everything to use PulseAudio in System>Preferences>Sound.

In my case (CA1060 Sound Card) this step was not necessary.  

Thank you very much.  This is why I love Ubuntu and this forum.  

Cheers,
John

---

### Post by irshadcharm on 2008-05-01
Sound Card: Sigmatel STAC 92221 Series...ive tried the above step but of no use....

---

### Post by zsolt320i on 2008-05-05
Hi,

I have the same problem like many of you!
I have Hardy Heron 64, motherboard Abit KN8SLi, Sound card:
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0.
The PC is connected with an optical cable to the amplifier.
The problem is that the SPDIF passtrough does not work, therefore the dolby do not work :(
Is there any chance to solve the passtrough?

---

### Post by Chobo-Mog on 2008-05-05
> **Hknuckles said:**
> I installed the Hardy RC today and had similar problems with my 5.1, all I needed to do was uncomment the line 'default-sample-channels' in the file /etc/pulse/daemon.conf and set the value from 2 to 6 for this line.  Then I just set everything to use PulseAudio in System>Preferences>Sound.

Cheers

Worked perfectly with my Hardy LTS and Audigy 2 ZS.  Thanks! =D

---

### Post by MeURi on 2008-05-10
I went crazy for some days, then some minutes ago I came up with a working setup (trial and error approach rules :D)

My hardware:
[LIST]
[*]Realtek ALC650 (AC97 Codec rev 02) on Intel ICH4
[*]Creative T6060 5.1 speakers
[/LIST]

My /etc/asound.conf
```

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

Then, my changes in the /etc/pulse/daemon.conf
```

default-sample-rate = 48000
default-sample-channels = 6

```

I'm using *pulseaudio-esound-compat*, and under *System>Preferences>Sound* I have the following setup:
[LIST]
[*]Devices: Everything says "PulseAudio Sound Server"; the *Default mixer tracks* section has "Intel 82801DB-ICH4 (Alsa-mixer)" as device
[*]Sounds: "Enable software sound mixing (ESD)" is enabled
[/LIST]

My user is in both *pulse-access* and *pulse-rt* groups

From the *gnome-volume-control* applet I had to specify:
[LIST]
[*]Surround Jack Mode: Shared
[*]Channel mode: 6ch
[*]Duplicate Front: disabled
[/LIST]

Now I have my stereo sound replicated through all my speakers, with surround.
The *speaker-test* command works (except that I have rear channels and center/LFE swapped - actually I noticed that only performing a speaker test, else I would have said everything worked perfect)

I'm gonna test some dvd playback with real 5.1 sound, and add my results.

-- DVD playback results --
I still have only stereo output option under vlc :(
Totem simply refuses to play my unencrypted dvd, gets stuck at 0:00. Moreover, under the *Properties* tab, it says that audio is AC3, but has 0 channels :|
-- End of results --

My just two cents :)

---

### Post by MeURi on 2008-05-10
@ zsolt320i:

I don't know much about passthrough...

Try looking at [thread=714712]this thread[/thread], maybe it hepls

---

### Post by sammydee on 2008-05-20
Anyone having problems with surround sound in pulseaudio, BEFORE messing around with asound.conf or anything like that, should probably check out [this thread.]("http://ubuntuforums.org/showthread.php?t=795525")

It might be very easy to get working :-)

---

### Post by KuriKai on 2008-06-25
[QUOTE=Hknuckles
I installed the Hardy RC today and had similar problems with my 5.1, all I needed to do was uncomment the line 'default-sample-channels' in the file /etc/pulse/daemon.conf and set the value from 2 to 6 for this line. Then I just set everything to use PulseAudio in System>Preferences>Sound.
[/QUOTE]

this worked for me as well, thanks

---

### Post by GraysonPeddie on 2008-07-16
Sorry to bring up this old thread but...

> **irshadcharm said:**
> Sound Card: Sigmatel STAC 92221 Series...ive tried the above step but of no use....

Same here, with my AMD 780G chipset (ECS motherboard).

---

