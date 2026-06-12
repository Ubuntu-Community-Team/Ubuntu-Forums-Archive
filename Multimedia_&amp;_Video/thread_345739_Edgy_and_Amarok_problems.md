---
title: "Edgy and Amarok problems"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by jabzwnein on 2007-01-24
Since upgrading to Edgy and finally getting Beryl installed, I haven't been able to use amarok to play, well, anything.  I'd never had problems before, but now amarok says it can't play mp3s and wma's won't play (altho it says they're playing).  I get the same problems with Banshee, although Rhythmbox still works fine with everything.  What do I need to do to fix this?  Altho amarok gives me the option of downloading something to enable mp3 play, clicking this button doesn't do anything.

Any ideas?  I really like amarok over Rhythmbox...

---

### Post by teitunge on 2007-01-24
You need to install some codecs.
Have you read what it says in the 'restricted formats'?

[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

hopefully this will help you.

---

### Post by jabzwnein on 2007-01-24
I thought that's what the problem was, too.  Somehow, I thought maybe the upgrade deleted the codecs I had previously installed.  But then why does Rhythmbox work?  I looked to see if I have the libxine-extracodecs and I do, it's the most recent version, too.  So that doesn't seem to solve the problem.

---

### Post by jabzwnein on 2007-01-28
bump

---

### Post by jabzwnein on 2007-01-28
Solved the problem!  Somehow, the multiverse became deselected during my upgrade to Edgy.  Once I reselected it, I had about 12 updates to download and now everything works.

---

