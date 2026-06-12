---
title: "Sound in quake wars"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by AbyssUK on 2007-11-08
Ok guys I need help now i've tried everything I can find...

Firstly all my sound works everywhere xmms/xine etc etc all in 5.1 dvd's play fine
Also Speaker-test -c6 works perfectly

Basically i get this and etqw has no sound

```

----- Initializing Sound System ------
sound system initialized.
--------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.14a
opened Alsa PCM device default for playback
buffer size select failed: Invalid argument
close pcm
dlclose
WARNING: sound subsystem disabled

--------------------------------------
----------- Alsa Shutdown ------------
--------------------------------------
```

After reading some forums I have tried to increase my buffer size in my asound.rc file which is

```
pcm.!dmix {
   type dmix
   ipc_key 1024
   slave {
       pcm "hw:0,0"
       channels 6
       period_size 512
       buffer_size 5460
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 6
   route_policy average
}

pcm.doom {
   type plug
   slave.pcm "surround51"
   slave.channels 6
   route_policy average
}
```

The max I can use for my buffer is 5460 any higher and nothing works then, it can't even initiate the driver.

Nothing like esd is running so it isn't that..

Forcing etqw to use the pcm.doom setting which uses the surround51 gives the same error.

Foricing etqw to use OSS does give me very broken slowed down sound..unplayable

I get full alsa sound using wine for half life 2 and other things!

I have an built in sound card on my asus motherboard it reports as an AC 97 based card

Any help/ideas considered!! Thanks alot

AbyssUK

edit:- Should mention i am running 7.10 and that ETQW does start up and i can play etc just no sound

---

