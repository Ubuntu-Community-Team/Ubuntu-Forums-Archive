---
title: "Audio uses too much cpu"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by antreas on 2007-11-04
Hi! This is my first post and i am happy to say it's about a problem fixed. I have an old pentium 4 1.7Ghz , 512 RDRAM,SBLive 5.1 pc with gutsy. After installation i noticed that every audio application uses too much CPU. Rhytmbox (gstreamer)used around 25-30% , MPlayer around 20% ,  and xine around 12-15% of my cpu(all numbers reported by top). My computer is old but 30% cpu of just playing an mp3 was ridiculous. 

After many hours of googling i found out about alsa dmix and resampling. Then i noticed that even my SBLive supports HWMIX the default configuration file of asoundrcconf(which i used for setting the default card) enabled dmix with resampling at 48000 which apparently used up my old cpu.

**default .asoundrcconf **
```
 # ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card Live
defaults.ctl.card Live
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format S16_LE
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device

defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device

defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device

defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device

defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device

defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device

defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device

defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device

defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device

defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device

defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off
```

**HOW I FIXED IT:**
I changed my ~/.asoundrc file to the following. Surround sound is enabled also and it works with media players but not with speaker-test(i don't why exactly).

**.asoundrc **
```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
#</home/antreas/.asoundrc.asoundconf>
pcm.Live {
   type hw
   card 0
   device 0
   subdevice -1
   nonblock 1
   slave.pcm "surround51"
   slave.channels 6
   route_policy duplicate
}
       
ctl.Live {
  type hw
  card 0
  device 0
}
```

Now Rhythmbox uses around 0.33% when minimized!:):)

Should i file a bug for this?And where shall i do it?

---

