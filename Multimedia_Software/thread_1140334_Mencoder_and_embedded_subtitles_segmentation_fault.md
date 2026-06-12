---
title: "Mencoder and embedded subtitles segmentation fault"
date: 2009-04-27
forum: Multimedia Software
---

### Post by bdEVILord on 2009-04-27
Hi,

I'm trying to convert an mkv to avi using mencoder. The file has both *** and text subtitles. But i wan't the *** subtitles because they look better.

So far i have tried to do this on two different computers both running 64-bit Ubuntu 9.04 Desktop. And at both occasions it has failed.


Running "mencoder file.mkv -oac mp3lame -ovc lavc -lavcopts vcodec=mpeg4 -sid 0 -*** -embeddedfonts -o file.avi" causes a segmentation fault.

```

do@compy-ubuntu:~/Desktop/toradora$ mencoder Episode\ 02\ -\ Ryuuji\ And\ Taiga.mkv -oac mp3lame -ovc lavc -lavcopts vcodec=mpeg4 -sid 0 -*** -embeddedfonts -o Episode\ 02\ -\ Ryuuji\ And\ Taiga2.avi
MEncoder 2:1.0~rc2-0ubuntu19 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x12516682
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang und
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang und
[mkv] Will play video track 1.
Segmentation fault

```


But if i skip the embedded subs and go for the text subs instead, i get worse subs but it works flawlessly. "mencoder file.mkv -oac mp3lame -ovc lavc -lavcopts vcodec=mpeg4 -sid 0 -o file.avi".

Mplayer plays the original file with both embedded and text subtitles without errors.

The first computer has a Core 2 Duo processor and the other has a AMD Mobile Athlon 64 processor.

It seems as though the forums censor the word "A S S". I ofcourse mean the Advanced SubStation Alpha variant of SSA.

Thanks for your time.
//bdEVILord

---

