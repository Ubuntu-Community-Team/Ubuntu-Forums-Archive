---
title: "Getting surround sound to work"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by ar1stotle on 2007-04-24
OK, is there any way to configure 5.1 surround sound in Ubuntu? I'm using onboard Nvidia CK804 audio, and it supports surround sound but afaik it's only doing output on one channel right now. 

Also, any ideas why I would have crackly sound using ZSNES? That's the only program that does it to me at the moment... it's just all crackly and annoying. SNES9x works fine.

---

### Post by disturbed1 on 2007-04-24
*"TRUE"* Surround sound is only supported using Nvidia's closed sourced oss driver. Good part to that is you'll have 5.1 sound on audio that is encoded that way. Downfalls, you'll have to change the sound system to OSS, stereo sound will only come through 3 speakers (Front Left, Front Right, low volume sub), the sound quality isn't that good, and the volume level just isn't there.

The default ALSA module for that sound chip will output to all channels, but not in a surround mode. Your front left and rear left speakers will receive the same information, front right and rear right receive the same, along with the center and sub being matrixed mono.

If you mainly listen to material with 5.1 encoding, and not that much stereo information (music games) then go for the Nvidia OSS drivers.

If you can live with the audio coming out of all of your speakers at a decent volume and sound quality, add the duplicate front, surround jack mode, and channel mode options to the volume control.

In GNOME double click on the volume icon, choose edit - preferences. You'll find the options there.

If you want to go the Nvidia driver route, here's a how to [http://ubuntuforums.org/showthread.php?t=253725&highlight=nvsound](http://ubuntuforums.org/showthread.php?t=253725&highlight=nvsound)

ZSNES emulates the super nintendo sound system. Try playing with the settings in the options.

---

### Post by TheMono on 2007-04-24
I may be wrong here, but a catch for you is if you are using OSS rather than ALSA, you will only be able to have one application using the sound system at once - for example, if you are listening to music and the system tries to beep, it will not be able to.

---

### Post by anmaxp on 2007-04-24
try tweaking the ~/.asoundrc file

there you can add a couple of policies to duplicate the stereo sound through your 5.1 system Currently I own a soundblaster live! 24-bit with a 7.1 speaker system, this is how I got all 8 channels working:

~/.asoundrc

```
pcm.multi {
   type multi;
   slaves.b.pcm "hw:0,0";
   slaves.b.channels 2;
   slaves.c.pcm "hw:0,1";
   slaves.c.channels 2;
   slaves.d.pcm "hw:0,2";
   slaves.d.channels 2;
   slaves.e.pcm "hw:0,3";
   slaves.e.channels 2;
   bindings.0.slave b;
   bindings.0.channel 0;
   bindings.1.slave b;
   bindings.1.channel 1;
   bindings.2.slave c;
   bindings.2.channel 0;
   bindings.3.slave c;
   bindings.3.channel 1;
   bindings.4.slave d;
   bindings.4.channel 0;
   bindings.5.slave d;
   bindings.5.channel 1;
   bindings.6.slave e;
   bindings.6.channel 0;
   bindings.7.slave e;
   bindings.7.channel 1;
}
pcm.!dmix {
   type plug
   slave {
       pcm multi
       channels 8
   }
}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 8
   route_policy duplicate
}
```

It works fine and several applications can use the soundcard at once

hope this helps!

---

### Post by disturbed1 on 2007-04-24
> **anmaxp said:**
> try tweaking the ~/.asoundrc file

there you can add a couple of policies to duplicate the stereo sound through your 5.1 system Currently I own a soundblaster live! 24-bit with a 7.1 speaker system, this is how I got all 8 channels working:

~/.asoundrc

It works fine and several applications can use the soundcard at once

hope this helps!

No need to do that, when the gnome sound app does it auto magically ;). Alsa allows more than one app to play back sound by default.

Thanks TheMono I forgot about that other downfall with OSS.

---

