---
title: "Cant play more than one audio stream"
date: 2009-12-19
forum: Multimedia Software
---

### Post by Gedna on 2009-12-19
here is the problem. 
i have installed my sound card rme 9632 with alsa (pulse audio was removed), it plays the sounds, i can play mp3, i can watch the movie and hear it, but after i play something in youtube, all other sounds dissapears, and i catn play mp3 and watch movie at the same time, i will got sound just from one, 

i have installed real time kernel, hoped to make some differences but no luck, 
rhythm box shows an gstream error saying that it need plugin...

i dont know where is the problem and how to make sounds everywhere..

help

---

### Post by Gedna on 2009-12-19
anyone :/

---

### Post by RaumTrug on 2009-12-19
have a look here: [http://www.linuxjournal.com/article/7024#comment-338737](http://www.linuxjournal.com/article/7024#comment-338737), a try to get sw mixing going. it seems like the ubuntu alsa setup doesn't enable the dmix-plugin by default for your card, so the alsa driver gets directly grabbed by the first prog. trying to, excluding others from using the card! ([http://alsa.opensrc.org/DmixPlugin](http://alsa.opensrc.org/DmixPlugin) for more info on configuring it!)

---

### Post by Gedna on 2009-12-20
wow that is so complex :S is there any easier way?

---

### Post by RaumTrug on 2009-12-20
hmm, I think there's no easier way! normally, for most cards, the ubuntu alsa installation defines dmix by default, like it was for my m2496 - when I removed pulseaudio (is a wise step imo, karmics pulse is a mare!), the dmix wrapper became the standard device, so things worked "out of the box". I looked into my /usr/share/alsa/ and found no definitions for your card there, so I guess one'd have to define it by him-/herself, best with a ~/.asoundrc.

I'm no expert at this, I just dipped into ubuntu myself, but I can give it a try (shouldn't be too hard)! but don't be frustrated if I don't acchieve positive results ;)

please post the output of "aplay -l && aplay -L" in terminal, and I'll try making up the file for you!

(basically you just put a little file called ".asoundrc" in your home folder (note it will be hidden because of the dot) where you tell alsa to use dmix with your card)

---

### Post by Gedna on 2009-12-20
you are so kind :)
heres what iv got

gediminas@gediminas:~$ aplay -l && aplay -L
**** List of PLAYBACK Hardware Devices ****
card 0: DSP [Hammerfall DSP], device 0: RME Hammerfall HDSP 9632 [RME Hammerfall HDSP 9632]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
default:CARD=DSP
    Hammerfall DSP, RME Hammerfall HDSP 9632
    Default Audio Device
null
    Discard all samples (playback) or generate zero samples (capture)
gediminas@gediminas:~$

---

### Post by RaumTrug on 2009-12-20
hello again!


oh well, forget it, I've overseen something in your first post: that mixing already worked before flash was running! then my approach'd be of no use for you!!!

try "sudo /etc/init.d/alsa-utils restart" when it happens again, maybe that is a workaround...

---

### Post by Gedna on 2009-12-21
sudo /etc/init.d/alsa-utils restart

