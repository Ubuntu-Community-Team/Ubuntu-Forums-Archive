---
title: "VLC crash"
date: 2013-05-02
forum: Multimedia Software
---

### Post by madnbri on 2013-05-02
Hi,
My VLC crashed once at opening a folder and since that it crashes always. Can I delete/overwrite something to solve?
Thanks in advance,
m

---

### Post by Yellow Pasque on 2013-05-03
I would try deleting the user config files so fresh ones get generated:
```
rm -r ~/.config/vlc
```

---

### Post by SlugSlug on 2013-05-03
if above fails

```
sudo apt-get remove --purge vlc; sudo apt-get autoremove; sudo apt-get install vlc
```

---

### Post by lovebluesky2009 on 2013-05-03
reinstall it may solve the prolem, like what SlugSlug said

---

### Post by madnbri on 2013-05-03
No. None of these are solution.

edited:

I tried an other folder and works. Something must be wrong with this one.

---

### Post by Elfy on 2013-05-03
Trry running it from a terminal with 

```
vlc
```

You might get more idea of what's going on to cause the crash.

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

---

### Post by madnbri on 2013-05-03
> **Elfy said:**
> Trry running it from a terminal with 

```
vlc
```

You might get more idea of what's going on to cause the crash.

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

```
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Couldn't find device name.
*** Zero check failed in ifo_read.c:2125
    for vts_attributes->vtstt_audio_attr[i] = 0x10a36e6500000000
*** Zero check failed in ifo_read.c:2125
    for vts_attributes->vtstt_audio_attr[i] = 0x10a36e6500000000
*** Zero check failed in ifo_read.c:2125
    for vts_attributes->vtstt_audio_attr[i] = 0x10a36e6500000000
*** Zero check failed in ifo_read.c:2125
    for vts_attributes->vtstt_audio_attr[i] = 0x10a36e6500000000
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
*** Zero check failed in ifo_read.c:705
    for vtsi_mat->vts_audio_attr[i] = 0x10a36e6500000000
*** Zero check failed in ifo_read.c:705
    for vtsi_mat->vts_audio_attr[i] = 0x10a36e6500000000
*** Zero check failed in ifo_read.c:705
    for vtsi_mat->vts_audio_attr[i] = 0x10a36e6500000000
*** Zero check failed in ifo_read.c:705
    for vtsi_mat->vts_audio_attr[i] = 0x10a36e6500000000
Segment error
```

Do you know what is intresting? mplayer plays a part of this folder.

---

### Post by Yellow Pasque on 2013-05-03
> No css library available
Did you run the following command? (Note: it's legally questionable, so consult a lawyer if you actually care):
```
sudo sh /usr/share/doc/libdvdread4/install-css.h
```

---

### Post by madnbri on 2013-05-04
> **Temüjin said:**
> Did you run the following command? (Note: it's legally questionable, so consult a lawyer if you actually care):
```
sudo sh /usr/share/doc/libdvdread4/install-css.h
```

Yes, same without 
"No css library available"

---

### Post by mc4man on 2013-05-04
> **madnbri said:**
> Yes, same without 
"No css library available"
The posted command was missing an s (.sh), this should work a bit better

```
sudo  /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by madnbri on 2013-05-04
> **mc4man said:**
> The posted command was missing an s (.sh), this should work a bit better

```
sudo  /usr/share/doc/libdvdread4/install-css.sh
```

Same results.

---

