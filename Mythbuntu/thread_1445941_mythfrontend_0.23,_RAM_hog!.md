---
title: "mythfrontend 0.23, RAM hog!"
date: 2010-04-03
forum: Mythbuntu
---

### Post by geoffp on 2010-04-03
Is anyone else noticing ridiculous memory usage from the mythfrontend in 10.04?  Mine is sucking down 777MB, which is way up from last revision.

It's actually eating up all my available RAM.  Not sure if this is a leak, or what.

---

### Post by superm1 on 2010-04-03
This is usually pretty dependent on the theme you are using and whether or not it has all that pretty artwork loading for individual shows.

Are you on the same theme as you were on 0.22?

---

### Post by jaakan on 2010-04-08
there seems to be an issue system wide with caching

mythfrontend for my only uses 20% of my ram
mythbackend 2.4%
mysql 1.5%
Xorg 4%

my laptop
```

             total       used       free     shared    buffers     cached
Mem:       3928280    1838056    2090224          0     119328    1004872
-/+ buffers/cache:     713856    3214424
Swap:      2000084          0    2000084

```

my Mythtv HTPC
```

             total       used       free     shared    buffers     cached
Mem:       2056768    2039956      16812          0      64708     679500
-/+ buffers/cache:    1295748     761020
Swap:      2000052          0    2000052

```

---

### Post by ian dobson on 2010-04-08
Hi,

That looks normal. Linux tries to use as much of your memory as possible caching disk accesses. If you ram that's used by the cache is required my something more important linux will clear the cache and allocate the ram

Remember unused ram is wasted ram. Windows does exactly the same but lies about the "free" ram.

Here's a free from my 8Gb backend
 ```

            total       used       free     shared    buffers     cached
Mem:       8194592    8106136      88456          0     148320    6714416
-/+ buffers/cache:    1243400    6951192
Swap:            0          0          0

```

Regards
Ian Dobson

---

### Post by jaakan on 2010-04-09
Compared to 9.10 and older versions not really. My current HTPC use to always be around 50% since I built it almost 2 years ago and now it hovering around 95% to 99%. I really notice this on my laptop before I upgraded my ram from 1G to 4Gb. Something has changed with 10.04.

---

### Post by pmorton on 2010-05-20
> **jaakan said:**
> Compared to 9.10 and older versions not really. My current HTPC use to always be around 50% since I built it almost 2 years ago and now it hovering around 95% to 99%. I really notice this on my laptop before I upgraded my ram from 1G to 4Gb. Something has changed with 10.04.

I've got the same problem. With 10.04, Although it didn't with the original install, Mythfrontend has now started eating up 95% of my 2Gb of RAM, and the video is dropping frames so that the picture is practically unwatchable.

---

### Post by stormb on 2010-05-25
I'm experiencing a similar issue since upgrading to 10.04 (with 0.23 auto builds) from 9.10 (with 0.22 auto builds).

Have a Revo R3600 with 1GB RAM, 256 of which is video RAM (sufficient for SD VDPAU).

Myth 0.22 was fine with the 750MB I have. I believe the frontend used about 150MB.

Now it's 250MB-300MB and swapping during playback. Restarting Mythfrontend brings usage back down to ~200MB and things are watchable again (however it grows again over a matter of hours).

I'm using the Mythbuntu theme and have disabled the artwork section of the theme. I was using this theme with 0.22.

Might try the MythCenter theme in case that helps, although I expect WAF will be affected!

Will

---

### Post by stormb on 2010-06-02
Well things seem to be much better for me now, after an upgrade to the latest version of all packages (I do this every week, so it must be something recent that fixed it). However I don't think things have improved because of changes with Myth - it seems Xorg has had a bugfix or something.

Mythfrontend.real is still using about 250-300MB of RAM (using Mythbuntu theme, and the artwork has become enabled again), but Xorg is using way less than it was (couple of hundred megs before, now down to 40MB).

So now I can use my HTPC normally again, woohoo! :D

Will

---

### Post by pmorton on 2010-06-07
After the grief I've had with it, I don't think my wife will let me go back to Myth!

---

### Post by demiurg on 2010-11-05
I noticed this problem in 10.10 too. Any suggestions ?

---

### Post by ronron261 on 2011-02-17
@ demiurg

I suspect you are using the Nvidia drivers (260.19.06) from the repository.
Apparently there is a bug in VDPAU , that caused it to attempt allocation of huge blocks of system memory. This regression was introduced in the 260.* driver series.
See bugticket  [http://code.mythtv.org/trac/ticket/9144#comment:7]("http://code.mythtv.org/trac/ticket/9144#comment:7")
Now I using the latest driver for a couple of day and that seems to solve it.
Using the ppa from [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html") gives me 270.18


Greeting,
Ronald.

---

