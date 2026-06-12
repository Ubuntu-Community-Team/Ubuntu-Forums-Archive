---
title: "Why is sound so quiet?"
date: 2009-08-14
forum: Multimedia Software
---

### Post by ThanosIsKing on 2009-08-14
Hey, I've got a weird question. Before I switched to Ubuntu I was using Windows Vista, and I could routinely hear the sound coming out of my speakers from as far away as the kitchen in my apartment (which is quite a feat; it's on the other side of a modestly-sized apartment, with several walls in between). However, now that I switched to Ubuntu I have found myself having to quite literally put my ears right next to the speakers in order to hear the sound. This problem seems to vary depending on the program I'm using at the time. When I watch video or listen to music with VLC, for instance, I can hear the audio quite clearly (but not on par with the volume capabilities under Vista). When I use the built-in Movie Player, the volume is a bit quieter, but I'm still able to make out what's being said. However, when I'm on YouTube, I'm forced to do the aforementioned "ear to the speakers" thing to hear anything. All of these occur with the audio already pumped to the maximum. Is there something that I can do in order to increase the audio "power" in Ubuntu for things like YouTube and the like?

For reference, I'm using Ubuntu version 9.04, I'm running on a Toshiba Satellite A135-S4427 laptop, and my sound card is the built-in Intel 82801G (ICH7 family) HD Audio Controller rev 02.

---

### Post by ekaren3376 on 2009-08-14
Try these** changes**:
Go to **Applications - Accessories - Terminal**    Type 'alsamixer'
Set all sliders to maximum, then Close

Then go to **System - Preferences - Sound**
In Devises -  set Playback to Alsa ,  set Sound Capture to Alsa
all others to Autodetect
In Default Mixer Track, find your audio device, then Close

Go to **Sound ico**n at top right of monitor screen, right click, ensure Master slider is at maximum. Close
Then right click sound icon again, go to Preferences.  Ensure your audio device is shown.

This worked for me.

---

### Post by gumblina on 2009-08-14
thanks for this! i didn't know why it was so much quieter on the ubuntu side compared to the xp side and now its fixed :)

---

### Post by sinisterstuf on 2011-05-30
I think I have a similar problem but I can't fix it.

If I listen to music on my mp3 player my headphones go quite loud, similarly if I use them on a Windows computer, this one used to have Windows on for example. However in Ubuntu it's much quieter and if I try to make it louder in the system preferences it gets distorted. Any idea what I can do?? I tried the above suggestion and nothing changed. All the output sliders on alsamixer were already at max! :(

---

