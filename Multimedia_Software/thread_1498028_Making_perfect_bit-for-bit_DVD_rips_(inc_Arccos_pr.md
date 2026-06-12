---
title: "Making perfect bit-for-bit DVD rips (inc Arccos protected)"
date: 2010-05-31
forum: Multimedia Software
---

### Post by thecapsaicinkid on 2010-05-31
I'm currently using;


```
lsdvd
ddrescue -n -b 2048 /dir/myrip.iso
```This *should* give me a perfect bit-for-bit rip of the disc, skipping over any bad sectors (i.e ArCCos protected discs)

Unfortunately on said protected discs the iso still gives libdvdread errors on playback yet plays fine direct from the disc.

```

libdvdread: Invalid IFO for title 4 (VTS_04_0.IFO)
```How can this be if ddrescue is supposedly giving a direct copy minus the corruption?



Thanks

---

### Post by ghostborg on 2010-06-08
I personally use k9copy in linux.
DVDFAB HD Decrypter free in Winblows.
DVDshrink and dvdfab free work in Wine.
People that use the full versions have problems entering their product keys in linux with the purchased version of DVDfab.

I have not used the command line to copy/decrypt in a while, but I used dvdbackup in the repos in the past and I remember seeing errors similar.
Maybe a copy protection or new one not handled properly by the program or possibly a scratched disc.

---

