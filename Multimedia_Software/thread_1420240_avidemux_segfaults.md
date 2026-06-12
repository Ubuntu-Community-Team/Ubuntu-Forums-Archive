---
title: "avidemux segfaults"
date: 2010-03-02
forum: Multimedia Software
---

### Post by zenxi on 2010-03-02
im trying to use avidemux to create dvd compatable mpegs,yes i know that other programs like DeVeDe and mandvd convert your files for you, but i believe that the production quality is better with avidemux.   anyways at first i was almost able to encode video using the DVD option from the auto menu, the encode would finish the first pass and when it would switch to the second pass it would segfault. tried this with AVI's and other formats  but now i cant save the output file   im connected to the ripbox via vnc so i will post the error message in the next post

---

### Post by zenxi on 2010-03-02
Segfault
 at line 0, file ??/usr/lib/libADM_core.so(ADM_backTrack+0x68) [0x7f8c07ad4f28]
/lib/libc.so.6 [0x7f8c02e69530]
/lib/libc.so.6(memset+0xa5b) [0x7f8c02eb7afb]
/usr/lib/ADM_plugins/audioEncoders//libADM_ae_twolame.so(twolame_malloc+0x35) [0x7f8bf1b472a5]
/usr/lib/ADM_plugins/audioEncoders//libADM_ae_twolame.so(twolame_init+0x15) [0x7f8bf1b45505]
/usr/lib/ADM_plugins/audioEncoders//libADM_ae_twolame.so(_ZN19AUDMEncoder_Twolame10initializeEv+0xe) [0x7f8bf1b4476e]
avidemux2_gtk(_Z16buildAudioFilterP22AVDMGenericAudioStreamj+0x114) [0x465374]
avidemux2_gtk(_Z12oplug_mpegffPKc14ADM_OUT_FORMAT+0x35b) [0x499ecb]
avidemux2_gtk(_Z6A_SavePKc+0x1d0) [0x462ae0]
avidemux2_gtk(_Z13A_SaveWrapperPc+0xe) [0x45bd5e]
/usr/lib/libADM_coreUI.so(_Z17FileSel_ReadWritePFvPKcEiS0_S0_+0x7a) [0x7f8c078c874a]
avidemux2_gtk [0x575ed8]
avidemux2_gtk(_Z12HandleAction6Action+0x143a) [0x4608aa]
avidemux2_gtk(_Z11guiCallbackP12_GtkMenuItemPv+0x1f) [0x57a52f]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e) [0x7f8c049815ae]
/usr/li

the error message cuts off there.

---

### Post by klausner on 2010-04-12
I get a segfault almost ever time I try to use avidemux to convert formats. It seems to complete the conversion, then at the last second, the program barfs. The latest try gave me this error:
> Segfault
 at line 0, file ??ADM_backTrack
/lib/libc.so.6 [0x7fadd6639530]
memset
twolame_malloc
buffer_init
twolame_encode_buffer_interleaved
AUDMEncoder_Twolame::getPacket(unsigned char*, unsigned int*, unsigned int*)
defaultAudioSlave(muxerMT*)
/lib/libpthread.so.0 [0x7fadda8d3a04]
clone

---

### Post by joddy on 2010-04-20
I experienced the same error (SEGFAULT) in Avidemux 2.5.2 using the DVD option in the Auto menu (I am using Ubuntu 10.04 Beta but I did have it with Ubuntu 9.10 as well).

For whatever reason (???), the Audio MP2 TwoLame encoding process fails and Avidemux crashes.

I am now selecting AC3(lav) for encoding the audio and so far it works fine.

If using either MP2 TwoLame or AC3 isn't really relevant for your purposes, then selecting AC3 can solve the problem (I believe AC3 is even better supported on commercial DVD players)

---

### Post by coady on 2010-08-27
> **joddy said:**
> I experienced the same error (SEGFAULT) in Avidemux 2.5.2 using the DVD option in the Auto menu (I am using Ubuntu 10.04 Beta but I did have it with Ubuntu 9.10 as well).

For whatever reason (???), the Audio MP2 TwoLame encoding process fails and Avidemux crashes.

I am now selecting AC3(lav) for encoding the audio and so far it works fine.

If using either MP2 TwoLame or AC3 isn't really relevant for your purposes, then selecting AC3 can solve the problem (I believe AC3 is even better supported on commercial DVD players)
I had exactly the same experience, same segfault (see the previous screen shot), and same solution.

So just to add confirmation that if you use the DVD auto setting in Avidemux, if you switch the audio codec to AC3 (lav) it will convert without a hitch. :)

---

