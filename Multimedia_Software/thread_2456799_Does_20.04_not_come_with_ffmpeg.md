---
title: "Does 20.04 not come with ffmpeg?"
date: 2021-01-20
forum: Multimedia Software
---

### Post by Swan_DB on 2021-01-20
Does 20.04 Focal fossa not play MPEG4 vidoes?  How can I check if I have it installed or not?  
[B]EDIT: Also, sorry if this is the wrong sub forum, I'm new.

VLC player seems to work, but I don't like it...  not sure why I don't like it, but I just don't.  Maybe because VLC player didn't work well on my windows 7, idk...[/B]

---

### Post by CelticWarrior on 2021-01-20
Any system plays any media file as long as it understand it. And in order to understand the format the system needs codecs.
Start by installing 'ubuntu-restricted-extras'

```
sudo apt install ubuntu-restricted-extras
```

Ffmpeg is not required to play mpeg4 files but you can install it as well.

---

