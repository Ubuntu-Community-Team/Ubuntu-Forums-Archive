---
title: "video volume"
date: 2012-10-31
forum: Mythbuntu
---

### Post by AlecJ on 2012-10-31
Is there a setting to adjust the independent volume from the Video and TV?

I have to increase the volume on Video playback and then if I forget to reduce the volume when going back to TV, it makes the windows shake! not to mention the neighbours?

I can't find anything in the menu's for the internal player I hoping their is a .conf file somewhere.

running Myth .25, 12.04.1
onboard sound card HDA ATI SB Realtek  ALC887-VD 6 channel

---

### Post by Rotak on 2012-10-31
Did you try changing the audio-track on the video? If it plays back the AC3 track, while you only use stereo output, volume may be very low.

At least I don't know of a function like that. My TV has something like that, though. But not in MythTV. I googled "mythtv volume normalization", and I don't expect it to be implemented soon.

---

### Post by AlecJ on 2012-11-02
I also googled "mythtv volume normalization" and found this web site
[HTML]http://blog.trenchcoatsoft.com/2009/11/mythtv_volume_leveling.html[/HTML]many thanks to Ross for his Blog

which says to use LADSPA plug in

I followed 

install Ladspa
```
sudo apt-get install ladspa-sdk swh-plugins
```create /etc/asound.conf

```
pcm.ladcomp {
      type plug
      slave.pcm "ladcomp_compressor";
  }
 pcm.ladcomp_compressor {
      type ladspa
      slave.pcm "ladcomp_limiter";
      path "/usr/lib/ladspa";
      plugins [
          {
              label dysonCompress
              input {
                  controls [0 1 0.5 0.99]
              }
          }
      ]
  }
 pcm.ladcomp_limiter {
      type ladspa
      slave.pcm "default";
      path "/usr/lib/ladspa";
      
      plugins [
          {
              label fastLookaheadLimiter
              input {
               controls [ 15 0 0.8  ]
              }
          }
     ]
  }
```Then manually enter  ALSA:ladcomp into audio output device in the frontend.
Restart frontend.

So far I have sound! 
the TV was much louder that before and most Video playback is at the same level at the TV.
Some Videos are still very quiet, that maybe how they were ripped?

So I'm going to test it see how it goes

---

### Post by AlecJ on 2012-11-08
Have had to change back to 5.1 surround as play back of VOB files caused a full volume modem type sound that shook the house!
No idea why yet?

but on TV it did seem to keep the ad's at the same volume as the rest of the TV.

---

