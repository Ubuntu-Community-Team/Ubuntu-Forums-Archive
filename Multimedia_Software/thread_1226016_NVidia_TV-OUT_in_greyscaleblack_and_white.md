---
title: "NVidia TV-OUT in greyscale/black and white"
date: 2009-07-29
forum: Multimedia Software
---

### Post by tom66 on 2009-07-29
I have an NVidia GeForce 7300 GT. I have hooked it up to my TV through an S-video to composite adapter. But the picture, at boot, and when in Ubuntu, is in greyscale/black and white. 

I suspect that it's output is set to NTSC, whilst my TV is in PAL. How could I set it to PAL? 

Thanks, Tom

---

### Post by Rhubarb on 2009-07-29
It's been a while since I last did this, and now I've got a newish TV that'll support ntsc and pal.

But anyway, there's a command line based nvidia setup app (I forgot what it's called, do a search on it) that can generate /etc/X11/xorg.conf files for you.  - I think you can specify pal / ntsc output in this app.

Another thing to note, is that not all svideo --> composite adapters actually work properly - I bought one a few months ago that would just work with black + white.
I did find one (that was originally with an old nvidia video card with tv out) that does work.
Another way of making sure your svideo --> composite adapter actually works, is to make one up yourself.  It just requires an s-video plug, a composite RCA plug, some wire, and a small non-polarised (preferably ceramic) capacitor.  I've made one of these up from a simple plan I found on the internet a few years ago, and it worked *very* well.

Sorry I couldn't find any links or anything specific to help you out, but I hope this can give you some pointers where to start looking.

Best of luck,
Rhubarb.

---

### Post by tom66 on 2009-07-29
I think my adapter works correctly, because it is very difficult to make a composite to s-video adapter (complicated comb filters). Whilst s-video to composite only requires a 470nF cap. I was hoping to not have to make an adaptor myself but I guess I'll have to if this one doesn't work.

When you talk about the command-line application, do you mean 'nvidia-xconfig'?

---

### Post by Rhubarb on 2009-07-30
> **tom66 said:**
> ...When you talk about the command-line application, do you mean 'nvidia-xconfig'?

Ahh yes, that's the CLI app I was thinking about!

I've got an inkling that nvidia doesn't support choosing PAL over NTSC for TV-OUT in their current linux drivers.  I could be wrong but I think I may have heard about it from somewhere.

My brain is currently a bit mushy as I've had a long day at work :P

---

