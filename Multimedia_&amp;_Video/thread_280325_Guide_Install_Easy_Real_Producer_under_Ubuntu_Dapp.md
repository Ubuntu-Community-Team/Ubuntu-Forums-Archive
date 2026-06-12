---
title: "Guide: Install Easy Real Producer under Ubuntu Dapper and convert AVI to RMVB"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by kecsap on 2006-10-19
The environment:

- Ubuntu 6.06 LTS (dapper)
- Intel Dual Core Processor
- I compiled, installed and tried the latest wine versions, version 0.9.17-0.9.23: IMPORTANT: You should compile and install the mesa library 6.5.1 version because of the wine version 0.9.17- are designed for that, but if you tries earlier versions of wine, then its GUI is broken. The application remains a bit unstable in spite of these actions. Perhaps, the dri ans glx of xorg should update also.

General installation:

1. Download the quartz.dll (windows dll) from somewhere and copy it to the fake windows/system32. Run the winecfg and add the quartz.dll to the list under Libraries (parameters: native, built-in).
2. Download the XP Codec Pack and install it (common codec pack). I used version 2.0.5. (You can try another one or your favourite.)
3. Download a new FFDshow pack. I used version 20060821-rev2546.
4. Download the Real Alternative and install it (codec pack of RealMedia codecs). I used version 1.50.
5. Download the Easy Realmedia Producer and install it. I used version 1.94.


Works:

- AVI files (DivX, Xvid, H264...) can be encoded to RMVB and MKV.
- 1-Pass and 2-Pass modes.
- Joblist.
- Command line parameters.
- RealMedia 8/9/10 codecs and so on.

What is not working?

- The application can not start the encoding process sometimes.
- A slider is displayed in the middle of the application. It is a bit disturbing, but not a big deal.

---

