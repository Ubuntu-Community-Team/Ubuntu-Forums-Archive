---
title: "video codec problem"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by tsunade on 2006-08-11
When i play an xvid video i get weird colors in it. I think it's only with xvid movies, not with divx, because some movies don't have the problem and i think they are divx.

As an example i have attached a screenshot from a video. As you can see there is a green border on the top side and a part of the video has a gray/pink overlay.

Somebody knows the problem?

---

### Post by s6dalane on 2006-08-11
Try installing all the codecs from [this]("https://help.ubuntu.com/community/RestrictedFormats") guide. I have no problems playing XViD files.

---

### Post by tsunade on 2006-08-11
thank you, problem solved =)

i think the problem was with the w32codecs that i didn't have installed yet: [https://help.ubuntu.com/community/RestrictedFormats#w32codecs](https://help.ubuntu.com/community/RestrictedFormats#w32codecs)

---

### Post by whatever on 2006-08-11
looks funny :)
somehow the chroma information got shifted downwards and therefore it doesn't match the luma information anymore.

---

