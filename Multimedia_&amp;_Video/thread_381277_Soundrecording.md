---
title: "Soundrecording"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by Keli on 2007-03-10
OK I'm new here and I'm not sure if I am posting it in the right place.

The thing is I am looking for something to replace cubase recording system in Linux.
I am using Ubuntu so if you know about something I can use in stead of Cubase, I would be very gratefull.

But there is more than only Cubase. cause I would need effects and more.

Allso if you know about somthing more professional tools for music, please let me know about it.

Regards, Keli.

---

### Post by Keli on 2007-03-10
bump

---

### Post by tatau on 2007-03-11
I've found Rosegarden to be the closest Cubase equivalent. To be clear, it is not Cubase. But if you're familiar with Cubase and have all the necessary "bits and pieces" to make Rosegarden work (with vst plugins, ladspa, dssi) then you'll find that after only an hour or two, you'll be able get working on making music.

However, before you can get to the "learning Rosegarden" stage you've got to install every needful thing. To wit, it's not an easy task to get it up and running, i.e. install dssi-vst, coordinate everything with jack and your sound card, link to external synths, low latency/preemption????###!!!

No crap, it's going to take you at least 2 weeks to get going (if you're a linux novice like me). And it's glitchy, it'll crash...a lot. You'll have to reboot, and reconfigure jack, and reconfigure Rosegarden, etc, etc.

But... at the end of it you will be making music. There are lots of quirks to learn, but then if you remember what it was like to learn Cubase with Rewire, et al and how temperamental it could be; all the plugins that caused crashes, etc...well, it puts it into perspective. Rosegarden is a new application in a completely new environment - for some of us - it requires a learning of the jargon/sytax.

On the positive, I can attest that it does work...really well, actually. But it's not as easy as simply switching over from cubase - but then you probably know that.

I've had it working well for about a week and here's what's working for me:

**Hardware: **3ghz P4, ATI 5200 pro, M-audio 2496, M-audio keystation 49e, (various other keyboards - I list the lowly keystation because Rosegarden recognises it off-the-bat), Mics, Limiter/compressors, Tube mic preamp, other stuff (mixers, monitors, etc).
**Software Connection Hub:** Alsa, Jack, ICE1712 (M-audio 2496 driver - kind of)
**App:** Rosegarden
**DSSI Softsynth plugins:** Xsynth, Hexter (DX7 Clone), Fluidsynth (sf2 synth)
**VST Softsynth plugs(working): **Triangle I, Oberon, MDA piano/e-piano/JX10/DX10, sfz, Free Alpha, Zr3, Muon Tau
**Linux Softsynths triggered via Jack control: **Hydrogen (drums), Horgand (organ), Alsa Modular Synth, Qsynth
**Efx Plugins: **Too many to list, there are literally tons. Some are very, very good. Others are not usable.
**Mastering Suite: **Jamin (mix the output from Rosegarden down to a wav. file, or whatever)

The quality you can achieve with the above tools is limited only by your hardware (sound card, etc). The sounds you can get from the software is limited only be your imagination (whoa, that sounds corny...but you get the gist). Well worth the shift. It's free. Good luck.:)

---