did not helped :( still the same,

---

### Post by VertexPusher on 2009-12-21
Did you install flashplugin-nonfree-extrasound?

Remove it!

flashplugin-nonfree-extrasound makes Flash use OSS instead of ALSA. OSS does not support sound card sharing, so that's why you can't play any other sounds while Flash is active. flashplugin-nonfree-extrasound was meant to fix some issues with PulseAudio, but since you removed PulseAudio, this "fix" is no longer needed.

---

### Post by Gedna on 2009-12-21
no,  flashplugin-nonfree-extrasound is not installed on my system

---

### Post by Gedna on 2009-12-22
anyone

---

### Post by Ubuntaqua on 2009-12-22
> **Gedna said:**
> anyone

It seems that you purposefully removed the very tool to handle multiple sounds. Yes, in standard ubuntu, pulseaudio is the official sound server / mixer. Was there a reason for that ?

---

### Post by Gedna on 2009-12-22
pulseaudio is not capable of working with rme 9632 just alsa is working with it, so if i want to even have some sound, i must remove pulseaudio, and i did. but im not having multiple sound sources and its killing me..

---

### Post by Ubuntaqua on 2009-12-22
> **Gedna said:**
> pulseaudio is not capable of working with rme 9632 just alsa is working with it, so if i want to even have some sound, i must remove pulseaudio, and i did. but im not having multiple sound sources and its killing me..pulseaudio does not touch your sound card, only alsa does. Alsa then sends the stream to the pulseaudio server. Pulseaudio is not a sound card driver !

---

### Post by Gedna on 2009-12-22
ok im new at ubuntu i dont know things, but even if now i go to terminal sudo apt-get install pulseaudio 
after that i will not have ANY sound at all..
so maby you cant explain me this, because i really dont know

---

### Post by Ubuntaqua on 2009-12-22
> **Gedna said:**
> ok im new at ubuntu i dont know things, but even if now i go to terminal sudo apt-get install pulseaudio 
after that i will not have ANY sound at all..
so maby you cant explain me this, because i really dont know

removing / reinstalling pulseaudio probably messed up some things.
If you have changed some things try in Synaptic to reinstall packages related to alsa and pulseaudio.

---

### Post by Gedna on 2009-12-22
tryed reinstalling alsa pulse stuff still the same, after pulse installation i cant hear any sounds, after it removal i can hear only one sound source...

---

### Post by Ubuntaqua on 2009-12-22
> **Gedna said:**
> tryed reinstalling alsa pulse stuff still the same, after pulse installation i cant hear any sounds, after it removal i can hear only one sound source...

so it means alsa is configured to talk to hardware instead of to pulse. try to remove all that with the purge option (removes stuff AND config files) reinstall everything... 
Last week I messed up badly with alsa/pulse config files and had problems not quite like yours but similar. After looking a bit for a solution I found it simplier to reinstall the whole distrib. There "should" be a better way, though.

---

### Post by RaumTrug on 2009-12-22
no well, removing pulse has various reasons, like avoiding its bugs, high cpu usage, programs that won't work with it etc...I did it, too, successfully, like described in the thread [http://ubuntuforums.org/showthread.php?t=1313253](http://ubuntuforums.org/showthread.php?t=1313253)

you might want to check if you did all that correctly and the necissary packages are installed/uninstalled.

post #3 describes the steps to do (you can leave out the esound/esd stuff btw).

normally, after doing this (like when you manage to kill pulse temporarily) alsa apps will use an alsa plugin called "dmix" that should be preconfigured by ubuntu (and it's quite hard to do so manually, some alsa tools are missing in ubuntu), enabling the system to play multiple sounds simultaneously (like pulse does, but dmix is way faster and more stable imho).

but I think that should not be a problem, since in the first post there was written that this stuff was already working untill some adobe flash stuff is started, after which programs can only use the soundcard exclusively (only one prog at any time)! or did I understand that wrongly? does playing multiple sounds work after reboot (try playing one mp3 plus a game with sound or whatever...), before you launch any flash app in the browser? if not, then there's something messed with the dmix configuration!

if it works, then I don't really understand what's going on other than dmix/alsa probably being abused hardly by adobe flash leading to it crashing, so alsa apps have the pure hardware alsa driver exposed as only sound device.

---

### Post by Gedna on 2009-12-22
thank you for your post.
maybe as was misleading, after you boot up the system, you can play songbird for example and hear the music, BUT i cant play vlc at the same time, no sound. and if i do vice-versa , play VLC first and then try to play music on Songbird (for example) iv got an error saying that auutoaudiosink and alsasink is missing and thats it.

---

### Post by RaumTrug on 2009-12-22
have you got "gstreamer0.10-alsa" installed (and likewise the gstreamer package w/ -pulseaudio at the end "purged"(remove completely in synaptic, do only when the -alsa package is already there)? have you tried running "gstreamer-properties" and setting "alsa" as output?

try installing all the packages in the link above, also (but don't do the autoremove stuff for safety...).

if all that doesn't help it's time for trying an .asoundrc enabling dmix manually! too bad some vital alsa tools are missing in ubuntu...but anyways...do you use surround sound or stereo only (stereo only would be dank, as I'm lazy :P )?

---

### Post by Gedna on 2009-12-22
stereo :) after opened gstreamer-properties and set everything to alsa, and pressed test, iv got a message that device is in use and it cannot open device for playback... :(

gediminas@gediminas:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open audio device for playback. Device is being used by another application. [gstalsasink.c(685): gst_alsasink_open (): /GstPipeline:pipeline0/GstAlsaSink:alsasink3:
Device 'default' is busy]
gediminas@gediminas:~$

---

### Post by RaumTrug on 2009-12-22
well, okay, then I'll give it a try; can't guarantee it to work - it's untested, as I don't have your card, and my alsa is running good, so I don't want to mess with it :P

first do "lsof | grep /dev/snd/pcm" to find the application using the soundcard, and terminate that application!

then (for safety) do "cat ~/.asoundrc", it should say something like "file does not exist", that's good then!

when all that is fine, open gedit (the text editor) and copy the stuff in the code block below in it, save as "~/.asoundrc"

do "sudo /etc/init.d/alsa-utils restart" to try to activate changes, if it doesn't work, reboot!

in case it still doesn't work, delete the file ("rm ~/.asoundrc") and restart alsa again, and we'll have to try something else :confused:

here the code goes:

```


# .asoundrc for dmix
# first try...stereo
# put to ~/.asoundrc
# do "sudo /etc/init.d/alsa-utils restart" to activate changes
# if it doesn't work, removing/renaming the asoundrc plus an alsa-utils restart
# should revert changes ;)

pcm.snd_card {
        type hw
        card 0
        device 0
}

ctl.snd_card {
        type hw
        card 0
        device 0
}

# dmix-plugin: software mixing
pcm.dmixer {
    type dmix
    ipc_key 1024
    # ipc_perm 0666       # making available for other "users"...in case a tvtuner or whatever needs this
    slave.pcm "snd_card"
    slave {
        period_time 0
        period_size 1024
        buffer_size 4096
        ### for changing sampling rate of card (default will be 48000)
        ### just remove the "#" before "rate" and enter a new number (i.e. 44100, 96000...)
        # rate 44100
        ### 24 bit sound activated, comment with "#" like rate above to try 16...
        format S32_LE
        ### number of channels must match binding below...for more channels (surround) just
        ### use correct num. of channels & propagate binding (i.e. 5.1 = 6 channels, bind. 0-5)
        channels 2 
    }
    bindings {
        0 0
        1 1
    }
}

#make dmix device default alsa one!
pcm.!default {
    type plug
    slave.pcm "dmixer"
}


```

---

### Post by Gedna on 2009-12-22
thank you for your effort to help me, but it does not helped. after   the code and the file i cant get any sound, i had to do  ("rm ~/.asoundrc") and then sudo /etc/init.d/alsa-utils restart
to get the sound, but it was the same as before, :(

---

### Post by VertexPusher on 2009-12-22
I just looked at the configuration files for RME cards in /usr/share/alsa/cards. Surprisingly, none of them defines the "default" PCM. This indeed explains all your troubles, because applications usually fall back to OSS if they fail to open the default ALSA device. OSS means: only one application at a time can use the card, others get blocked.

RaumTrug is right, you need a custom .asoundrc file that defines the "default" PCM for applications to use. And you need to make sure that all the applications, including GStreamer, use ALSA again instead of OSS.

Please enter the following commands and post their output here. Based on that information it should be possible to customize .asoundrc properly.
```
aplay -l
arecord -l
aplay -L
arecord -L
```

---

### Post by Gedna on 2009-12-22
its nice to see helpful people around here, :) thank you
 heres what iv came up with

gediminas@gediminas:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DSP [Hammerfall DSP], device 0: RME Hammerfall HDSP 9632 [RME Hammerfall HDSP 9632]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
gediminas@gediminas:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: DSP [Hammerfall DSP], device 0: RME Hammerfall HDSP 9632 [RME Hammerfall HDSP 9632]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gediminas@gediminas:~$ aplay -L
default:CARD=DSP
    Hammerfall DSP, RME Hammerfall HDSP 9632
    Default Audio Device
null
    Discard all samples (playback) or generate zero samples (capture)
gediminas@gediminas:~$ arecord -L
default:CARD=DSP
    Hammerfall DSP, RME Hammerfall HDSP 9632
    Default Audio Device
null
    Discard all samples (playback) or generate zero samples (capture)
gediminas@gediminas:~$

---

### Post by RaumTrug on 2009-12-22
heh, I knew I'd suck badly at this!

maybe it's just the channel numbers that were wrong (so dmix did output to the wrong ports with my asoundrc)...? I've seen an asoundrc for this card (link earlier in the forum) that used channel 16 & 17, those are probably the s/pdif (digital) ports...say, how are the speakers/the amplifier connected to the card? from what I've seen of it on the web it's quite some monster...it's probably reason for shame to use it with dmix, it's just crying for hw mixing drivers!

---

### Post by Gedna on 2009-12-22
its connected through XLR breacout cables to my monitors, Tannoy reveal 5a and a sub tannoy ts8

---

### Post by VertexPusher on 2009-12-22
> **Gedna said:**
> gediminas@gediminas:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DSP [Hammerfall DSP], device 0: RME Hammerfall HDSP 9632 [RME Hammerfall HDSP 9632]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
gediminas@gediminas:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: DSP [Hammerfall DSP], device 0: RME Hammerfall HDSP 9632 [RME Hammerfall HDSP 9632]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gediminas@gediminas:~$ aplay -L
default:CARD=DSP
    Hammerfall DSP, RME Hammerfall HDSP 9632
    Default Audio Device
null
    Discard all samples (playback) or generate zero samples (capture)
gediminas@gediminas:~$ arecord -L
default:CARD=DSP
    Hammerfall DSP, RME Hammerfall HDSP 9632
    Default Audio Device
null
    Discard all samples (playback) or generate zero samples (capture)
gediminas@gediminas:~$
Try the following .asoundrc:
```
pcm.!default {
    type asym
    playback.pcm {
        type plug
        slave.pcm "dmix:DSP"
    }
    capture.pcm {
        type plug
        slave.pcm "dsnoop:DSP"
    }
}
```
When the file is in place, quit any running sound application, then run the following command:
```
speaker-test -t wav -c 2
```
You should hear a test sound switching between the left and right speaker. While the test is running, launch other sound applications and see if they can access the sound card at the same time. If there is an application which is still blocked, list it here.

---

### Post by Gedna on 2009-12-22
saved the file no sound app was running typed speaker-test -t wav -c 2

and iv got a looong messaged saying that its busy, 

speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
ALSA lib pcm_direct.c:975:(snd1_pcm_direct_initialize_slave) unable to install hw params
ALSA lib pcm_dmix.c:1020:(snd_pcm_dmix_open) unable to initialize 
ALSA lib pcm_direct.c:975:(snd1_pcm_direct_initialize_slave) unable to install hw params
ALSA lib pcm_dmix.c:1020:(snd_pcm_dmix_open) unable to initialize slave
Playback open error: -16,Device or resource busy
ALSA lib pcm_direct.c:975:(snd1_pcm_direct_initialize_slave) unable to install hw params
ALSA lib pcm_dmix.c:1020:(snd_pcm_dmix_open) unable to initialize 

and so on.. i have heard no sound at all

---

### Post by VertexPusher on 2009-12-22
The new .asoundrc takes effect on any application that is launched **after** the file was put in place. Any application that was launched **before** must be quit because it will still use the old settings.

If you have trouble finding that application (it could be a messenger or even the web browser running a Flash applet), just keep the .asoundrc file there and reboot the computer.

If the card is still blocked after the reboot, we should take a closer look at how you removed PulseAudio. Maybe you forgot something.

---

### Post by Gedna on 2009-12-22
after reboot its the same

---

### Post by VertexPusher on 2009-12-22
There is one more possible error in the current setup: The dmix PCM must be run at
[list][*]a sample rate (44.1kHz, 48kHz, 96kHz...)[*]a sample format (16bit, 24bit, 32bit, float...)[*]a channel configuration (stereo, 5.1, 7.1)[/list]
which is supported by the hardware driver of the card. In any other case it will refuse to initialize, and this may be what causes the "unable to install hw params" error.

To find out what your card can handle, run this command:
```
speaker-test -l 1 -D hw:DSP -F S16_LE -r 48000 -c 2
```
If my theory is right, you will see one of the following errors:
```
Sample format not available for playback: Invalid argument

Channels count (2) not available for playbacks: Invalid argument

Rate 48000Hz not available for playback: Invalid argument
```
If you see one of these, run the command again with a different format (-F), sample rate (-r) or channels (-c) parameter until you find a combination that is accepted by the card. Only modify the parameter that the error message refers to.

Possible values for the sample rate:
44100 48000 96000 192000

Possible values for the sample format:
S16_LE S16_BE U16_LE U16_BE S24_LE S24_BE U24_LE U24_BE S32_LE S32_BE U32_LE U32_BE
(There are more, but these are the most likely ones.)

Once you have found a working combination, we can modify the .asoundrc file accordingly so that dmix uses the same parameters.

---

### Post by RaumTrug on 2009-12-22
edit: do change

```
 slave pcm "dmix:DSP, FORMAT=S32_LE"
```

same with the dsnoop.

---

### Post by Gedna on 2009-12-23
VertexPushe i tryed tons of parameters but everytime iv got this message 
speaker-test 1.0.20

Playback device is hw:DSP
Stream parameters are 44000Hz, S32_BE, 2 channels
Using 16 octaves of pink noise
Access type not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument
root@gediminas:~# speaker-test -l 1 -D hw:DSP -F U32_LE -r 44000 -c 2

speaker-test 1.0.20

Playback device is hw:DSP
Stream parameters are 44000Hz, U32_LE, 2 channels
Using 16 octaves of pink noise
Access type not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument
root@gediminas:~# speaker-test -l 1 -D hw:DSP -F U32_BE -r 44000 -c 2

and so on....

RaumTrug after changing things you mentioned in asoundrc file after reboot iv got noo sound at all, had to undo to hear something again

---

### Post by VertexPusher on 2009-12-23
> **Gedna said:**
> Access type not available for playback: Invalid argument
Now we are getting somewhere.

Please run this test:
```
speaker-test -c 2 -D plughw:DSP
```
If you hear the test sound and don't get any error message, try this .asoundrc:
```
pcm.!default {
    type asym
    playback.pcm {
        type plug
        slave.pcm {
            type dmix
            ipc_key 5678292
            ipc_gid {
                @func refer
                name defaults.pcm.ipc_gid
            }
            ipc_perm {
                @func refer
                name defaults.pcm.ipc_perm
            }
            slave {
                pcm "plughw:DSP"
                format "S32_LE"
                rate 48000
            }
        }
    }
    capture.pcm {
        type plug
        slave.pcm {
            type dsnoop
            ipc_key 5678291
            ipc_gid {
                @func refer
                name defaults.pcm.ipc_gid
            }
            ipc_perm {
                @func refer
                name defaults.pcm.ipc_perm
            }
            slave {
                pcm "plughw:DSP"
                format "S32_LE"
                rate 48000
            }
        }
    }
}
```
When the file is in place, run this:
```
speaker-test -c 2
```

---

### Post by Gedna on 2009-12-23
speaker-test -c 2 -D plughw:DSP 
after this i finally heard a sound. then maked the file
and run this speaker-test -c 2

bus then iv got this error 

speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib pcm_dmix.c:1013:(snd_pcm_dmix_open) dmix plugin can be only connected to hw plugin
Playback open error: -22,Invalid argument
ALSA lib pcm_dmix.c:1013:(snd_pcm_dmix_open) dmix plugin can be only connected to hw plugin


*i just noticed something after making .asoundrc file with your code. Skype is not launching , after delete of this file it can launch again... strange how the hell this file connect with Skype

---

### Post by VertexPusher on 2009-12-23
> **Gedna said:**
> speaker-test -c 2 -D plughw:DSP 
after this i finally heard a sound.
I found some info about the Hammerfall card. It seems there is an additional channels parameter required in the dmix configuration. Since plughw:DSP seems to work, let's find out how it talks to hw:DSP. The "aplay" tool can be used for that.
```
aplay -v -D plughw:DSP /usr/share/sounds/alsa/Front_Center.wav
```
The "-v" option makes aplay show the PCM configuration used during playback. Please copy and paste the entire output here.

---

### Post by Gedna on 2009-12-23
gediminas@gediminas:~$ aplay -v -D plughw:DSP /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
Plug PCM: Route conversion PCM (sformat=S32_LE)
  Transformation table:
    0 <- 0
    1 <- 0
    2 <- 0
    3 <- 0
    4 <- 0
    5 <- 0
    6 <- 0
    7 <- 0
    8 <- 0
    9 <- 0
    10 <- 0
    11 <- 0
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 2048
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 2048
  stop_threshold   : 2048
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Slave: Hardware PCM card 0 'Hammerfall DSP' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_NONINTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 12
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 24
  buffer_size  : 2048
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 2048
  stop_threshold   : 2048
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
  appl_ptr     : 0
  hw_ptr       : 0
gediminas@gediminas:~$

---

### Post by VertexPusher on 2009-12-23
```
pcm.!default {
    type asym
    playback.pcm {
        type plug
        slave.pcm {
            type dmix
            ipc_key 5678292
            ipc_gid {
                @func refer
                name defaults.pcm.ipc_gid
            }
            ipc_perm {
                @func refer
                name defaults.pcm.ipc_perm
            }
            slave {
                pcm {
                    type hw
                    card "DSP"
                }
                format "S32_LE"
                rate 48000
                channels 12
                buffer_size 2048
                period_size 1024
            }
        }
    }
    capture.pcm {
        type plug
        slave.pcm {
            type dsnoop
            ipc_key 5678291
            ipc_gid {
                @func refer
                name defaults.pcm.ipc_gid
            }
            ipc_perm {
                @func refer
                name defaults.pcm.ipc_perm
            }
            slave {
                pcm {
                    type hw
                    card "DSP"
                }
                format "S32_LE"
                rate 48000
                channels 12
                buffer_size 2048
                period_size 1024
            }
        }
    }
}
```
Please run
```
speaker-test -c 2
```
with the .asoundrc file above.

---

### Post by Gedna on 2009-12-23
You my friend VertexPusher  did it :) its working all the sounds are working now . omg thank you sooo so much :) you made my day,

perfection, solved the problem

---

### Post by VertexPusher on 2009-12-23
Please test capture mode as well, e.g. do a test call in Skype or record some sound in Audacity. The capture PCM is defined separately, i.e. its parameters can be adjusted if necessary without affecting the playback part.

---

### Post by Gedna on 2009-12-23
well yes there are errors in recording audacity, but since im not going to use this sound card with Ubuntu on some Audio recording work its not a big headache for me :)

---

### Post by Jose Catre-Vandis on 2009-12-23
Kudos @ Vertexpusher :)

---

### Post by RaumTrug on 2009-12-23
ah the thing needs 12 channels to be running simultaneously!

great, now as it works, I can sleep again. merry xmas, you can now play an arbitrary number of out-of-tune christmas songs in parrallel to get yourself into the mood ;)

