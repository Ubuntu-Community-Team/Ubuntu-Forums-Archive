---
title: "Ubuntu 10.10 getting sound from OSS game"
date: 2011-01-29
forum: Multimedia Software
---

### Post by jsbiff on 2011-01-29
Hello,

   I've recently upgraded to Ubuntu 10.10. There's a game I sometimes like to play called Enemy Territory. In the past, I've been able to get sound working with ET (which is an old Open Sound System program), following instructions I've found in the Ubuntu Community Documentation.

Essentially, the instructions boil down to creating a startup script that does the following:

```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```

The problem is, in Ubuntu 10.10, this is generating an error:

cannot create /proc/asound/card0/pcm0p/oss: Directory nonexistent

I believe this indicates that a required kernel module is missing. A bit more searching on these forums and google turned up suggestions to load the kernel modules snd_seq_oss (and some other related modules).

The problem is, with 10.10, when I run sudo modprobe snd_seq_oss, I get an error:

Module snd_seq_oss not found

Has this been moved into an optional package which I need to install?

---

### Post by lidex on 2011-01-30
Perhaps this:
[http://ubuntuforums.org/showpost.php?p=10219347&postcount=2](http://ubuntuforums.org/showpost.php?p=10219347&postcount=2)

---

