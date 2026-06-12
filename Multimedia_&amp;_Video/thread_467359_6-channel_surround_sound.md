---
title: "6-channel surround sound?"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by qhex16 on 2007-06-07
I've been trying to get my integrated Intel ICH5 audio to output to all my speakers.

I'm not sure if my issue is related to the ALSA setup or my player configuration.

Right now, playing mp3s with totem outputs to the front 2 speakers. I've played around in alsamixer and I set:

Surround Jack Mode: Shared
unmuted Center, LFE
muted Line, Mic (these ports are used for the rear and center/sub outputs)
Channel Mode: 6ch

When I turn on Duplicate Front, the sound also goes to the rear speakers, but I really want it to use the subwoofer (LFE redirection).

In totem, I have set Preferences > Audio > Audio output type to 5.1-channel, but I'm only getting 2 channel playback. What can I do to fix this?

Thanks!

---

### Post by qhex16 on 2007-06-08
Nevermind, fixed it myself. Turns out I had to create a .asoundrc configuration file, as per the instructions at:
[http://gentoo-wiki.com/HOWTO_Surround_Sound#Duplicating_across_all_channels](http://gentoo-wiki.com/HOWTO_Surround_Sound#Duplicating_across_all_channels)

My .asoundrc:

```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/.../.asoundrc.asoundconf>

pcm.!dmix {
   type dmix
   ipc_key 1024
   slave {
       pcm {
		type hw
		card "ICH5"
		device 0
       }
       channels 6
       period_size 2048
       buffer_size 4096
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 6
   route_policy duplicate
}
```

---

