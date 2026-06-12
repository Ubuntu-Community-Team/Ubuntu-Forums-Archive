---
title: "Skype Problems"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by CrAzY12 on 2011-01-09
Just downloaded skype and I have two problems with it. 
1. The video of me from my web cam is upside down (it is a built in web cam so that isnt possible)
2. The other person on the other line can not hear me speak. 
From my understanding Skype does not have a fully operational skype for Ubuntu. But It could be misleading information. Any suggestions?

---

### Post by mikewhatever on 2011-01-09
Let's see if we can get it to work anyway.

_webam_
Try launching skype from a terminal window with the following command, then test the webcam:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype &
```

_microphone_
Obviously, you mic isn't working, Make sure it's not muted in the Sound Preferences.

---

