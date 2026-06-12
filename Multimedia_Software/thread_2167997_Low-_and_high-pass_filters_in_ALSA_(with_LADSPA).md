---
title: "Low- and high-pass filters in ALSA (with LADSPA)"
date: 2013-08-16
forum: Multimedia Software
---

### Post by Elastic_Potential on 2013-08-16
Greetings,

I've been using an unaltered ALSA for awhile, but I think it'd be beneficial to set up a low-pass and high-pass filter, so I'm in the babby stages of setting-up an .asoundrc file.  I ran across [a post on the Achlinux forums]("https://bbs.archlinux.org/viewtopic.php?id=168026") where a user set up both using ladspa-plugins.  However, I can't seem to locate this package in [L]ubuntu.  Any recommendations?

Also, does anyone know if ALSA can utilize a limiter (to prevent songs from clipping)?  I know this can be done in various players, such as DeaDBeeF, but it'd be a lot more convenient to set-up a system-wide limiter rather than continuously updating my replygain tags.

Thanks.

---

### Post by tgalati4 on 2013-08-16
Do you have this installed?  

ubuntustudio-audio-plugins - Ubuntu Studio audio plugins Package

Open a terminal:

```
apt-cache policy ubuntustudio-audio-plugins
apt-cache search LADSPA
```

The filters you are looking for are either in the Ubuntu Studio package or in one of the other packages listed above.

I'm not aware of a way for ALSA by itself to limit clipping.  You have to play the file through a player (and there are several) and use the player's filters to limit clipping.  If you can't get enough volume through your setup, then you need an external amplifier so that your player volumes are always low enough to prevent clipping from all musical sources.  Most PC amplifiers are only good for 1 or 2 watts of power and will always clip at moderately loud volumes.  You need a 100-watt stereo system to prevent such clipping.

---

### Post by Elastic_Potential on 2013-08-21
> **tgalati4 said:**
> The filters you are looking for are either in the Ubuntu Studio package or in one of the other packages listed above.

Thank you for your help.  However, I'm going to concede to my lack of knowledge about how to configure some of these plugins.  The configuration in the link I posted initially uses a different high pass filter than the one I have (theirs is like 1051, and mine is 1890 (highpass_iir_1890.so)).  Not to mention this is my first time with all this, and I feel very ignorant to admit that it's all very confusing.

Is there a guide on how to configure some of these plugins?  I'm unaware of where to find their parameters which I can utilize.

---

### Post by tgalati4 on 2013-08-21
A simple search in *NewDocs* gives the following:

