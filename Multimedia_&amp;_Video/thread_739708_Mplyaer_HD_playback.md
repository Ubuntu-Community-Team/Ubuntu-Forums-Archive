---
title: "Mplyaer HD playback"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by jacobc2 on 2008-03-30
Hello all,
     I am running mythbuntu on a 2.8GHz P4, with 512MB of ram, a Nvidia FX5200 pci video card, and a 750GB SATA HD on a pci raid card.  When I try to play back a HD mov file downloaded from revision3 I get choppy playback.  Its watchable but I was wondering if there is some way to make the play back go a lot smoother.

I have nvidia drivers installed, and glxinfo is reporting that DRI is on.

Thanks in advance.

---

### Post by shirilover on 2008-03-30
Given your hardware specs, chances are that you will be able to get much improvement in HD H.264 playback.

Since H.264 is processor intensive, it requires much more CPU than other video compression algorithms.

Thus, if the source video you are attempting watch is 1080p, anything less than a dual core CPU of >2.0 GHz will not give you smooth playback. Installing other codecs will not help.

However, there are some switches that may improve H.264 playback in MPlayer.
They may not make it completely smooth, but you can try using the following:
```

-ladvopts fast:skiploopfilter=all

```

---

### Post by drdrewdown on 2008-03-30
be specific as to what format & resolution the video you are having problems with.

smplayer has worked best for me

```
sudo apt-get install smplayer
```

its just a tweaked version of mplayer, but it plays 1080p x264 files the best for me, but until there is h264 hardware acceleration provided by nvidia we will be SOL imo in reference to smooth frame-loss-less playback

cheers

---

### Post by Cresho on 2008-03-30
smplayer is excellent.  I just installed it due to the movieplayer not being able to play my High definition movies.  This one plays them flawlessly for me.

---

### Post by jacobc2 on 2008-03-30
as far as I can tell all the files ar 720x no clue to what revision3 is doing on the p or i side of things.  I tried adding
```
-ladvopts fast:skiploopfilter=all
```
but it didn't seem to help any.

I can't use smplayer as I am using mythtv and smplayer is its own gui and all.

---

### Post by Cresho on 2008-03-31
actually, Xine movieplayer is much better than smplayer.

---

### Post by jocheem67 on 2008-03-31
That's a bold statement. Any arguments for that??

---

### Post by aeiah on 2008-03-31
you could try xine. both xine and mplayer playback HD content the best for me, although i do get sound issues with xine (gaps in audio + sync issues).

i havent tweaked mplayer particularly though so i cant really help. i run my HD content on an AMD x2 3800 1gig ram nvidia 7800gt.

---

### Post by sloggerkhan on 2008-03-31
Hmm. For me, mplayer has somewhat choppy playback of high-def on an 8600gt using smplayer (mkv h264 file). With xine and having set in xine prefs for ffmpg to get 2 threads, I have pretty smooth playback, but my file plays with 2.07 instead of 1.77 aspect ratio and I have no idea why... (there's something wrong with my version of xine that makes it so the aspect ratio's not propper for some files). If I knew more about mplayer, i could probably get it to use both my cores too and be fine. The reason this problem exists for me (so far as I understand) is that nvidia hasn't implemented h264 playback acceleration for their linux driver.

---

### Post by aeiah on 2008-03-31
even under windows, x264 playback is rarely hardware accellerated so dont worry about missing out. its just gonna take time... 

there is a way to make mplayer use 2 cores, but i wont be able to find out what's in my mplayer config file until later today when im not at work. as for xine aspect ratio problems, have you tried forcing a set aspect ratio in the xine config? (such as telling it your monitor is 16:10 or 16:9 etc). also, i think xine listens to your xorg.conf, and you can set the aspect ratio in there, which is what i do because im currently using my 16:9 hdtv in the crap resolution of 1024x768

---

