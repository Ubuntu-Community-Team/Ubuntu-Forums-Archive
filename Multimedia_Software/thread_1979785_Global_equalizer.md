---
title: "Global equalizer"
date: 2012-05-14
forum: Multimedia Software
---

### Post by samwillc on 2012-05-14
Hi everyone,

I am having trouble installing a global equalizer on a new install of ubuntu 12.04.

I saw the other thread about 'pulseaudio' but there are loads of different commands for different versions of linux, I am confused as to how to even follow the guides. I am not confident yet using the command line as I don't know what the commands are actually doing, of course I am learning day by day.

I even tried downloading linux drivers from Realtek (I used to use Realtek HD audio on win7 which included an equalizer). I tried to install these, restart and the system froze up on the opening ubuntu splash screen, so back to the drawing board!

Has anyone got a simple to follow guide? Or even a way to install via the software centre? Any guidance would be most helpful. Thanks.

Sam.

---

### Post by oldos2er on 2012-05-14
Moved to Multimedia & Video.

---

### Post by Enigmapond on 2012-05-14
This, I believe, is only available for 10.04. I had it with Lucid but saw it was not available for 12.04 when I upgraded. Currently that is the only one available for Ubuntu so maybe they are working on it for Precise...

---

### Post by samwillc on 2012-05-14
Ok thanks, will keep an eye out for new developments.

Sam.

---

### Post by c-m on 2012-12-28
Any update. I need some form of equaliszer for my system to control the global output, not just the output from one specific program

---

### Post by samwillc on 2013-01-12
Hi, I still don't have a decent solution!

I was thinking of trying to get a few people together to make one. I'm not much of a coder though so could test rather than create.

I am surprised there is no equalizer, windows has one with realtek HD audio (download the manager and there it is, full on custom EQ, easy), mac has boom ( [http://www.globaldelight.com/boom/](http://www.globaldelight.com/boom/) which works brilliantly), no idea why none for linux! It's a really good thing to have rather than individual equalizers on each program.

Sam.

---

### Post by logan_2k6 on 2013-06-02
there is alsaequal (search "alsaequal" in software manager ..it has a diffrent name there but dont worry)
[http://www.thedigitalmachine.net/alsaequal.html](http://www.thedigitalmachine.net/alsaequal.html)
and there is also pulse equilizer
[http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)
which is a crap....at least for me is a crap...sound get clipped and distorted and god knows what else...

both are system wide equlizers
both are useless for me
i dont know how to make alsa equlizer to work with pulseaudio so i had to disable pulseaudio for good.
but even so i still get sound only on front spearkers..so i guess my entire surround system (7.1) is useless.

well i suggest to look more into alsaequal and also ladspa (also for alsa).
goodluck :) u'll need it

---

### Post by samwillc on 2013-06-02
I gave up on ubuntu a few months back because I was always jumping through hoops just for features that in my opinion, should be present in an OS that is trying to reach out to the mainstream. I'm happy with OSX at the moment.

This looks promising though:

[http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)

I'd love to go back to ubuntu as the freedom it gives is superb, plus you can theme it out any way you like. Of course, the other drawback is the power problems which can make a laptop battery last about an hour, that is unless you buy a laptop with the exact hardware required for ubuntu. All very different from the picture they paint on the ubuntu homepage, perhaps they could also add "may not work on your machine".

---

### Post by logan_2k6 on 2013-06-02
well i finally manage to create (as in copy/paste from multiple sources) a pretty much good eq (at least for me) 
this configuration does a nice up mix from 2 to 7.1 channels so one of my problem solved. also the equlizer itself works of course on all 7.1 channels...so pretty much my problems got solved. of course im still testing it right now. hope it works for you too.

edit: forgot to say that u have to disable pulseaudio. Edit etc/pulse/client.conf and add autospawn = no and also etc/pulse/daemon.conf and add daemonize = no

```
# Install alsaequal and also swh-plugins and Audacious to get equlizer values
# usefull link for caps plugins (id and label) http://quitte.de/dsp/caps.html#Eq

pcm.upmix71 {
    type upmix
    slave.pcm "hw:0,0"
    channels 8
}

pcm.eq {
  type ladspa

  # The output from the EQ can either go direct to a hardware device
  # (if you have a hardware mixer, e.g. SBLive/Audigy) or it can go
  # to the software mixer shown here.
  #slave.pcm "plughw:0,0"
  slave.pcm "plug:upmix71"

  # Sometimes you may need to specify the path to the plugins,
  # especially if you've just installed them.  Once you've logged
  # out/restarted this shouldn't be necessary, but if you get errors
  # about being unable to find plugins, try uncommenting this.
  path "/usr/lib/ladspa"
#  channels 8
  plugins [
    {
      label Eq
      id 1773
      input {
        # These are the values copied straight from the EQ in Audacious
        # u can see each band for each value @the above like
    # controls [ 4.8 4.32 0.96 -2.88 -2.88 -3.36 -1.92 1.92 2.88 0.95 ]
     controls [ 5.6 7 6 3.5 3 3.5 5 5.9 5.9 3.9 ]
      }
    }
  ]
}

# Redirect the default device to go via the EQ - you may want to do
# this last, once you're sure everything is working.  Otherwise all
# your audio programs will break/crash if something has gone wrong.
pcm.!default {
#pcm.tdefault {
  type plug
  slave.pcm "eq"
}

# Redirect the OSS emulation through the EQ too (when programs are run through "aoss")
pcm.dsp0 {
  type plug
  slave.pcm "eq"
}
```

---

