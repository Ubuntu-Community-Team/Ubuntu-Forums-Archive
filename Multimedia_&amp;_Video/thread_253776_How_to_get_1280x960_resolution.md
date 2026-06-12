---
title: "How to get 1280x960 resolution?"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by victron on 2006-09-08
Hi there,

I notice that while my Windows installation allows me to go all the way up to 1600x1200 res, Ubuntu only allows 1024x768, 800x600, and 640x480.  I would like to get it to run at 1280x960 like I use for Windows.  How might I go about doing this?  I've used Automatix to install the NVidia drivers.

Thanks.

---

### Post by croak77 on 2006-09-08
You can edit your /etc/X11/xorg.cong. You will see a list of all your display modes like this;
```
Modes           "1024x768" "800x600" "640x480"
```

Just add the mode that you want. It reads the first entry from left to right, so if you wanted 1280x960
```
Modes           "1280x960" "1024x768" "800x600" "640x480"
```

---

### Post by enopepsoo on 2006-09-08
Can you just add whatever, or does it need to be supported by your video card?


:-k

---

### Post by varean on 2006-09-08
Its not the video card support that matters(99.9% of cards support pretty much all crazy resolution) but rather monitor support. Look at your monitors manual to see the max supported resolution.

---

### Post by victron on 2006-09-09
> **varean said:**
> Its not the video card support that matters(99.9% of cards support pretty much all crazy resolution) but rather monitor support. Look at your monitors manual to see the max supported resolution.

Oh wow thanks.  That was easy enough.  I added a couple of higher resolutions to each display mode ("Modes" actually appears about 5 times..) and found that whichever mode is to the left is default.  Last time I tried this, X wouldn't start and I had to use my backup .conf.... Well, thanks!

---

