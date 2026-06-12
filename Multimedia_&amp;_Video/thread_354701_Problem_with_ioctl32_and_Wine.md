---
title: "Problem with ioctl32 and Wine"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by rogeriovinhal on 2007-02-06
Hi, I use Ubuntu 6.10 AMD64, and I installed wine from many different ways, but all of them showed the same error. Any 3D game Wine attempted to run, It hard-locked the system after a few minutes.

I have browsed through logs, and this messages appear repeated a lot of times in many logs just in the time the system locked:

```

Feb  6 13:39:00 roger-desktop kernel: ioctl32(Frozen Throne.e:3914): Unknown cmd fd(16) cmd(82187201){02} arg(00221000) on /home/roger/.wine/c/windows/system32
Feb  6 13:39:01 roger-desktop kernel: ioctl32(explorer.exe:3922): Unknown cmd fd(8) cmd(82187201){02} arg(00222000) on /home/roger/.wine/c/windows/system32

```

Am I to believe that this is the reason from wine been locking my system up?
What should I do?

I use a ATI 9600XT with fglrx succesfully configurated.

---

