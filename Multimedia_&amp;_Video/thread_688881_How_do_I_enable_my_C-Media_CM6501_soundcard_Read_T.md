---
title: "How do I enable my C-Media CM6501 soundcard? Read This!"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by lakersforce on 2008-02-05
Go to System->Preferences->Sound and set everything to USB Audio.

Then run this from the command line:
```
asoundconf set-default-card default
```

---

