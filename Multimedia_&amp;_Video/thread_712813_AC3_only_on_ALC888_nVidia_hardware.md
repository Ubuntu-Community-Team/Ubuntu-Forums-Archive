---
title: "AC3 *only* on ALC888 nVidia hardware"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by SteveTPearce on 2008-03-02
I wonder if anyone's come across this before. I'm suddenly left *only* able to get AC3 passthrough from my Ubuntu 7.10 64 bit installation. DTS, Dolby Digital etc all work fine from a DVD played via xine, but nothing else seems to work at all.

The only thing I can recall the may've caused this was that I:
[LIST]
[*]Switched to "safe mode" GNOME to stop compiz messing up video playback
[*]Selected the DTS track from a DVD in xine
[/LIST]
Now, no matter how I log into the box, and whatever I try the only thing that will give audio output is xine playing a DVD.
I have an AV amp connected to the optical SPDIF that's been working fine for years. When I turn on the IEC958 output it registers a signal, when I switch it off it shows "no data". It's like the computer is outputting pure digital silence all the time, no matter what faders I fiddle with.
I have tried purging and reinstalling the ALSA drivers to no avail, and am utterly at a loss.
Any ideas..? Thanks in advance!

Having just connected an analogue lead, it looks like there's no sound at all--analogue or digital..!

---

### Post by knathraak on 2008-03-02
Hi,

I have a very similar problem to yours.  For me, spdif was working fine with all audio.  then I played some videos with an ac3 soundtrack using ac3 passthrough, and all of a sudden /only/ ac3 passthrough works, but nothing else.  Analog out still works, too.

I can't find anything in alsamixer that looks out of place.

I'm running mythbuntu 7.10.
Here's a bug I submitted:
[https://bugs.launchpad.net/bugs/197441](https://bugs.launchpad.net/bugs/197441)

---

### Post by knathraak on 2008-03-02
Hi,

as a workaround,  boot into a livecd session and see if your spdif works right.  if so, then save the alsa state using
alsactl store /path/to/thumbdrive/asound.state

then, after rebooting, see if this fixes it:
sudo alsactl -f /path/to/thumbdrive/asound.state restore.

this worked for me.  not sure what caused the problem to begin with or if this will stick.  hopefully it helps though.

---

### Post by SteveTPearce on 2008-03-02
Good call, knathraak! It occurred to me to try the LiveCD option, but I wouldn't've thought to alsactrl the settings! I'll give it a go tomorrow, and post my findings...

---

### Post by SteveTPearce on 2008-03-03
Thanks again, knathraak! Worked like a charm...

---

### Post by knathraak on 2008-03-03
> **SteveTPearce said:**
> Thanks again, knathraak! Worked like a charm...

Glad to hear it.  Hope it sticks.

---

### Post by celestius on 2008-03-14
holy crap thanks for the fix. i had to make a few modifications to get the file to backup properly but it totally worked. i'm running 7.10 and an ALC883 sound card. i was actually having a different issue where my coax digital output just stopped working for no reason at all. though i was using the beta 2.0 skype and had been watching movies with xine and AC-3 passthrough enabled. anywho, i'll do more experimenting to see if i can replicate the issue now that i have a working backup of my sound settings.

this is what i had to run while using the live cd:

```
alsactl store 0 -f /placewhereiwannasave/asound.state
```

and then when i was back in my regular ubuntu:

```
sudo alsactl restore 0 -f /placewhereisaved/asound.state
```

had to add the zero to specify the sound card which i was backing up the info for.

---

### Post by knathraak on 2008-03-14
> **celestius said:**
> 

```
alsactl store 0 -f /placewhereiwannasave/asound.state
``` 


Yep, good point, you may need to specify which sound card to work with. 0 is the first.  I believe if you have only one sound card it defaults to that one.  

-f tells it the name of the file to use to store to or restore from, so that's important.

---

