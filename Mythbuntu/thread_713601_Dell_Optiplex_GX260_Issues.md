---
title: "Dell Optiplex GX260 Issues"
date: 2008-03-02
forum: Mythbuntu
---

### Post by nasha on 2008-03-02
```
Hey Guys,
Having some problems installing Mythbuntu frontend on my GX260. It doesnt boot the live cd, sometimes freezes on a black screen with a cursor, sometimes at the mythbuntu loading screen, sometimes at the selection menu (i have noticed the keyboard lights are flashing at this time).

The one time it managed to boot the live cd, it installed fine, but when it reboots, i get a screen of horizontal coloured lines, along with a mouse pointer, that doesnt move.

A quick forum search revealed changing the onboard memory buffer to 8mb.. This didnt seem to work for me.

Any ideas? Anyone successfully running a frontend on one of these?
```

Seems changing the video buffer solved the problem, just needed a cold power off

---

### Post by vanasdale on 2008-03-12
....

---

### Post by luvit on 2008-03-13
I don't want to sound like a broken record, but I was excited to make mine work! :)
I have pure success, and Optimal video setting on my GX260. Heres what I did:

I downloaded the alternate ISO and it solved my video problem on my GX260.  I now can leave my BIOS at 256MB Video RAM _and_ have 1024x768 75Hz refresh rate.

For reference I viewed my display settings:
  System>Administration>Screens and Graphics - Graphics Card Tab - Driver: intel Experimental modesetting driver for l...

Before I installed Ubuntu I upgraded my BIOS which may have contributed to my fantastic video success. You can get the BIOS update from my blog. Lemme Know!

---

