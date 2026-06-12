---
title: "Guitar Pro 6: libportaudio.so.2: cannot open shared object file"
date: 2010-06-26
forum: Multimedia Software
---

### Post by lduperval on 2010-06-26
I'm trying to install the demo version of Guitar Pro to see how it stacks up against TuxGuitar. I installed the .deb and also getlibs.

At first try it complained that libportaudio2 wasn't installed so  I installed it too. But when I try to run it I get:

libportaudio.so.2: cannot open shared object file

When I try getlibs ont he binary it says:

No match for libportaudio.so.2

Any ideas?

Thanks,

L

---

### Post by marteus on 2010-06-26
Are you by any chance running 64 bit?

There isn't a lib32 version of libportaudio in the 64 bit repositories required to run the 32bit Guitar Pro binary.

(I have that problem on 10.04 64 bit)

---

### Post by Lennon V C on 2010-07-04
[http://ubuntuforums.org/showthread.php?t=1458626&highlight=guitar+pro](http://ubuntuforums.org/showthread.php?t=1458626&highlight=guitar+pro)
This should answer you question.

---

