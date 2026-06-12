---
title: "Kid3 now you see it now you dont"
date: 2020-12-26
forum: Multimedia Software
---

### Post by aughey on 2020-12-26
I have two laptops. I recently upgraded both to Ubuntu 20.10. There is a programme I use a lot to title mp3s called kid3. On the HP laptop two versions of Kid3 appeared in the briefcase of available software. However on my Toshiba it told me there was no such package available. I had to Google it and use the terminal to install it from the developers website on that machine. Why should that be? PS is there a way to use a cable or remmina for example to install software on one machine to the other without needing to use the internet?

---

### Post by CatKiller on 2020-12-26
That package is in the Universe repository, which you'd need to enable for it to show up in your package management tools.

---

### Post by Yellow Pasque on 2020-12-26
Compare the output of this on your two machines:
```
apt-cache policy kid3
```

kid3 is part of the Ubuntu repo, so I'm not sure why you're having trouble with it, unless you have PPA's interfering on the one machine.
[https://launchpad.net/ubuntu/+source/kid3](https://launchpad.net/ubuntu/+source/kid3)

> **CatKiller said:**
> That package is in the Universe repository, which you'd need to enable for it to show up in your package management tools.

Universe is enabled by default on Desktop installs. On the Live media and maybe on Server installs, it isn't.

---

