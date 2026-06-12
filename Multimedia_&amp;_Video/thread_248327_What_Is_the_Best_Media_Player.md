---
title: "What Is the Best Media Player?"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by azraelx401 on 2006-08-31
I just want to get a few people's view on what the best media player would be for video's (avi, quicktime, wmv, etc)?  And what would be the best codecs to download?


I had a problem a bit ago where i downloaded some bad plugins and my sound card would crash on boot up.  Don't want that to happen again now that I have it back up.

---

### Post by LKRaider on 2006-08-31
I use Totem ( gstreamer ) on my Ubuntu box, and Xfmedia ( xine ) on my Xubuntu laptop, and both are working really well for me after having installed the extra codecs provided, including the w32codecs.

---

### Post by zettberlin on 2006-09-01
I got all 3 major players installed:

vlc, xine and mplayer

In every case i try VLC first and use xine or mplayer, if this fails only.

Main reasons:

1.) I like the interface of vlc best
2.) VLC is the most stable and tolerates to run without access to the sounddevice (mplayer crashes totally, if jackd is running. Xine complains quite annoying).

For all my musicfiles i use alsaplayer: the only player i know, that starts playing via jack immediately (one can hear a track playing even before the GUI is up ;-) :-) )

---

### Post by Cynical on 2006-09-01
I use vlc mostly because of the interface and the fact that I dont *need* extra codecs. Totem (xine) is what I use to play wmv files.

---

### Post by floogy on 2006-09-01
> **zettberlin said:**
> 
2.) VLC is the most stable and tolerates to run without access to the sounddevice (mplayer crashes totally, if jackd is running. Xine complains quite annoying).

For all my musicfiles i use alsaplayer: the only player i know, that starts playing via jack immediately (one can hear a track playing even before the GUI is up ;-) :-) )

I like mplayer very much:

```
~$ mplayer -ao alsa:device=jackplug /home/gerhard/Streamripper_rips/jazzradio.wma
[...]
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Video: no video
Starting playback...
A:  29.8 (29.7) of 0.0 (unknown)  0.9%
```

But I must admit, that it 

cat ~/.asoundrc
```
#JACK http://gentoo-wiki.com/HOWTO_Jack#Any_application_that_uses_ALSA

pcm.jackplug {
    type plug
    slave { pcm "jack" }
}

pcm.jack {
    type jack
    playback_ports {
        0 alsa_pcm:playback_1
        1 alsa_pcm:playback_2
    }
    capture_ports {
        0 alsa_pcm:capture_1
        1 alsa_pcm:capture_2
    }
}
#EndJACK
```

mplayer plays the videos, although jackd isn't running.
But it doesn't like xruns at all...

---

### Post by capsid on 2006-09-01
trying to pick the "best" media player seems impossible, because different media require different features, but I use VLC %90 of the time if I just want to experience the media and not fuss with the player.  It's nice for anime cause you can get at the different audio/subtitle tracks by right clicking in the window.  

Some disadvantages of VLC (and I'm really reaching here:)

--once you drag something into a VLC playlist, it cant change position on the list, right?  maybe that's just the windows version, i dunno.
--shoutcast stations will still play, but last time shoutcast got updated it broke VLCs ability to search the station list. :(
--chokes on some .movs, in my experience.  although it could have just been bad encoding (the only time i mess with .movs is when  my mac friend exports stuff from shake).   

So yeah, go VLC for zero config and no codec hunting.

---

### Post by azraelx401 on 2006-09-02
thanks alot everyone.  i've pretty much desided to try a few of them and keep the ones I like.

---

### Post by Rhapsody on 2006-09-02
Despite my short amount of time running it, I've found MPlayer to be very nice. In the past, I've used Winamp, Windows Media Player, Zoom Player, VLC media player, and Media Player Classic. MPlayer is my favourite so far.

---

### Post by bwanab on 2006-09-09
Since nobody has mentioned it, I nominate Rhythmbox. It is well behaved and very intuitive. Only downside is that it isn't jack enabled. When I'm doing audio work, I use alsaplayer as a jack client.

---

### Post by dolson on 2006-09-09
Doesn't Rhythmbox only play audio? The original poster was talking about video. If I am wrong, then I learned something today.

---

