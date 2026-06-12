---
title: "libdvdcss2 fails to break CSS keys"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by joegester on 2007-06-04
I've got a fresh install of Feisty on my laptop.  I've got medibuntu going and I've installed libdvdread and libdvdcss from there.  Nonetheless, I can't play encrypted DVDs with xine or mplayer.

I get this from mplayer:
```

Playing dvd://1.
There are 5 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x0000017e)

```

And totem tells me :
> 
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?


However!

```

root@em:~# dpkg --get-selections | grep dvd
dvd+rw-tools                                    install
dvdrip                                          install
dvdrip-doc                                      install
libdvdcss2                                      install
libdvdnav-dev                                   install
libdvdnav4                                      install
libdvdplay0                                     install
libdvdread3                                     install
lsdvd                                           install
root@em:~# 

```

I saw_ [this thread]("http://ubuntuforums.org/showthread.php?t=79256&highlight=dvdcss") _but that doesn't seem to be very up to date on this issue.  I'd rather not use a random repo for libdvdcss when medibuntu is right there for this purpose.

Thoughts? Suggestions? I'm overlooking something obvious? I'm a moron?

---

### Post by Pragmatist on 2007-06-05
Please post the output of this:

```
ls -l /usr/lib/libdvdcss*
```

---

### Post by Blue_Sv on 2007-06-05
Hi There... same issue here... got two Feisty installs .... one's fine the other not. :(

andrew@nw8240:~$ dpkg --get-selections | grep dvd
dvd+rw-tools                                    install
dvdauthor                                       install
dvdrip                                          install
dvdrip-doc                                      install
libdvdcss2                                      install
libdvdnav4                                      install
libdvdread3                                     install
lsdvd                                           install
andrew@nw8240:~$ ls -l /usr/lib/libdvdcss*
lrwxrwxrwx 1 root root    18 2007-06-04 17:37 /usr/lib/libdvdcss.so.2 -> libdvdcss.so.2.0.8
-rw-r--r-- 1 root root 31480 2007-01-21 01:45 /usr/lib/libdvdcss.so.2.0.8
andrew@nw8240:~$ 

Any help appreciated

---

### Post by joegester on 2007-06-05
Same version here:
```

joe@em:~$ ls -l /usr/lib/libdvdcss*
lrwxrwxrwx 1 root root    18 2007-06-04 21:41 /usr/lib/libdvdcss.so.2 -> libdvdcss.so.2.0.8
-rw-r--r-- 1 root root 31480 2007-01-20 07:45 /usr/lib/libdvdcss.so.2.0.8

```

---

### Post by Limitlesschannels on 2007-06-10
Same issue here.  There have been a number of threads about this.  What's going on?

---

