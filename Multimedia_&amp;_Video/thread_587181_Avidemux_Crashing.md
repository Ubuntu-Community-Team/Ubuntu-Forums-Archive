---
title: "Avidemux Crashing"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by eklypsd on 2007-10-22
I have tried a few times to convert an avi to dvd with avidemux and am getting the following error:

Assertion Failure: ADMmplexout.cpp Line 72
Function: avidemux2gtk(ADMbackTrack+0x4b) [0x81a445b]
Function: avidemux2gtk(ZN14lFileBitStreamC1EP11PacketQueueP21mplexStreamDescriptorj+0xd4) [0x84e6974]
Function: avidemux2gtk [0x84e57cc]
Function: /lib/tls/i686/cmov/libpthread.so.0 [0xb70b046b]
Function: /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [oxb703373e]

I have tried upgrading to a newer version not in the repositories and still get the same results. I have used devede but the end result has horizontal lines. Filters used include converting to 29.97fps and resizing to 720x480. Any help would be appreciated.

---

### Post by ciscoookid on 2007-10-22
Try this tutorial:

[http://avidemux.org/admForum/viewtopic.php?pid=20330](http://avidemux.org/admForum/viewtopic.php?pid=20330)

I haven't tried it yet, but it should work.

---

### Post by eklypsd on 2007-10-22
That didn't really tell me anything new. This isn't the first time i've used the program...just the first time under Gutsy. I've used Fedora previously (F7) and had no problems at all. Any other ideas, anybody?

---