[https://help.ubuntu.com/community/Audio/ApplicationIntroductions](https://help.ubuntu.com/community/Audio/ApplicationIntroductions)
[http://manpages.ubuntu.com/manpages/hardy/man1/applyplugin.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/applyplugin.1.html)
[http://manpages.ubuntu.com/manpages/hardy/man1/listplugins.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/listplugins.1.html)

---

### Post by Elastic_Potential on 2013-10-10
Sorry it took so long to reply.  With your help and a lot of red herrings, I found two commands to be very useful, and I'm going to post them for anyone else who jumps into alsa:

```
listplugin
```
which will populate a list of ladspa plugins, from which you can pick one and view more info about its parameters using:
```
analyseplugin plugin.so
```
and a basic format for ladpsa plugins from this page:
[http://alsa.opensrc.org/Ladspa_%28plugin%29](http://alsa.opensrc.org/Ladspa_%28plugin%29)

Okay, that being said, those resources helped me get this bandpass filter working.  Note that I have the cutoff values at stupid settings for testing purposes:

```

#~/.asoundrc
pcm.highpass {
    type ladspa
    slave.pcm "lowpass";
    path "/usr/lib/ladspa";
    plugins [{
        label hpf
        input {
            controls [ 14000 ]
        }
    }]
}

pcm.lowpass {
    type ladspa
    slave.pcm "plughw:1,0";
    path "/usr/lib/ladspa";
    plugins [{
        label lpf
        input {
            controls [ 20000 ]
        }
    }]
}

```

using the command "speaker-test -Dplug:highpass -c 2"

However, I'd like for this to apply to all sound output, including my music player (DeaDBeeF).  What do I need to do to accomplish this?

---

### Post by tgalati4 on 2013-10-10
You might have to write your own plug-in for deadbeef:  [http://deadbeef.sourceforge.net/plugins.html](http://deadbeef.sourceforge.net/plugins.html)

Follow an example like the headphone crossfeed plug-in and use the ladspa plug-ins to create the filter that you need.  There is no system-wide EQ in ALSA, nor is there system-wide digital processing, so each player handles it differently.

*Speaker-test* is a special player for playing test tones to ring out speakers.  The fact that you were able to use custom digital filters with it is quite clever.  But then to get 5.1 surround sound requires digital processing, so *speaker-test* has a framework for handling digital filters.  *Deadbeef* also has a framework for specialized plug-ins, but not a clip limiter.  

In fact, I'm not aware of any linux player with a clip limiter, just recorders such as *audacity*, *ardour*, and *calf*, where a clip limiter is quite helpful.  

ALSA redirects audio but does not process it.  It sets up the hardware with the correct channel, bit-rate, sampling frequency, etc, then connects the software stream to that device.  You need a music player that handles (decodes) the music then applies a digital filter then sends that stream to ALSA or pulseaudio.  *Deadbeef* with a clip-limiter plug-in would do that.

Of course, you would have to write it.

*rhythmbox* has a extensive plug-in architecture and a decent plug-in writing guide:  [https://wiki.gnome.org/RhythmboxPlugins/WritingGuide](https://wiki.gnome.org/RhythmboxPlugins/WritingGuide)

*audacious* supports ladspa plug-ins but I have not played with it.  You can activate the ladspa host in Preferences-->Effects.  With some fancy tweaking, you can probably get a clip limiter using ladspa in *audacious*.

---

### Post by Elastic_Potential on 2013-10-11
Thank you for all your help, [**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895").

If need be, I may dabble with plugin-making for DB; Audacious sounds promising as well, but I've had issues with its functionality in the past (ie random crashes).  

Before I go any further in that, though, I want to share my output for "aplay -L":
```

nergal@Aeon:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
highpass
lowpass
default
    Playback/recording through the PulseAudio sound server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
sysdefault:CARD=SB
    HDA ATI SB, CONEXANT Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, CONEXANT Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=SB,DEV=0
    HDA ATI SB, CONEXANT Analog
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, CONEXANT Analog
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, CONEXANT Analog
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, CONEXANT Analog
    Hardware device with all software conversions
nergal@Aeon:~$ 

```
I found this interesting because deadbeef, in the "output device" drop-down list, includes all of these options EXCEPT "highpass" and "lowpass", the two custom pcm I made in my .asoundrc file:
[http://i.imgur.com/3hUEA4t.png](http://i.imgur.com/3hUEA4t.png)

Is it possible to just tell deadbeef to access my custom pcm?

EDITS: 
After downloading Audacious, I discovered that it will recognize the pcms in my .asoundrc file:
[http://i.imgur.com/9MAiYpA.png](http://i.imgur.com/9MAiYpA.png)
However, it gives me an error when I go to play them:
"ALSA error: snd_pcm_hw_params_set_access failed: Invalid argument."

Independent of that finding, I can confirm that Audacious has stable LADSPA support:
[http://i.imgur.com/UqcWi4R.png](http://i.imgur.com/UqcWi4R.png)

However, it'd be preferable to use deadbeef, if possible; because Audacious will read my custom pcms, I have faith that db could also read them, though i don't know how to accomplish this (I will do some research on this).  If any help can be given, I would appreciate.

---

### Post by tgalati4 on 2013-10-11
I have not used deadbeef, although I do like Brent's chopped liver.  I have used audacious extensively, but I have not done any ladspa work with it.  Perhaps you need a ladspa server running so that your highpass and lowpass have a device to run them.  Again, this is beyond my experience.

---

### Post by Elastic_Potential on 2013-10-12
If that's the case, you make like CorneDBeeF player ;)  and no worries; you've been great help as it is.

So I finally solved both problems:
1) have a working .asoundrc file with both high and low pass filters
2) it's showing up and working fine in deadbeef

With a little inspiration from some electrical engineering guides on making actual filters I read about not long ago, I solved it by making two instances of each filter for the both Left and Right channels.  Then, I tied them all together with a plug pcm called "bandpass"; here, per the suggestion of an Arch forum user, I added a parameter which adds a description and "show on" (assuming this is boolean), and this made it show up in the Deadbeef output modules list.  

At this point, I suppose it's fair to mark this thread as solved; however, I have this feeling like my solution was sloppy because there are two instances of each plugin per filter; so, if anyone has advice for cleaning it up, I would be all ears.  Below is the final copy of my .asoundrc file, which is working wonderfully.

Thanks for all the help.

```

#This one actually works
#~/.asoundrc

# Bandpass plug
# this will tie everything together.
# Because it contains the "hint" parameter,
# it will be the only PCM to show up in DeaDBeeF player
# (and, likely, other players as well)
pcm.bandpass {
    type plug
    slave.pcm "highpass"
    hint {
        show on
        description "Bandpass filter"
    } 
}


# Simple high pass filter
# the value is stupid high for testing purposes, so
# remember to change the control value to something reasonable.
# on my pc, I have it set at 60 (which is 60 Hz)
pcm.highpass {
    type ladspa
    slave.pcm "lowpass";
    path "/usr/lib/ladspa";
    channels 2
    plugins {
        0 {
            label hpf
        policy none
        input.bindings.0 "Input";
        output.bindings.0 "Output";
        input {
            controls [ 14000 ]
            }
        }
        1 {
        label hpf
        policy none
        input.bindings.1 "Input";
        output.bindings.1 "Output";
        input {
            controls [ 14000 ]
            }
        }
    }
}

# Simple Low pass filter
# this one only attentuates sounds above the higher range
# of human hearing (20,000 Hz, thus, control value is 20000)
pcm.lowpass {
    type ladspa
    slave.pcm "primary";
    path "/usr/lib/ladspa";
    channels 2
    plugins {
        0 {
            label lpf
        policy none
        input.bindings.0 "Input";
        output.bindings.0 "Output";
        input {
            controls [ 20000 ]
            }
        }
        1 {
        label lpf
        policy none
        input.bindings.1 "Input";
        output.bindings.1 "Output";
        input {
            controls [ 20000 ]
            }
        }
    }
}

# This defines the default hardware device
# You can find this value with "aplay -l"
pcm.primary {
    type plug
    slave.pcm "hw:1,0"
}

```

---

### Post by tgalati4 on 2013-10-12
I'm glad that you have it figured out.  ALSA is quite powerful, but it also has a learning curve.  Normally you would use the EQ in any of a number of music players, but you have found a solution that fixes a specific problem and works with your setup.  Congratulations for that.

---

### Post by Elastic_Potential on 2013-10-13
> **tgalati4 said:**
> Normally you would use the EQ in any of a number of music players, but you have found a solution that fixes a specific problem and works with your setup.

Since I'm more or less dependent on my netbook, I try to use as few resources as possible (I love Lubuntu for this reason).  Deadbeef with alsa uses around 2% - 3% cpu.  Enabling its equalizer, flat or not, bumps this up between 8% - 12%, which produces a noticable amount of heat; nevermind that 16 flat bands is kinda overkill imo.  My current setup just gives me the benefits of this without the cpu draw/heat output.

---

