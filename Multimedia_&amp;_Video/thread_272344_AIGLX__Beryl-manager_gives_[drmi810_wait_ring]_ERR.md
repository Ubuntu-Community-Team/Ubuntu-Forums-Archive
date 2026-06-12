---
title: "AIGLX / Beryl-manager gives [drm:i810_wait_ring] *ERROR*"
date: 2006-10-06
forum: Multimedia &amp; Video
---

### Post by CheeseEatingBulldog on 2006-10-06
I have setup AIGLX on my sony Vaio, got DRI to work and the thing to boot. When I launch Beryl-manager I get

    [drm:i810_wait_ring] *ERROR* lockup
    [drm:i810_wait_ring] *ERROR* space:65512 wanted 65528

Which kills my X. I am so close to getting it to work but am lost. Can anyone please help? Google has given me no joy.

I have all the modules loaded, glxgears works etc...I posted this on the beryl forum as well, but got no reply. Does anyone here have a clue?

---

### Post by Jaidee on 2006-10-07
I have exactly the same problem. 

Hardware is Intel 82815 chipset.

dmesg | grep drm gives the following
```

[17179614.768000] [drm] Initialized drm 1.0.1 20051102
[17179614.776000] [drm] Initialized i810 1.4.0 20030605 on minor 0
[17179614.804000] [drm] Using v1.4 init.
[17179771.564000] [drm] DMA Cleanup
[17179773.160000] [drm] Using v1.4 init.
[17179825.492000] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[17179825.492000] [drm:i810_wait_ring] *ERROR* lockup
[17179828.668000] [drm:i810_wait_ring] *ERROR* space: 65512 wanted 65528
[17179828.668000] [drm:i810_wait_ring] *ERROR* lockup
```

---

### Post by picpak on 2006-11-18
*bump*

I have the exact same problem. The Beryl splashscreen loads fine, then it switches to a console and says

```
[17180053.232000] [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[17180053.232000] [drm:i810_wait_ring] *ERROR* lockup
```

Any ideas?

---

### Post by yaddoshi on 2007-02-16
> **CheeseEatingBulldog said:**
> 
    [drm:i810_wait_ring] *ERROR* lockup
    [drm:i810_wait_ring] *ERROR* space:65512 wanted 65528


I have the same exact problem trying to set this up on my wife's laptop.  If I find an answer I'll be sure to post it here.  Until then...

...*** BUMP *** again.

---

### Post by CheeseEatingBulldog on 2007-02-19
I know it isn't beryl, and it is only the 3d switching of desktops...and it is a little old, but still I am having some fun with [3ddesktop]("http://desk3d.sourceforge.net/") which is in the repos. It worked in one go, so while you are getting beryl to work, maybe this is a small gadget-thingy to ease the frustration ;)

---

### Post by Tiede on 2007-04-01
So I get it that no one has found a workable solution for this in to months. I am also seeing the same bahavior with an old Dell Optiplex PC with an onboard intel i810 chipset graphics card.
I have looked there and fro to no avail. If anyone has an idea about what to do, I - and I am quite certain many others too - am all ears...
Thanks in advance.

---

### Post by Tiede on 2007-04-05
How can this be that this issue hasn't been fixed after ALL these months...

---

### Post by HoraceLai on 2007-04-15
I don't know anything about Linux but I have the same problem.  I also came across this which might help some of you experts to solve the problem:

[http://www.linuxquestions.org/questions/showthread.php?t=107880](http://www.linuxquestions.org/questions/showthread.php?t=107880)

---

