---
title: "All users but me have sound..."
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by nightmareci on 2006-09-29
So yeah, even the login screen's little drum sound plays, yet I don't have sound at all. And sound worked before today, so I don't need to compile/install any special drivers. I've followed the "Comprehensive Sound Problem Solutions Guide", but purging and reinstalling all that software just put me back where I started. So, what can I do to get back audio in my user?

---

### Post by morphodone on 2006-09-29
maybe your user got knocked off the audio group...i wouldn't think
that would be the case but you never know.


you can check the /etc/group file.

```
sudo nano /etc/group
```

look for the audio group and make sure your user name is listed

---

### Post by nightmareci on 2006-09-30
Thank you very much! That was EXACTLY the problem I was having. Turns out theres some other groups I'm not part of, so I should add myself to those other groups when need-be. Weird, I wouldn't know what could cause this.

---

