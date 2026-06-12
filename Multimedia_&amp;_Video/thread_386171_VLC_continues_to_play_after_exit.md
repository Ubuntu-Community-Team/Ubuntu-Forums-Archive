---
title: "VLC continues to play after exit"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by pjman on 2007-03-16
VLC keeps playing audio even though I've exited from the application. I'm running Edgy.

Has anyone seen this before?

Thanks!

---

### Post by kobewan on 2007-03-16
> **pjman said:**
> VLC keeps playing audio even though I've exited from the application. I'm running Edgy.

Has anyone seen this before?

Thanks!

Yeah, although I'm not sure why it happens. It seems to happen when VLC isn't shutdown cleanly, and even then not all the time. To stop it, close all instances of VLC and type in ```
killall wxvlc
```

---

### Post by Byakko on 2007-04-23
> **kobewan said:**
> Yeah, although I'm not sure why it happens. It seems to happen when VLC isn't shutdown cleanly, and even then not all the time. To stop it, close all instances of VLC and type in ```
killall wxvlc
```


yay, thank god for the search bar. and thanks kobewan, it was puzzling me for a long time (take that vlc!)

---

### Post by ricardisimo on 2007-07-06
It's also happening in Feisty. Anyone know if there's a fix in the works, or a bug report to which I can append? Thanks.

---

### Post by xkendrax on 2007-07-30
I got the same problem, any fix already?

---

### Post by Majlo on 2007-07-30
Still no fix :(

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/54630](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/54630)

Please update bug .

PS : bug doesn`t occure if you use skinned interface 
vlc -I skins2

---

### Post by ozzyprv on 2007-08-23
> **Majlo said:**
> Still no fix :(

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/54630](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/54630)

Please update bug .

PS : bug doesn`t occure if you use skinned interface 
vlc -I skins2

Thank you!

---

