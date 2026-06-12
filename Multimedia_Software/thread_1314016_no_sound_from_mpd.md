---
title: "no sound from mpd"
date: 2009-11-04
forum: Multimedia Software
---

### Post by bobdobbs on 2009-11-04
Hi all.
I've just done a fresh install of koala on my desktop.
Most everything is fine, and I can play DVD's, cd and mp3's.

Trouble is, I get no sound when I play something with mpd.

I use gmpc as a front end. And I can select tracks and play them. According to gmpc the track is playing. But no sound comes from my system.

The only lines in mpd.log are these:
```

No protocol specified
XOpenDisplay() failed

```

How do I troubleshoot this issue ?

---

### Post by bobdobbs on 2009-11-06
bump

---

### Post by bobdobbs on 2009-11-08
bump

---

### Post by pheleven on 2009-11-09
I get the same errors in my log when MPD starts up. I do, however, get sound via MPD (and other sources).

I can not, however, control the volume through MPD - I get this error just after the one(s) you listed : 

No protocol specified
XOpenDisplay() failed
Nov 09 02:44 : can't find alsa mixer control "PCM" (this changes to any mixer I try - and yes, I have a PCM mixer showing up and working with alsamixer)

This is a new bug introduced in Karmic. My system was working fine with MPD until the new heavy Pulseaudio integration. On the MPD mailing lists there are others with issues surrounding pulseaudio/Karmic. Some like yours with no sound.

Unfortunately, you can no longer uninstall Pulseaudio without extreme repercussions (such as ubuntu-desktop being removed with it). 

This is a MASSIVE gimp to this computer I'm using as my music/media center and I may have to move away from Ubuntu.

Why is Pulseaudio being so heavily integrated when it is clearly hated by a big chunk of the community?

---

### Post by cweiske on 2010-04-27
The problem of
```
can't find alsa mixer control "PCM"
```
can be solved by disabling ALSA output and enabling [PulseAudio]("http://mpd.wikia.com/wiki/PulseAudio") output.

In /etc/mpd.conf, just disable all alsa output lines and enable the pulseaudio ones:

```
#audio_output {                                                                                                                                                                   
#       type            "alsa"                                                                                                                                                    
#       name            "My ALSA Device"                                                                                                                                          
#       device          "hw:0,0"        # optional                                                                                                                                
#       format          "44100:16:2"    # optional                                                                                                                                
#       mixer_device    "default"       # optional                                                                                                                                
#       mixer_control   "PCM"           # optional                                                                                                                                
#       mixer_index     "0"             # optional                                                                                                                                
#}                                                                                                                                                                                
[...]
audio_output {
        type            "pulse"
        name            "My Pulse Output"
#       server          "remote_server"         # optional                                                                                                                        
#       sink            "remote_server_sink"    # optional                                                                                                                        
}
```

- now I can set loudness of the music via mpd clients again.

---

