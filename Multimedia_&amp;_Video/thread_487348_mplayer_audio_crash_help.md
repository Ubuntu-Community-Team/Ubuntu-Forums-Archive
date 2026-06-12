---
title: "mplayer audio crash help"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by zerocle on 2007-06-29
So i was watchin a movie in mplayer, very happy with myself that i just setup linux all by myself, when all of the sudden i get MPlayer interrupted by signal 11 in module: decode_audio. I know this is happening in the mplayer ac3 audio codec, but other than that, I couldnt tell ya. Im using onboard sound, so i dont really know how it could be a sound card issue. I ran a gdb and waited for it to crash, when it did "where" gave me this:
#0 0x087648b7 in imdct_do_512_see ()
#1 0x08ce8f00 in ?? ()
#2 0x00000002 in ?? ()
#3 0x00000002 in ?? ()
#4 0x43c00000 in ?? ()
#5 0x08760918 in a52_block ()
#6 0x08d61c00 in ?? ()
#7 0x00000007 in ?? ()

Thanks ahead of time for the help guys, i really appriciate it!

---

