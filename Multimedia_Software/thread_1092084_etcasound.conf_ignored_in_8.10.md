---
title: "/etc/asound.conf ignored in 8.10?"
date: 2009-03-10
forum: Multimedia Software
---

### Post by xianthax on 2009-03-10
first i suppose i should explain what i'm trying to do:

i'm attempting to add dynamic range compression (DRC) and limiting to a selectable audio output.   DRC effectively makes louder sounds quieter, and quieter sounds louder, ie you can watch an action movie and be able to hear the dialog without the explosions waking the neighbors.  

the approach i've been trying to use is to add an ALSA device and use the dysonCompress and fastLookaheadLimiter plug ins on the plug to create the effect, then i can just select this ALSA device in the desired application (mplayer or vlc in this case) when i want the effect enabled, and use the default device (routed through PA) for music and other sounds.  

To this end i've added the following to a previously non-existant /etc/asound.conf (tried in .asoundrc too 

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
                  #peak limit, release time, fast ratio, ratio
                  controls [0 1 0.5 0.99]
              }
          }
      ]
  }
 pcm.ladcomp_limiter {
      type ladspa
      slave.pcm "plughw:0,0";
      path "/usr/lib/ladspa";
      plugins [
          {
              label fastLookaheadLimiter
              input {
               #InputGain(Db) -20 -> +20 ; Limit (db) -20 -> 0 ; Release time (s) 0.01 -> 2
               controls [ 20 0 0.8  ]
              }
          }
     ]
  }

```

aplay -L doesn't show the new device, in fact, nothing i do in this file seems to have any effect (i am restarting ALSA of course).

is 8.10 ignoring these files and using some other method for configuration? 

cheers,

xian

---

