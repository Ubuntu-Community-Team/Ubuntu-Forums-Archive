---
title: "convert cd to wma lossless"
date: 2008-07-21
forum: Multimedia Software
---

### Post by leo5111 on 2008-07-21
and before anyone says sound juicer i see WAV no wma lossless..:popcorn:

---

### Post by kostkon on 2008-07-21
> **leo5111 said:**
> and before anyone says sound juicer i see WAV no wma lossless..:popcorn:
You don't have many options for *WMA* in the open source world. One sure option is to use *FFmpeg* which will allow you to encode to *wmav1* and *wmav2*, namely *WMA* ver. 7 and ver. 8, but no lossless, I'm afraid. I doubt you will find a way to encode to *WMA Lossless* in *Ubuntu/Linux*.

If you decide to use *FFmpeg*, you'll have to install the version of it that is offered by the [*Medibuntu* repository]("http://medibuntu.org/") and has the support for restricted formats enabled.

You can convert your CDs to *WAV* and then to *WMA* with *FFmpeg*, using a GUI frontend like [*WinFF*]("http://www.winff.org/"), for example.

---

### Post by kajillin on 2008-07-21
i dont think u can rip lossless .wma in linux ( its a proprietary format, so i could be wrong but i havent been able to), try an open source format maybe, ogg, or flac.

---

### Post by kostkon on 2008-07-21
One other option would be to try to use a windows program that encodes to WMA Lossless in Ubuntu using Wine.

---

