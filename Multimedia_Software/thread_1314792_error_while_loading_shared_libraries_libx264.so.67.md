---
title: "error while loading shared libraries: libx264.so.67: cannot open shared object file:"
date: 2009-11-04
forum: Multimedia Software
---

### Post by xenogia on 2009-11-04
Hi I've installed MPlayer and I keep getting the following error

error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory

though i checked /usr/lib and the library is there, any ideas?

---

### Post by andrew.46 on 2009-11-04
Hi xenogia,

> **xenogia said:**
> 

```
error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory
```


Could you run the following:

```
sudo find /usr -iname 'libx264.so.*'
```

This will show definitively what versions of this library you have and the locations of the files.

Andrew

---

### Post by xenogia on 2009-11-04
> **andrew.46 said:**
> Hi xenogia,



Could you run the following:

```
sudo find /usr -iname 'libx264.so.*'
```This will show definitively what versions of this library you have and the locations of the files.

Andrew

Hi Andrew,

I did the following and got

/usr/share/mplayer/libx264.so.76
/usr/lib/libx264.so.76

Do I need to make a symbolic link and if so how do i do that?

---

### Post by andrew.46 on 2009-11-04
Hi xenogia,

> **xenogia said:**
> 
```
/usr/share/mplayer/libx264.so.76
/usr/lib/libx264.so.76
```


So the problem is clear at least. I suspect you have the repository MPlayer which depends on the libx264-67 and you have installed a newer x264 library for another program, perhaps FFmpeg?

> Do I need to make a symbolic link and if so how do i do that?

Hmmmm.... I am not so sure that this would work as versions of MPlayer/MEncoder are tied fairly closely to versions of x264 and normally if you update one you would update the other. It hinges a little on why you need the updated x264 that is on your system?

Andrew

---

### Post by FakeOutdoorsman on 2009-11-04
> **xenogia said:**
> Hi I've installed MPlayer and I keep getting the following error

error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory

though i checked /usr/lib and the library is there, any ideas?

Do you have any third-party repositories enabled?

---

### Post by xenogia on 2009-11-04
I figured out the problem, seems it was mplayer-nogui that was causing the issues and mplayer wasn't installed.  I uninstalled mplayer-nogui and install mplayer and it resolved the issue.

---

### Post by andrew.46 on 2009-11-04
Hi xenogia,

> **xenogia said:**
> I figured out the problem, seems it was mplayer-nogui that was causing the issues and mplayer wasn't installed.  I uninstalled mplayer-nogui and install mplayer and it resolved the issue.

Glad to hear that you have resolved the issue :).

Andrew

---

