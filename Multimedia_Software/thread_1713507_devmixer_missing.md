---
title: "/dev/mixer missing"
date: 2011-03-24
forum: Multimedia Software
---

### Post by kmashlea on 2011-03-24
Hi, I am new to Linux, and have managed to get most things working but I am stuck with getting some audio software I wrote to work using pymedia. It requires /dev/mixer which is not there.

I have read loads of forums/googles etc and tried most of the suggestions to no avail.

The ones I do not want to try are the ones saying I need to re-compile the kernel to get it to work!

Can someone please help me or let me know if I am wasting my time.

Thanks

---

### Post by kmashlea on 2011-03-30
As no one has got back with any information, I decided to completely remove Ubuntu 10.10 (which included everything I had worked on to set up and install).

I have now installed 10.4 which seems to work correctly and /dev/mixer /dev/dsp etc are all there.

I am hoping that this is going to be fixed in Natty 11.04 or at least a way to modify my programs with a replacement for /dev/mixer etc as I am about ready to give up and return to windows (for all its faults, they don't just remove functionality).

---

### Post by bowens44 on 2011-03-30
> **kmashlea said:**
> As no one has got back with any information, I decided to completely remove Ubuntu 10.10 (which included everything I had worked on to set up and install).

I have now installed 10.4 which seems to work correctly and /dev/mixer /dev/dsp etc are all there.

I am hoping that this is going to be fixed in Natty 11.04 or at least a way to modify my programs with a replacement for /dev/mixer etc as I am about ready to give up and return to windows (for all its faults, they don't just remove functionality).

This is by design. /dev/mixer is the legacy OSS device and is no longer included n the kernel. If you want to have it, recompiling the kernel is your only solution. It's not difficult.

---

### Post by kmashlea on 2011-03-30
You say its not difficult! I used unix about 20-30 years ago and have been using windows since its inception.

I would not have a clue about re-compiling the kernel let alone what to do to get the functionality back that is in 10.04.

Is there no similar way of accessing media like /dev/mixer etc?

I use a module called pymedia in my programs which works fine under windows and works great under 10.04 but not under 10.10.

I have tried various other decoders as well and they all use /dev/mixer.

Can you tell me of any similar module to pymedia that I can use

I was so pleased when I first loaded Ubuntu as all my hardware etc worked without incidence unlike when I tried it many years ago, then I start to use it in earnest and fall over at the first block because it has been changed.

Why can't it support legacy stuff as well as new stuff? isn't that the whole idea Linux?

I must say that I am disappointed, and having seen all the other peaople with the same issues, I am really supprised that Linux survives.

---

### Post by Yellow Pasque on 2011-03-31
Use padsp:
```
padsp <program>
```

---

