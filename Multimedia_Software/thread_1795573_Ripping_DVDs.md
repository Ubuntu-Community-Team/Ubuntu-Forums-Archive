---
title: "Ripping DVDs"
date: 2011-07-02
forum: Multimedia Software
---

### Post by TimmyK. on 2011-07-02
What program do I use for this, and what format will it be in?

---

### Post by Mia1990 on 2011-07-03
DVDRip works good it's in the synaptic there are also how to's all over the Internet.

Good Luck

---

### Post by TimmyK. on 2011-07-03
OK, thanks, I'll give it a try. And what format will it be in?

---

### Post by handy on 2011-07-03
Handbrake is brilliant. It rips to .mp4 & .mkv. There are some complications in policy that cause Handbrake to not be in the Ubuntu repos, so you have to install it another way:

[http://www.jonathanmoeller.com/screed/?p=2991](http://www.jonathanmoeller.com/screed/?p=2991)

---

### Post by crispy_420 on 2011-07-03
+1 for Handbrake for conversion. The batch conversion is great.

---

### Post by TimmyK. on 2011-07-03
And will handbrake also remove copy protection?

---

### Post by pjd99 on 2011-07-03
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and

[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

Install libdvdcss. If you can play it, you can rip it...

---

### Post by inobe on 2011-07-03
along with post #7, OGMrip found in synaptic/ software manager/ kpackagekit will do the same as hanbrake and then some.

---

### Post by TimmyK. on 2011-07-05
OK, thanks, OGMrip is awesome.

---

### Post by handy on 2011-07-05
How do OGMrip & HandBrake compare speed wise?

---

### Post by perspectoff on 2011-07-05
If you just want to copy a DVD, k9copy is best. It will downsize at the same time. k9copy can convert to mp4 and a variety of other formats.

Handbrake will rip to a file when every other program fails, but it does it in real time. A 2 hour movie will take 2 hours to rip.

I have never had Handbrake fail, but I usually don't have the patience for it. I therefore reserve it for those situations when other programs fail.

---

### Post by handy on 2011-07-05
> **perspectoff said:**
> 
...

Handbrake will rip to a file when every other program fails, but it does it in real time. A 2 hour movie will take 2 hours to rip.

...

I get faster times than 1:1. I think that hardware may play a very important role with HandBrake, at least, as it will very intelligently use as much of every CPU core that you have available.

I'm very happy with the output of HandBrakeCLI, but if OGMrip is as reliable & does the job quicker I may give it a go.

Re. using HandBrakeCLI, I've made it easy by having a simple alias "hb" set in ~/.bashrc this makes it quicker to use & I expect that you get to see more info when you use the Terminal.

---

### Post by JohnAStebbins on 2011-07-06
> **perspectoff said:**
> Handbrake will rip to a file when every other program fails, but it does it in real time. A 2 hour movie will take 2 hours to rip.

I have never had Handbrake fail, but I usually don't have the patience for it. I therefore reserve it for those situations when other programs fail.
Use faster settings.  E.g. put this in the advanced x264 options edit box.
```

ref=1:bframes=0:cabac=0:8x8dct=0:weightp=0:me=dia:subq=0:rc-lookahead=0:mbtree=0:analyse=none:trellis=0:aq-mode=0:scenecut=0:no-deblock=1

```
Those particular settings will probably result in some loss of quality, but they demonstrate the point.  You can re-enable features till you get to a speed/quality/file-size compromise that you are happy with.  

Also, multi-threaded decoding is now available in the nightly builds.  This speeds up transcoding of high definition sources by quite a bit.

---

### Post by handy on 2011-07-07
> **JohnAStebbins said:**
> 
...

Also, multi-threaded decoding is now available in the nightly builds.  This speeds up transcoding of high definition sources by quite a bit.

I forgot to mention that I'm using handbrake-svn, probably because I've been doing it for so long. :)

@**JohnAStebbins**: By the way, thanks for your contribution to the wonderful HandBrake.

---

### Post by JohnAStebbins on 2011-07-07
> **handy said:**
> I forgot to mention that I'm using handbrake-svn, probably because I've been doing it for so long. :)

@**JohnAStebbins**: By the way, thanks for your contribution to the wonderful HandBrake.

FYI, if you are using the nightly builds PPA and you've been using it for a while, you might want to check that it is still updating properly.  I had to change the version number format recently because the packaging tools changed a version number check from a warning to an error, so my package builds broke.  Changing the format caused updates to fail since it thinks the new package has an older version number.

To fix you can:
```

sudo apt-get remove handbrake-gtk
sudo apt-get install handbrake-gtk

```

---

### Post by handy on 2011-07-08
> **JohnAStebbins said:**
> FYI, if you are using the nightly builds PPA and you've been using it for a while, you might want to check that it is still updating properly.  I had to change the version number format recently because the packaging tools changed a version number check from a warning to an error, so my package builds broke.  Changing the format caused updates to fail since it thinks the new package has an older version number.

To fix you can:
```

sudo apt-get remove handbrake-gtk
sudo apt-get install handbrake-gtk

```

I'm using Arch & handbrake-cli. So I may or may not be experiencing this problem. 

Though, I haven't been getting the SVN updates for some months, (I don't recall switching back to the standard builds, but I must have) so I just had a look at the date of the most recent  /var/cache/pacman/handbrake-cli .pkg which is the 8-march-2011, which is the same date as /usr/bin/HandBrakeCLI . 

So it looks like I've managed to stop using the svn versions on this machine (Box.1). Probably done in a bleary eyed haze in the early hours of the morning, which helped to erase it from my memory (too).

I am using it on Box.2, (which is rarely turned on these days) though.

I think I'll switch back to the standard release of handbrake-cli on box.2 as well, as I'm really happy with the output & as previously stated, I rarely have need these days, though in the past I had many hundreds of DVDs to process, it took me months. :) Which brings up the only problem that I could find with handbrake (or any other similar tool), which is how long it takes to process a file. I suspect that when we are all running 12 core CPUs there won't be anymore complaints in that regard. :)

---

