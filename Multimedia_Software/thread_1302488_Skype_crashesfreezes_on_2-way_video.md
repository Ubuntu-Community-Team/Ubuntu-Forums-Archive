---
title: "Skype crashes/freezes on 2-way video"
date: 2009-10-27
forum: Multimedia Software
---

### Post by siabost on 2009-10-27
Ubuntu 9.04 32bit
Dell 3Ghz P4 Desktop, ATI Graphics Card with proprietary driver installed (via Ubuntu).
Technika USB Webcam c/w built-in mic (gspca drivers NOT installed as the webcam seems to work without them & I had difficulty compiling in 9.04 anyway)

Loaded Skype from Medibuntu repo, configured Skype to use Pulseaudio for sound, Video test:fine, Sound test:fine, Skype call test: fine.

As soon as I call someone I can see their video & hear their sound & I can speak to them. As soon as I activate my video so they can see me their video freezes & they don't hear me.

I unistalled the ATI proprietary graphics driver and then on activating video their video doesn't freeze but I can't speak to them.

What am I doing wrong?
Is it a graphics card problem?
Should I download latest Skype version from Skype web?

Any ideas helpful.

Thanks.

---

### Post by siabost on 2009-10-28
Also downloaded the 2.1 deb version for Ubuntu 8.10 (there isn't one yet for 9.04) directly from the Skype website and tried that.

With V2.1 in test/set-up mode I get video but all three Audio options (Sound in/Out/Ringing) are locked on Pulseaudio and can't be changed. This means I can't select my webcam mic & thus no sound in.

Any ideas, anyone?

Thanks.

---

### Post by siabost on 2009-11-01
Re Skype 2.1, I note the advice given in other places to install "padevchooser" but before I could try it Ubuntu 9.10 came out and I did a clean install of that, installed the various "restricted-extras" and after adjusting the volume of my Technika Webcam/mic via the sound preferences in 9.10 (it detected the Technika) everything worked!

The only thing is the pic-in-pic view where the inset video (sitting bottom left) within the video-in picture blurrs/distorts the part of the incoming video in a band to the right of it.

A fix for this would leave everything working pretty much perfectly.

---

