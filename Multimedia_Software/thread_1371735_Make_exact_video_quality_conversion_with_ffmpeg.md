---
title: "Make exact video quality conversion with ffmpeg"
date: 2010-01-03
forum: Multimedia Software
---

### Post by needhelppeeps on 2010-01-03
I spent about a half hour wrestling with different website tutorials about how to convert a file with ffmpeg and figuring out how to get all the video quality options right. Then I discovered you can just use the -sameq option and it figures it all out for you if you don't want to change the vid quality but just want it in another format. Thought I'd leave this on the site in case anyone else finds himself in the same boat.

---

### Post by FakeOutdoorsman on 2010-01-03
The *-sameq* option should only be used when converting to and from formats that use the same **quantizer scale**.  For example, the following encoders use the *mpeg* quantizer scale: flv, h263, h263+, mpeg1, mpeg2, mpeg4, msmpeg*.

---

