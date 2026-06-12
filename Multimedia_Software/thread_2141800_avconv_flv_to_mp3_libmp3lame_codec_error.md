---
title: "avconv flv to mp3: libmp3lame codec error"
date: 2013-05-03
forum: Multimedia Software
---

### Post by thaitang on 2013-05-03
Hi!

I'm experiencing troubles converting video to mp3. Exact same problem as OP in this solved thread [http://ubuntuforums.org/showthread.php?t=1967864](http://ubuntuforums.org/showthread.php?t=1967864), except after downloading xubuntu-restricted-extras (running on xubu 12.04)  nothing changed. I still get the same errors listed below.
These commands

```
 avconv -i test.flv test.mp3
```

```
avconv -acodec libmp3lame -i test.flv test.mp3
```

```
avconv -acodec libmp3lame0 -i test.flv test.mp3
```

give all an error. Either

```
 Encoder (codec id 0) not found for output stream #0:0
```

or

```
 Unknown encoder 'libmp3lame(0)'
```

On ubuntu 10.04 the second command used to work.

Also, the package manager tells me I have the package "libmp3lame0" installed.

Does anyone know what I can do?
Thanks in advance!

---

### Post by thaitang on 2013-05-05
I managed to solve the issue by unistalling and re-installing the extras pkg. Now all seems to be working as desired.

---

### Post by cibalo on 2013-05-08
Hello,

> **thaitang said:**
>  Unknown encoder 'libmp3lame(0)'
Try:
1. Enable Universe/Medibuntu Repos
2. Run the following commands:
```
Sudo apt-get install libavcodec-extra-53
Sudo apt-get install --reinstall avconv
```

---

### Post by andrew.46 on 2013-05-08
Bear in mind that the future of Medibuntu is a little uncertain at the moment:

[http://www.medibuntu.org/getinvolved.php](http://www.medibuntu.org/getinvolved.php)

---

