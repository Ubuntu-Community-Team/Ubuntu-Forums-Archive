---
title: "can't run playdv from bash script"
date: 2013-07-17
forum: Multimedia Software
---

### Post by jwladd on 2013-07-17
right up front: am linux noob
setting up machine strictly for dv/1394 capture & encode; found skullmunky's 1/23/11 post very helpful.
am running command line dvgrab piped into ffmpeg to produce a (don't laugh, have to do for compat sake) wmv for weekly upload to website.
works great, but would like preview, so as suggested in skullmunky's post, used tee to send to both ffmpeg & playdv (avconv).
this works great too, as long as typed into terminal & run, but when try to run from bash script, can't get to run.. later in testing, found couldn't get playdv to ever run from script.
couldn't find much on playdv to explain why couldn't call from script.. am from M$ world, pretty familiar w/scripting & batch files, at a loss on this one.
ex:
dvgrab -f dv1 - | tee >(ffmpeg -f dv -i - -b 1500k -ab 128k -strict experimental -y -vcodec msmpeg4 -acodec wmav2 201307071000M.wmv) >(playdv --disable-audio --no-mmap)

---

### Post by jwladd on 2013-07-18
resolved.

---

### Post by FakeOutdoorsman on 2013-07-18
This type of post is particularly annoying for those looking for an answer. Why did you not provide details on how you resolved it?

---

