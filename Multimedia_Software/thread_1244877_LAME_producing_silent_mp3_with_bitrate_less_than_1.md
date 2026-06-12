---
title: "LAME producing silent mp3 with bitrate less than 128kbps"
date: 2009-08-19
forum: Multimedia Software
---

### Post by Beacon11 on 2009-08-19
Hello.

I have a strange issue that I have been working on nearly all day. I'm using Ampache as a streaming media server (pretty slick), but I have a lot of .m4a files (unprotected). To stream m4a files, they are decoded on-the-fly. It wasn't working right, so to test this decoding, I tried to convert test.m4a (255kbps) into test.mp3. The command I used was:

```

faad -f 2 -w test.m4a | lame -r -b 32 -S - test.mp3

```

Notice the -b 32 argument to lame, requesting 32kbps bitrate. This command produced an mp3 with no sound. It plays the correct length, but simply has no sound. I opened it up in Audacity and there was no waveform whatsoever, just a flat line. However, if I change that command to ask for 128kbps instead of 32, like so:

```

faad -f 2 -w test.m4a | lame -r -b 128 -S - test.mp3

```

It works great! Unfortunately I want it at 32kbps. Does anyone know what I'm doing wrong? I just can't figure it out.

Thank you for any help.

---

