---
title: "video freezers - Error while decoding frame!"
date: 2009-07-21
forum: Multimedia Software
---

### Post by 8472 on 2009-07-21
Hi,
I do have a problem while watching some movies in the computer [using ubuntu 9.04].
At some times (and it's always the same times) the picture in the player freezes, but as I've noticed the time counter in the player works further even that the picture is freezed. And after a minute or two the picture gets back and the movie continues (until another freeze).
I've already tried several media players, and the same result with all of them.
So I think it's possible that some codec problem?
Furthermore, when I've tried the MPLAYER from the CLI, i received this at the time of that freezing:
> 
...
[mpeg4 @ 0x8972350]header damaged  0.289 10573/10573  3%  1%  3.1% 3 0
Error while decoding frame!
...


When i made the same attempt with MPLAYER but using VERBOSE parameter too, i received this:
> 
...
ChunkSize mismatch! raw=0 idx=384 
ChunkID mismatch! raw= idx=01wb 
ChunkSize mismatch! raw=0 idx=384 
ChunkID mismatch! raw= idx=00db 
ChunkSize mismatch! raw=0 idx=7 
ChunkID mismatch! raw= idx=01wb 
ChunkSize mismatch! raw=0 idx=384 
ChunkID mismatch! raw= idx=01wb 
ChunkSize mismatch! raw=0 idx=384 
ChunkID mismatch! raw= idx=00db
...


the movie "parameters" are:
video codec: XVID MPEG-4
audio codec: MPEG 1 Audio, Layer 3 (MP3)

Does anybody have any advice how to solve that freezing?

thx in advance
8472

---