my apologies for trying to fix something I didn't totally understand... :oops:

---

### Post by Jose Catre-Vandis on 2009-12-23
Sorry RaumTrug - didn't mean to leave you out!

I too have removed pulseaudio (Using Audacious which won't work with Pulse no matter what I try) but I was only getting one device at a time.

Adding the .asoundrc
```
pcm.!default {
    type asym
    playback.pcm {
        type plug
        slave.pcm "dmix:nForce2"
    }
    capture.pcm {
        type plug
        slave.pcm "dsnoop:nForce2"
    }
}
```
and restarting alsa allowed multiple devices to access the soundcard and play.

This is useful when you are listening to music and you pause to listen to something else

---

### Post by RaumTrug on 2009-12-23
btw. gedna, if you wish to record something with that beast of card, try looking into the jack sound server, choosing "hw:0" as interface...should give you lots of channels of which you'd have to find out what they're for...

also, for rme cards there's a special mixer/audio interface tool in the package "alsa-tools-gui" you might want to check out, one called hdspconf, one hdspmixer (they appear in the multimedia menu). be careful with something like "enhanced mode" as I read somewhere that the hdsp driver changes the number of channels exposed, and it is recommended closing all alsa-using apps before switching and then running jack (and switching back when through with jack before using standard alsa apps). it will enable the dank high sample rates of the device.

good luck!

---

### Post by Gedna on 2009-12-23
thank you all and merry Xmas :)

