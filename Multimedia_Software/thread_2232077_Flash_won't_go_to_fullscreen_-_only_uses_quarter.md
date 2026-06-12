---
title: "Flash won't go to fullscreen - only uses quarter"
date: 2014-06-29
forum: Multimedia Software
---

### Post by Ben_Cook on 2014-06-29
So I've developed a problem today - when I put videos to fullscreen it only is on the upper left quadrant of the screen, and it is only a quarter of the picture.  I've tried disabling the add-ons, restarting firefox in safe mode, disabling the hardware accelerator and making sure I have the most up to date flash player (which I do).  I've rebooted the netbook but no luck with that either.  I should mention that I am using a different tv for display, as my other one just broke.  It's just a used 42" Sanyo, nothing special although it did "auto adjust" when I first plugged in the VGA cable. I've tried virtually every setting on the tv, although I can't imagine the tv being the problem when everything else is fine.  I'm running the latest Lubuntu.  Thanks!

---

### Post by Ben_Cook on 2014-07-01
Just to add to what I said, it does the same thing in Chromium as well.

---

### Post by Yellow Pasque on 2014-07-01
Is this all Flash videos or only a certain site(s)?

You may want to try clearing the Flash cache (make sure browsers are closed):
```
rm -r ~/.adobe/Flash_Player/*
```

---

### Post by Ben_Cook on 2014-07-01
That did it....thank you.  Such a nice easy solution.  I didn't know what I did.  And yes, it was every site

---

