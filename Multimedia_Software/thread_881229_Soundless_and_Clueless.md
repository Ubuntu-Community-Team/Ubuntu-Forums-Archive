---
title: "Soundless and Clueless"
date: 2008-08-05
forum: Multimedia Software
---

### Post by zoe-scutterbug on 2008-08-05
hiya please kindly help

once upon a time i had sound ...life was cool ...everything worked beautifully ...oh happy days.
But then I messed things up ...such a mess that i haven't a clue how i did it...and the more i try to fix it ...( i have tried following as best a techno dummy can this and a few guides on this list) the less it seemed that sound is likely to return...it seems to be getting worse. Even tried a big reinstall...think i might do it again...and be more selective. I run Opengeu 98% of the time , but i also have UbuntuStudio, Xubuntu and Kubuntu installed too ....thats poss part of my problem...why have one application when you can have five.

Streaming sound on secondlife comes out in a stuttering mess.. but i get no sound on bbc iplayer or Zatto ...these all worked ..my dvd player seems to work for VLC but no longer for XBMC ...

i use flock mostly but also firefox

i have an nvidia graphics card
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    Subsystem: ASUSTeK Computer Inc. Unknown device 81cb
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
    Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>


 I also recently brought a usb external creative blaster surround 5.1 (driver emu10k1) when i started not getting stuttering sound...but it is as quiet as a deadfish...with a little blue light to show me it is as least on


anyways lets start at the miserable beginning

zoe@****-knows:~$ aplay -L
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:36:0:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /home/zoe/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
zoe@****-knows:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:36:0:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /home/zoe/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:214: control open (0): Invalid argument
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:36:0:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /home/zoe/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:214: control open (1): Invalid argument
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:36:0:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /home/zoe/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:214: control open (2): Invalid argument
zoe@****-knows:~$ 


so i look in my .asoundrc file

pcm.!default {
  type pulse
}

ctl.!default {
  type pulse
}

pcm.pulse {
  type pulse
}

ctl.pulse {
  type pulse
}

pcm.equalized {
  type plug
  slave.pcm "equalizer";
}

pcm.equalizer {
  type ladspa

  # The output from the EQ can either go direct to a hardware device
  # (if you have a hardware mixer, e.g. SBLive/Audigy) or it can go
  # to the software mixer shown here.
  slave.pcm "plughw"
  #slave.pcm "plug:dmix"


???????
and i haven't a clue

heaps of appreciation in advance

zoe
                                                                                               __________________

---

### Post by markbuntu on 2008-08-05
Rename your home/zoe/asoundrc file and see if that fixes things. You don't really need one.

---

### Post by kostkon on 2008-08-05
I assume you have to followed this [how-to]("http://ubuntuforums.org/showthread.php?t=789578"), am I right? It seems that your *.asoundrc* file is malformed, you forgot to close some brackets. According to this how-to, your file should look like this:
```
pcm.!default {
  type pulse
}

ctl.!default {
  type pulse
}

pcm.pulse {
  type pulse
}

ctl.pulse {
  type pulse
}

pcm.equalized {
  type plug
  slave.pcm "equalizer";
}

pcm.equalizer {
  type ladspa

  # The output from the EQ can either go direct to a hardware device
  # (if you have a hardware mixer, e.g. SBLive/Audigy) or it can go
  # to the software mixer shown here.
  slave.pcm "plughw"
  #slave.pcm "plug:dmix"

  # Sometimes you may need to specify the path to the plugins,
  # especially if you've just installed them.  Once you've logged
  # out/restarted this shouldn't be necessary, but if you get errors
  # about being unable to find plugins, try uncommenting this.
  path "/usr/lib/ladspa"

  plugins [
    {
      label mbeq
      id 1197
      input {
       #this setting is here by example, edit to your own taste
       #bands: 50hz, 100hz, 156hz, 220hz, 311hz, 440hz, 622hz, 880hz, 
       #       1250hz, 1750hz, 25000hz, 50000hz, 10000hz, 20000hz
       #range: -70 to 30
        controls [ -1 -1 -1 -1 -5 -10 -20 -17 -12 -7 -6 -5 -5 0 0 ]
      }
    }
  ]
}
```

---

### Post by zoe-scutterbug on 2008-08-06
easy peasey

brilliant
i have sound back on zattoo and bbc iplayer ...thank you

my sound on secondlife (its where i waste too much time)  however remains very warbly  :(

what i did...firstly i fixed the asoundrc file as suggested ...then i renamed it

any suggestions

zoe (back in  12hours)

---

### Post by zoe-scutterbug on 2008-08-06
...nudge...

any kind recommendations on how to solve the stuttering sound on secondlife?

plus if anyone else mucks about with secondlife...have they got voice to work...i must admit i have never tried voice over the internet..not even skype...so not sure where to begin...any recommendations would be cool

big thank you in advance

zoe

ps hi Koston...i think i probably did try to follow that guide...i tried lots of things, but since i failed to correctly copy that .asoundrc file i wonder what else i might of failed to do???

---

### Post by markbuntu on 2008-08-06
There is some info on setting up the pulseaudio daemon for skype here:


[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

It might also work for secondlife.

---

