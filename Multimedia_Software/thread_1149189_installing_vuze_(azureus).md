---
title: "installing vuze (azureus)"
date: 2009-05-05
forum: Multimedia Software
---

### Post by sonaural on 2009-05-05
downloaded the installer i can't figure out what to do from there or which file to run.  has anybody else had problems with this i don't remember it being this complicated on my last computer?  souldn't there just be a file that you click on which installs the program?

---

### Post by edwardTheGreat on 2009-05-05
I installed it from the ubuntu repo and it works fine for me.
In my experience the open-jdk was required as well (correct me if I'm wrong someone) even if you already have sun's jdk installed (which I did). This is how I installed it.

In a terminal type:

```
sudo apt-get install openjdk-6-jdk vuze
```


and then it should be available in under Applications --> Internet

---

### Post by sonaural on 2009-05-05
thanks for the tip, i think my comp was justing brainfarting... seems to have sorted itself

---

### Post by edwardTheGreat on 2009-05-05
No drama then, at least it's documented now for anyone else having the issue :)

---

