---
title: "Can't play Youtube Video's?"
date: 2014-02-17
forum: Multimedia Software
---

### Post by dapps2 on 2014-02-17
Have only just installed Lubuntu 13.10 (i686) and then i ran ```
sudo apt-get update && sudo apt-get upgrade
```. I then tried to play a Youtube video but all i got was a white screen?

---

### Post by SeijiSensei on 2014-02-17
Did you check the boxes during installation to include "restricted" items?  One of them is Adobe flashplayer since it is distributed without any source code.  Try "sudo apt-get install flashplayer-installer" and see if that helps.

If you didn't install the restricted items already, you should also run "sudo apt-get install ubuntu-restricted-extras" to get packages to support audio and video playback and the Microsoft web fonts like Arial and Tahoma.

---

### Post by dapps2 on 2014-02-17
Have done as you suggested and now i can watch + listen to Youtube video's. Thanks SeijiSensei

---

