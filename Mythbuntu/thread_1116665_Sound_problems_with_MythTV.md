---
title: "Sound problems with MythTV"
date: 2009-04-05
forum: Mythbuntu
---

### Post by neanderthalman on 2009-04-05
I've been fighting with the sound from my TV tuner for a few hours now, and it's about time I asked for a little guidance.

I started out with a two second lag between the video and sound.  I learned that it means that my TV tuner was outputting sound directly to the sound card, while the video was being written to disk then replayed.  In my particular case, my card deviates from the documentation by outputting sound via a CD header on the card, not line in.  Regardless, following the directions found [_here_](http://www.mythtv.org/docs/mythtv-HOWTO-7.html#ss7.2) with that minor change I was able to fix the lag.  The sound now lines up perfectly with the video.

Unfortunately, it's now extremely distorted.  It's tinny, almost metallic sounding.  Everything I've found suggests that it is due to the volume levels set too high.  I've tried all possible combinations, even down to about 5% volume, but the sound is still just as distorted.  The only change is that I need to crank up the external amp. ;)

Before "capturing" the sound, the sound was output cleanly, so logically, I think it has something to do with the process by which the sound is captured and then replayed, perhaps an issue with the audio codec or what-have-you.  However, I'm grasping at straws here.

If anyone has experienced a similar issue, or can point me in the right direction, it would be appreciated.

---

### Post by klc5555 on 2009-04-05
> **neanderthalman said:**
> I've been fighting with the sound from my TV tuner for a few hours now, and it's about time I asked for a little guidance.

I started out with a two second lag between the video and sound.  I learned that it means that my TV tuner was outputting sound directly to the sound card, while the video was being written to disk then replayed.  In my particular case, my card deviates from the documentation by outputting sound via a CD header on the card, not line in.  Regardless, following the directions found [_here_](http://www.mythtv.org/docs/mythtv-HOWTO-7.html#ss7.2) with that minor change I was able to fix the lag.  The sound now lines up perfectly with the video.

Unfortunately, it's now extremely distorted.  It's tinny, almost metallic sounding.  Everything I've found suggests that it is due to the volume levels set too high.  I've tried all possible combinations, even down to about 5% volume, but the sound is still just as distorted.  The only change is that I need to crank up the external amp. ;)

Before "capturing" the sound, the sound was output cleanly, so logically, I think it has something to do with the process by which the sound is captured and then replayed, perhaps an issue with the audio codec or what-have-you.  However, I'm grasping at straws here.

If anyone has experienced a similar issue, or can point me in the right direction, it would be appreciated.

Could depends on what your tuner card is, and whether it's getting analog or digital.

For software-encoding analog, some cards (e.g. the pchdtv-5500 being a notorious example) have to have the bit-sampling rate set to 48000 rather than Myth's default 32000. This doesn't apply to hardware-encoding Mpeg2 analog cards like the Hauppauge PVR 150, etc. 

The change is done both in the backend setup, in the Tuner Card section for your particular analog card, and in the frontend setup, under all the Recording Profile categories for your card, i.e. "default" "high quality" ..etc.

If you're having trouble with hardware-encoding analog, or with a digital tuner, then I'm not sure what the issue might be.

---

### Post by neanderthalman on 2009-04-05
> **klc5555 said:**
> Could depends on what your tuner card is, and whether it's getting analog or digital.

For software-encoding analog, some cards (e.g. the pchdtv-5500 being a notorious example) have to have the bit-sampling rate set to 48000 rather than Myth's default 32000. This doesn't apply to hardware-encoding Mpeg2 analog cards like the Hauppauge PVR 150, etc. 

The change is done both in the backend setup, in the Tuner Card section for your particular analog card, and in the frontend setup, under all the Recording Profile categories for your card, i.e. "default" "high quality" ..etc.

If you're having trouble with hardware-encoding analog, or with a digital tuner, then I'm not sure what the issue might be.

It's a software encoding analog tuner, a couple years old now - Asus TV FM 7135 (saa7134) <--not a typo

I tried various sampling rates, based on your suggestion, and it didn't help.

However, as it always seems to be the case, you definitely pointed me in the right direction - in the "recording profiles", the volume for the capture was set to 90% - apparently ignoring the value set by alsamixer.  I moved the slider down to 70% and lo and behold, it worked!

Thanks for the help!  Now lets see what the next problem will be.....

---

