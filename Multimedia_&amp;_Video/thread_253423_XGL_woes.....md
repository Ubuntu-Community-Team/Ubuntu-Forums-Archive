---
title: "XGL woes...."
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by Martin A on 2006-09-08
Before I begin, I would like to state that this has happened FOUR times now....

I have Ubuntu 6.06 running XGL/Compiz, It all works great until I click on the software update icon.... once everything is updated the X server craps out completely and all I get if I try to start XGL/Compiz is 
```

compiz: couldn't load plugin: gconf

```

And so once this has happened I have to reformat and start again. Only now now that I've done a reformat/reinstall the problem is still here. So if someone can help me fix this problem and XGL/Compiz working again, I swear I will never touch that stupid software update icon again :confused: 
I'm using an Nvidia Geforce 6800, 3D accel works fine (until I start XGL then I get no direct rendering)....

Anyone?

---

### Post by whatever on 2006-09-08
start compiz with /usr/bin/compiz-start instead of your custom script and use csm for configuration.

> **Martin A said:**
> 3D accel works fine (until I start XGL then I get no direct rendering)
Xgl + direct rendering is impossible by design.

---

### Post by whatever on 2006-09-08
wrong button, accidently hit quote instead of edit... ;)

---