---

### Post by Terror1980 on 2010-08-29
_UPDATE_:
Turns out that I had a asoundrc file (created in an attempt to solve another problem ...with XBMC). When I removed it I can play more audio streams at the same time but here I am getting back to my old problem. Can't make the surrond work through digital...or at least partial. Let me explain. When I use the below command:

```
speaker-test -t wav -c 5
```

I get the below output

```
speaker-test 1.0.22

Playback device is default
Stream parameters are 48000Hz, S16_LE, 5 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 39 to 419430
Period size range from 12 to 139810
Using max buffer size 419428
Periods = 4
was set period_size = 104857
was set buffer_size = 419428
 0 - Front Left
 1 - Front Right
 2 - Rear Left
 3 - Rear Right
 4 - Center
Time per period = 9.118639
 0 - Front Left
 1 - Front Right
 2 - Rear Left
 3 - Rear Right
 4 - Center
Time per period = 9.154754

....and so on

```

and what I hear is the correct sound for fr, fl, and center. The rr and rl sounds are played in the front right and front left speakers.

_END-UPDATE_




Hello guys,

I have the same problem with the playback on my sound card - Can't play more than one audio stream. Besides the 5 channels test only plays on the 2 front speakers.
The following was generated with the ALSA Information Script [http://www.alsa-project.org/db/?f=44b386e0bb4759f6b1ed0318ccea740aa79fc2dd](http://www.alsa-project.org/db/?f=44b386e0bb4759f6b1ed0318ccea740aa79fc2dd)

Here's the result of aplay -l:

```
bogdan@bogdan-desktop:/usr/share/alsa/cards$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```The hardware setup is the following:
The connection made through Coax cable from the blue jack into a coax digital input on [Yamaha RX-V367 Receiver]("http://www.yamaha.com/yec/products/productdetail.html?CNTID=5117154")
The receiver is set to Dolby Pro 2 and I have 5 big speakers (1 center, fl, fr, rl, rr)

When issuing:

```
aplay -v -D plughw:CA0106 /usr/share/sounds/alsa/Front_Center.wav
```I get the below output:

```
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
Plug PCM: Route conversion PCM (sformat=S16_LE)
  Transformation table:
    0 <- 0
    1 <- 0
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 4096
  period_time  : 85333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  period_event : 0
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Slave: Hardware PCM card 0 'CA0106' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 4096
  period_time  : 85333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  period_event : 0
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
  appl_ptr     : 0
  hw_ptr       : 0

```Please let me know if you need additional information.

Thanks in advance
P.S. I am a newbie so have mercy :D

---

