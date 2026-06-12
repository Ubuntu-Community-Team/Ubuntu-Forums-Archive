---
title: "Problem to run avidemux"
date: 2022-01-05
forum: Multimedia Software
---

### Post by satimis on 2022-01-05
I have avidemux_2.8.0.appImage download on /Videos

On Terminal;
$ cd Videos
$ chmod a+x avidemux_2.8.0.appImage 
$ ./avidemux_2.8.0.appImage ```

Freetype version 2.10.1
Fontconfig version 21301 :2.13
Using system freetype, fontconfig and fribidi.
Using system libva.
Using system libvdpau.
/tmp/.mount_avidemvo9de1/usr/bin/avidemux3_qt5: error while loading shared libraries: libpcre2-16.so.0: cannot open shared object file: No such file or directory
/home/satimis/Videos

```

Pls help.  Thanks

Regards

---

### Post by schragge on 2022-01-05
```
sudo apt install libpcre2-16-0
```

---

### Post by satimis on 2022-01-05
> **schragge said:**
> ```
sudo apt install libpcre2-16-0
```
Thanks for your advice.

I got it done

Regards

---

