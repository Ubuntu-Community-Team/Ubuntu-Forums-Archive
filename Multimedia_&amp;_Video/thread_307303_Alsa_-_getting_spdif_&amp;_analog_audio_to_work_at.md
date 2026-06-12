---
title: "Alsa - getting spdif &amp; analog audio to work at the same time"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by juski on 2006-11-26
Hi folks.

I've recently migrated my epia-m 10k MythTV box to Dapper from 'minimyth' where all audio would be routed through spdif as well as through stereo analogue channels.

Everything went well, the install etc and I had myth up & running in next to no time at all.

I'm starting X from rc.local & running ratpoison & mythfrontend from a .xinitrc file.  gdm is no longer allowed to start because I disabled it with sysv-rc-conf.

Anyway I've had a weird issue with alsa recently where I could only get audio to come out of analogue or spdif but not both at the same time.  The default setup is for the IEC958 (spdif) output to carry everything on the pcm channel.  DTS & Ac3 passthru (with xine & mplayer) worked just fine.

I played with various /etc/asound.conf files & found that with (from a working 'minimyth' distro install)

pcm.!default {
    type plug
    slave {
        pcm "hw:0,1"
#         pcm "spdif"
        rate 48000
    }
}

ctl.!default {
    type hw
    card 0
}

I could comment out one of the 'pcm' lines, save the file & restart alsa-utils to get either analogue or spdif to work (but still never both).

All the while alsamixer was showing that my settings were correct - IEC958 output was enabled and its playback slider was set to '0' (which should, according to the alsa docs for snd-via82xx route everything on PCM to spdif aswell).

Many reboots later, and as if by magic - with  pcm "hw:0,1" uncommented in the above asound.conf, I suddenly got sound playing through the analogue AND spdif outputs at the same time!

I checked my mixer settings again and true enough they were exactly the same as before, when it didn't work.

On discovering that I rebooted and tried again - still the same - audio is output through analogue & spdif.

I even went through my console history to see what I'd done differently.  Nothing!  In all cases I'd edited asound.conf & restarted alsa-utils before trying to play an audio file.

The 'random' nature of the problem suddenly going away has me concerned.  If started working all of a sudden so I guess it could also stop working just as randomly.

Anyone have an idea as to what might have happened here?

---

### Post by shrm on 2006-11-29
I have also been trying to get sounds out from spdif and analog in same time. Juski what was your original config that you used in minimyth?

shrm

---

### Post by shrm on 2006-11-29
> **shrm said:**
> I have also been trying to get sounds out from spdif and analog in same time. Juski what was your original config that you used in minimyth?

shrm


The following page was helpfull for me to have both digital and analog output work simultaniously:
[http://knoppmythwiki.org/index.php?page=DigitalAudioHowTo](http://knoppmythwiki.org/index.php?page=DigitalAudioHowTo)

---

