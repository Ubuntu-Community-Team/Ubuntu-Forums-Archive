---
title: "Java related media problem?"
date: 2009-07-12
forum: Multimedia Software
---

### Post by Ifrgtmyname on 2009-07-12
Hey guys and gals,

I have a very strange problem with my 64-bit hardy system. Sometimes media files just don't play on my computer, they stick on 0:00 with all media players (Movie player, Exaile, Rythmbox). Today I have found how to replicate the problem: I play an online Java game called runescape (runescape.com) and if I load up runescape before playing a media file, the media file will not play. If I play the file before loading runescape, it will continue to play along with runescape (I can even close the media player and re-open it and it will still work).

The problem is, I have no idea where to start fixing this problem. I have tried some sketchy internet searches but have found nothing because I'm really not sure what to search for! I am also not sure which log files to post so if you want to see any just give me a shout.

Thanks

---

### Post by 6205 on 2009-07-12
Let's start with question, Do you need 64-bit version? I don't like them and don't trust them..

---

### Post by Ifrgtmyname on 2009-07-12
I like my 64-bit system! And I am fairly unconvinced that that is what is causing the problem!

---

### Post by raboofje on 2009-07-12
Perhaps java is taking exclusive control over your sound card?

This might be related to this launchpad item: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/209198](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/209198)

---

### Post by Ifrgtmyname on 2009-07-12
> **raboofje said:**
> Perhaps java is taking exclusive control over your sound card?

This might be related to this launchpad item: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/209198](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/209198)

It looks like a very similar problem (and he's running 32 bit!) Thanks!

---

