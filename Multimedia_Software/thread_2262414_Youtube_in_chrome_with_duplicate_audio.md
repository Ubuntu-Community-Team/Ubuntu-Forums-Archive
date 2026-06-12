---
title: "Youtube in chrome with duplicate audio"
date: 2015-01-24
forum: Multimedia Software
---

### Post by macozz on 2015-01-24
Hi all,
I am experiencing for a while an issue when reproduce a video of Youtube in Chrome. I always have duplicated (sometimes triplicated) audio that did not stop when the video is paused or the sound canceled.

This does not happens with Firefox nor when a video is reproduced from a link from Facebook, for example.

I searched the net over this issue, but failed to find anything. I also did not find anything like this in the forum here.

I was guessing if some of the extensions may have something to do with this and deactivated all the extensions regarding Youtube and media, but the issues was not resolved.

Any ideas?

Thank you in advance!

---

### Post by ajgreeny on 2015-01-24
Try with a new Chrome profile as it may be something in your current config for Chrome. I do not know how to start Chrome with a new profile, but I think all the configuration for Chrome is in ~/.config/chrome-browser but as I don't use it I'm not certain about that.  When you find it you could just rename that folder so Chrome will make a new one.

---

### Post by kerry_s on 2015-01-24
> **macozz said:**
> Hi all,
I am experiencing for a while an issue when reproduce a video of Youtube in Chrome. I always have duplicated (sometimes triplicated) audio that did not stop when the video is paused or the sound canceled.

This does not happens with Firefox nor when a video is reproduced from a link from Facebook, for example.

I searched the net over this issue, but failed to find anything. I also did not find anything like this in the forum here.

I was guessing if some of the extensions may have something to do with this and deactivated all the extensions regarding Youtube and media, but the issues was not resolved.

Any ideas?

Thank you in advance!

check "chrome://gpu" make sure your running accelerated. google has chosen to blacklist a lot of devices.
it should all be green using hardware.

pics:

---

### Post by macozz on 2015-01-24
Thank you people,
what I get in the chrome://gpu is this:
Graphics Feature Status
Canvas: Software only, hardware acceleration unavailable
Flash: Hardware accelerated
Flash Stage3D: Software only, hardware acceleration unavailable
Flash Stage3D Baseline profile: Software only, hardware acceleration unavailable
Compositing: Hardware accelerated
Multiple Raster Threads: Disabled
Rasterization: Software only, hardware acceleration unavailable
Threaded Rasterization: Enabled
Video Decode: Software only, hardware acceleration unavailable
Video Encode: Hardware accelerated
WebGL: Hardware accelerated

Is all in green (pale and normal green) except Multiple Raster Threads, which is in red because is disables. I have no idea how to enable this.

I made the changes you suggested in  chrome://flags. Actually I only had to change the second one, because the first was already enabled.

I am testing the changes now...

---

### Post by kerry_s on 2015-01-24
you sure the first 1 is enabled, cause when it's enabled it says disable.

you want it to say hardware, software is where you get that lag, dual audio, & sound from tabs you already closed.

---

### Post by macozz on 2015-01-25
OK, but how I enable this?
The other changes has no efect. Dual audio stand...

---

### Post by kerry_s on 2015-01-25
just click enable, then click relaunch now at the bottom.

---

### Post by macozz on 2015-01-25
Done! Thank you very much. Now is OK

---

### Post by macozz on 2015-01-31
It was solved... but the very same problem is back.. despite all the graphic features are hardware accelerated.
I seems to me that do not make sense the problems being apparently solved and then come back...

---

