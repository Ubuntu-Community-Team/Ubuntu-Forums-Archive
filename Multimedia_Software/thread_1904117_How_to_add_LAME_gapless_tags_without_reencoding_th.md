---
title: "How to add LAME gapless tags without reencoding the MP3s?"
date: 2012-01-04
forum: Multimedia Software
---

### Post by noah++ on 2012-01-04
Hi,

I have a set of MP3 files that were not encoded with LAME. I don't know of any Linux audio player that can play MP3 gaplessly without these tags (even if DEADBEEF can usually come close). Now that I have them, how can I simply add gapless tags to them without reencoding the files and suffering quality degeneration? I've Googled around, and haven't been able to find a way.

---

### Post by satanselbow on 2012-01-04
You could try adding the "ITUNESGAPLESS" with a value of "1" to each file... poor support for that on Windows (let alone Linux) media players (including itunes), however.

Either that or manually contruct a cuefile?

---

### Post by noah++ on 2012-01-05
Here's an informative response I got from Mike Brown on the official LAME site:

> There are two kinds of gapless MP3s. The kind produced by LAME's old gapless options is just a single stream chopped into sections on frame boundaries, and you (or the player) are supposed to concatenate them before or during playback. This technique was largely abandoned before it gained much traction. The other, currently popular kind is what LAME produces by default (no special options needed), where each file is a separately encoded stream, with metadata in it telling the player how many delay & padding samples to skip on each end to get the part of the stream that corresponds to the original sample set. This may not be perfectly seamless but is the definition of gapless that people generally want.

If the encoder was LAME, the encoder delay is known, and for CD-sourced material (multiples of 588 samples), the padding can be guessed at, or even confirmed if you have access to the exact track length from the original CD. Otherwise, there's no way to know for sure. If the encoder is unknown, then not even the delay is certain. So I don't think there's really a way to do what you want automatically. _[Further reading.]("http://wiki.hydrogenaudio.org/index.php?title=Gapless_playback")_

---

