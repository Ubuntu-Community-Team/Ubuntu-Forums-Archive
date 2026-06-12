---
title: "AAC Compression Levels using nautilus-script-audio-convert"
date: 2007-09-19
forum: Multimedia Production
---

### Post by chriswyatt on 2007-09-19
Hi, I just installed nautilus-script-audio-convert to convert my FLACs to AAC format but it asks me to set a compression level, this is either 100, 200, 300, 400 or 500.  I expected to be able to select the bitrate, I wanted all my AACs to be at 256Kbps.  I tried using the default, 300, and checked the bitrate of the file under Nautilus but it's not reported :( .

Do these values correspond to bitrate or is this something else entirely :S .  Or is there another solution to convert my FLACs to AACs?  If all else fails I could just rerip my CDs.

EDIT: Could someone delete this message?  I've reposted this in Multimedia & Video, didn't see it eariler, sorry ...

---

### Post by stmiller on 2007-09-20
FAAC encodes by quality level. -q 150 is a high quality AAC (higher encoding rate than iTunes). I think -q 100 is the default.

So that may be asking for the faac quality setting, but I'm not 100% sure.

---

