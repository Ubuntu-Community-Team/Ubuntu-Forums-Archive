---
title: "Linux Video/Audio Apps in practice"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by tatau on 2007-02-19
Disclaimer: I'm a complete linux-novice.
Backstory: Was working for a small multi-media production company last year doing video editing/corporate dvds, etc. Also did some music production for video, etc. Looking to use my slightly aging hardware (2 3ghz P4's) to do some freelance stuff; sadly I no longer have any of the software installed.
Just a question or two. If anyone could help, It'd be appreciated.
Used sony vegas 5 + dvd architect 2.0 on pc to capture/edit film and author to dvd. Q: Has anyone used linux apps to produce "pro" looking results, and if so which apps do you recommend to replace vegas+dvda? How do they compare? (I'm not so concerned about myriad transition effects or 3d text).
Also, used cubase sx, jv2020, external compressor/limiters, mics, etc, t-racks for mastering. Q: Are there functional linux apps (that you've used) to produce professional results? What do you recommend? What is the sound quality of the plugins; softsynths, fx, etc?
Heard about Ubuntu Studio and have been very interested to see it up and running.
Thanks, in advance.

---

### Post by tatau on 2007-03-06
After much "wringing of hands" and "gnashing of teeth," pasting code into my terminal and loss of sleep, I finally have some joy. Still a bit glitchy, but very cool to get it all going...sort of.

For Audio: I'm using Rosegarden, using ladspa, dssi, vst plugins (and all the heartache that goes along with setting-up vst). It's very cubase-like for functionality - triggering softsynths, step sequence drums (which I prefer, having done it for the last 20 yrs circa roland MC 50), audio recording, with a ton of efx plugins, etc. I'm very happy with it.
Xsynth-dssi - instrument plugin, nice patches, sits well in a mix
Fluidsynth-dssi - plugin soundfont synth akin to sfz, v-cool
Hexter-dssi - the ubiquitous DX7, suitably 80's sounding
Amsynth - very cool, if I ever get a chance to tweak with it. Very usable sounds/oldskool modular.
Audacity - like soundforge very good
Jamin - mastering, wicked.

Video: Using Kino to capture, Cinelerra CV to edit, QDVD Author to, of course, author DVDs. Blender for efx/3d stuff - though I currently have little desire to include much 3d stuff in my work.
Kino - simple design but captures perfectly from pdx10 and pd170. Haven't tested HDV.
Cinelerra - does it all. Sort of Pinnacle-esque in it's design. Warning: must have all the bits and pieces to get it working properly. Rendering time is still slower than I am used to but I'm still in the process of tweaking.
QDVD Author - was crashing everytime I tried importing media. But, several pastings-of-the-terminal later, it's producing great looking DVDs; background templates created with Gimp.

So in the last two weeks I've finally got everything - basically - working and in the process have gained a real appreciation for the work that has gone into these awesome "free" apps and saved a s**t-load of money - which I don't have. And these are indeed pro-sumer to pro grade tools available...for free. If two weeks of cramming is all that's required to get a studio workstation up and going, and produce a short on dvd and mastered audio tracks to cd, it's a small price indeed.

---

