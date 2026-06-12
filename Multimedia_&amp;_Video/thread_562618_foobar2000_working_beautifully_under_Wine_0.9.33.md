---
title: "foobar2000 working beautifully under Wine 0.9.33"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by namely on 2007-09-29
There was enough encouragement at winehq about foobar2000 0.8.3 working in Wine that I decided to try it.  After reading 100+ pages of threads about which music player under Linux is the best, and trying them all, I still missed foobar2000 too much to let it go.

My sound in foobar started working when I chose EsounD driver (ESS) in the Audio tab of System->Preferences->Wine Configuration.  In that same tab, Hardware Acceleration set to Emulation, sample rate = 44100 and Default Bits per Sample = 16 worked fine.  I also followed recommendations to set the Output method in foobar (Foobar2000->Preferences->Playback->Output) to WaveOut and under the "go to settings..." button, increasing the buffer to the max of 8000 msec to prevent skipping.  There hasn't been a single skip in foobar, which runs faster in Wine than it did on the same hardware in Win2K.

A lot of instructions (including those at winehq) suggest installing IE6 and WMP7 to get some of the plugin .dll files in the foobar2000\components directory to load.  I couldn't get IE6 and WMP7 to install no matter what I did (all wine-config-sidenet did was blow away my installed programs in Wine - I wouldn't recommend that), so I went looking for other solutions.

A google search turned up the idea that foo_id3v2.dll will load if MSVCP60.DLL (easily downloadable) is placed in the foobar2000 directory, and that worked for me.  When sidenet blew away my install, foo_audioscrobbler.dll started giving me an "unable to load dll" error message in the foobar console.  Copying libcurl.dll into the foobar2000 directory fixed that.  

This link 
[http://www.hydrogenaudio.org/forums/lofiversion/index.php/t41334.html](http://www.hydrogenaudio.org/forums/lofiversion/index.php/t41334.html)
has other suggestions for .dll files you may need to download to get other foobar plugins to work, but I only needed the ones I mentioned.

Earlier on, I thought foobar2000 might work better with the latest version of Wine (currently 0.9.45) but both foobar and SoulSeek broke under that version, so I went back to the 0.9.33 version from the Feisty repository, and all was well again.

I hope this will help folks get foobar2000 running under Wine.  Good luck!

---

### Post by tbroderick on 2007-09-29
There's way too many native music players to go through the hassle of installing foobar through wine.

---

### Post by namely on 2007-09-29
Some of the native players are good players, and there may be some good tagging apps available, but the integration of the two has not been accomplished to my satisfaction in any of the native apps I tried.  Foobar integrates playing and tagging very well.

Maybe now that I've gone through the hassle of getting foobar2000 running under Wine, it will be easier for other people who can't live without it.  Maybe they will be able to salvage their Windows boxes that much sooner.

I imagine you've seen some of the "best player for Linux" threads.  There's a reason foobar2000 keeps getting mentioned in the discussions, IMO.

---

### Post by boast on 2007-10-23
> **tbroderick said:**
> There's way too many native music players to go through the hassle of installing foobar through wine.

I have yet to find a linux music player that will look like so 

[img]http://host.trivialbeing.org/up/fofr-fb2k-v9-rail.jpg[/img]

know any?

---

### Post by kst- on 2007-10-23
was looking for a decent music player on linux since the day I installed Ubuntu (been using it for 1-2 months now), and I ended up with [gmusicbrowser]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html"). It has some neat features (read through the guide on the website), tagging is not as good as in foobar but that's close to impossible ;-) and it is really damn comfortable (the tray icon popup is nothing but AWESOME, I would use it for that feature alone). Well, in case you haven't tried it: give it a go, it really rocks.

---

