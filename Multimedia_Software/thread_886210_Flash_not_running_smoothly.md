---
title: "Flash not running smoothly"
date: 2008-08-10
forum: Multimedia Software
---

### Post by jeanniegenie on 2008-08-10
if I'm trying to play a video, i always get this big diagonal split in the middle of the video, which makes the video really choppy. So it also wouldn't fit with the sound because the picture is being split in 2 making it run slower. I tried playing videos without sound but that still showed the evil diagonal.  >_<

i never had this problem before, and I'm not sure when it started. I slightly want to blame these backports i downloaded via update manager because I didn't want to install them since flash was working okay but I ended up installing them because....I don't know. I guess I had a dumb moment. But I'm not sure if that really is the problem.

help? >.<

Oh and i'm using 8.04

---

### Post by eye208 on 2008-08-11
Enter "about:plugins" into the URL bar of Firefox and tell us which version of Flash you are using.

---

### Post by jeanniegenie on 2008-08-11
flash 9.0 :)

---

### Post by eye208 on 2008-08-12
Flash 9 on Linux does not yet use video acceleration features provided by graphics cards (e.g. XVideo overlay etc.). So unfortunately it's quite normal to see some tearing. Full motion videos are affected more than those with rather static content.

Flash 10 is supposed to fix this, but it is not quite stable at the moment. There is a Firefox extension to download any Flash video and play it in an external media player, bypassing Flash's poor video performance. Most Flash videos also end up in the /tmp folder, so you can open them from there.

---

### Post by jeanniegenie on 2008-08-12
aw okay :< well, thanks for that /tmp tip. it helps : )

---

