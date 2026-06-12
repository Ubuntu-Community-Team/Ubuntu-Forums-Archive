---
title: "Codecs needed for:"
date: 2010-05-14
forum: Multimedia Software
---

### Post by mrapoc on 2010-05-14
Hi guys and gals

Im looking at reinstalling cause I failed on the last install

Need to essentially make an x64 install capable of

DVD playback, DVD ripping and Encoding to h264.
Mp3 playback
General flash, java etc.
DVD and CD burning

What plugin/codec packs will I need

Cheers

---

### Post by cariboo on 2010-05-18
You can start by install the ubuntu-restricted-extras meta package, this will install most of what you asked about. For dvd playback you need libdvdcss2, it is available from the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories, or you can run the script located in /usr/share/doc/libdvdread4:

```
sudo ./install-css.sh
```

---

