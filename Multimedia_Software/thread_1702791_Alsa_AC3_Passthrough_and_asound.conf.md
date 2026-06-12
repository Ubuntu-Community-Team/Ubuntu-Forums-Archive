---
title: "Alsa AC3 Passthrough and asound.conf"
date: 2011-03-08
forum: Multimedia Software
---

### Post by Ted_C on 2011-03-08
Hi all.

This will be the first question I'm posting.  First - a little about who I am.  I've been an Ubuntu user for a little over a year now - running XBMC live on an acer aspire revo.

Recently - I moved over to Ubuntu 10.10 Maverick Meerkat generic and upgraded my hardware to a self built HTPC.  

The reason I moved to a new HTPC:  I wanted more than just XBMC on my home theatre.  I wanted a desktop to watch youtube and/or surf the net.  I wanted my own DVR.  And I wanted XBMC.

My main goals of the HTPC are in XBMC - have flawless playback of 1080p content with my ripped movies and tv shows (all are .m4v with .h264 and two audio tracks - AAC and AC3).  If I choose the AC3 Soundtrack - I want true Dolby Digital - not simulated copying of AAC to 6 channels.  I don't have any goals for the DVR yet - as I haven't used it enough.

I - like many other people - have struggled with getting sound to work through HDMI on a GEForce GT 430 Fermi card.  After about 12 re-installs, I think I have the setup I like.


[LIST]
[*]I have removed pulseaudio ([here]("http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html") and [here]("http://www.jeffsplace.net/node/12") - two steps were taken since it appeared Pulse was still trying to update itself after purging)
[/LIST]

[LIST]
[*]Install the NVidia "additional drivers"
[*]Fix Plymouth ([here]("http://ubuntu4beginners.blogspot.com/2011/01/fix-ugly-plymouth-usplash-in-ubuntu.html"))
[*]Run Update manager and let it install 247 updates
[*]Followed the instructions [here]("ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#_trouble_shooting") and [here]("http://ubuntuforums.org/showthread.php?t=1668737") to get sound working on Alsa - I had more confidence from the second example - as the author takes you through correctly identifying your correct device and updating the initramfs grep eld_valid /proc/asound/NVidia/eld*
[*]sudo update-initramfs -u
[*]I did not set-up a modprobe.d sound.conf entry.  I'm using either "default" or hw:1,9 in my applications.
[*]I did not get the aplay to work on wave files with the included instructions (NVidia:hdmi).  I did get it to work with my default device though.
[/LIST]
So now to my question.  I am using the following /etc/asound.conf settings:
```
pcm.dmixs51 {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,9"
        format S16_LE
        rate 44100
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 4096
   }
}
pcm.!default {
    type plug
    slave.pcm "dmixs51"
    slave.channels 6
    route_policy duplicate
}

```This works great from movieplayer and from youtube.  I get six channels of sound from a 2 channel source (it's not truly surround-sound - as it just duplicates the 2 channels into 6 channels).  There's no crackling or distortion either.

In VLC player - I try to play some of my encoded .m4vs (with two audio tracks - AAC and AC3).  When I choose the Audio = Alsa and Audio device from preferences and set it to default - the AAC soundtrack functions just like I would like it to - with the 2 channels duplicated to the 6 channels my receiver supports.
When I choose the 2nd audio track (AC3) - instead of switching to a straight pass-through like I would like - it continues to run through the default profile I've defined in asound.conf and duplicates two channels to 6 channels.

In VLC player - If I change the ALSA device from default to hw:0,9 - the 2 channel source (AAC) only outputs two channels (where I'd rather have the 2 channels duplicated to 6 channels)  but the AC3 source outputs true pass-through (and my receiver switches over to Dolby Digital automatically).

So is there a way to have the best of both worlds - where AAC (or other 2 channel sources)  is automagically output to 6 channels and AC3 is automagically passed through using one PCM alias (i.e. pcm.!default) defined in my asound.conf?

Thanks and sorry for the long winded thread...

---

### Post by Ted_C on 2011-03-10
Okay - after letting this simmer for the week - I'm thinking this idea isn't possible.  Alsa defines the device to play content - content doesn't drive what alsa should do.  is this a fair statement?

---

