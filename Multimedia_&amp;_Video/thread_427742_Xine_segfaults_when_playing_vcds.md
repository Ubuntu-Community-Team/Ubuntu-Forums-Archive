---
title: "Xine segfaults when playing vcds"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by anando on 2007-04-29
Hi

Here is the error message : when I try to run a vcd using xine - I get dumped :confused: 

```
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
WARN: psd offset out of range in extended PSD (304 >= 256)
WARN: psd offset out of range in extended PSD (304 >= 256)
WARN: psd offset out of range in extended PSD (320 >= 256)
WARN: corrupt PSD???????
xiTK received SIGSEGV signal, RIP.
Abort (core dumped)

```

Has anyone seen this ? A work around will be gratefully acknowledged.

- Anand.

---

### Post by yabbadabbadont on 2007-04-29
I used gxine, but I got a segmentation fault when I selected VCD from the file menu and it tried to access the CD.  When I used the VCDO option from the file menu, the CD played fine.  If you are using xine-ui, there should be two different VCD related buttons you can press.  Try using them both to see if one of them will work.

---

### Post by anando on 2007-04-30
I tried the VCD0 button on the xine-ui menu - nothing happened. The VCD button results in segmentation fault and core dump horror.

Since you reported gxine worked for you (at least the VCD0 button) - I will try the same and let the forum know ...

I can't believe I am the only one playing (and having problems with) VCDs on xine - am I that outdated ? :-k 

Cheers,
Anand.


> **yabbadabbadont said:**
> I used gxine, but I got a segmentation fault when I selected VCD from the file menu and it tried to access the CD.  When I used the VCDO option from the file menu, the CD played fine.  If you are using xine-ui, there should be two different VCD related buttons you can press.  Try using them both to see if one of them will work.

---

### Post by kwidzin on 2007-05-02
xine-libs over 1.1.2 are buggy if you want to play vcd :-(

---

### Post by anando on 2007-05-02
> **kwidzin said:**
> xine-libs over 1.1.2 are buggy if you want to play vcd :-(

Is this a known bug ? I'd appreciate if someone can file a bug report. I can volunteer to submit if someone shows me how/where.

Thanks,
Anand.

---

