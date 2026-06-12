---
title: "No Sound"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by skinnie339 on 2007-06-06
I'm running Feisty 7.04 64 bit.  I have no sound when logged in as my own user, but when I run Totem from sudo, sound works perfectly.
Any Help?

---

### Post by NeoLithium on 2007-06-06
```

alsamixer

```

Make sure you have all the volumes turned up and nothing muted inside there.  Perhaps that could be it?

Hope this helps,

---

### Post by skinnie339 on 2007-06-06
returned with this:
alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by NeoLithium on 2007-06-06
Hmmm, I did a bit of searching, perhaps this post will offer some help?
[http://ubuntuforums.org/showthread.php?t=418360&highlight=alsamixer%3A+function+snd_ctl_open+failed+for+default%3A+No+such+device](http://ubuntuforums.org/showthread.php?t=418360&highlight=alsamixer%3A+function+snd_ctl_open+failed+for+default%3A+No+such+device)

---

