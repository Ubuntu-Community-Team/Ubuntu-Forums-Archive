---
title: "No sound watching movies on 12.04 LTS"
date: 2014-01-15
forum: Multimedia Software
---

### Post by deaton25 on 2014-01-15
I don't have any sound on the movies I'm watching. I installed Ubuntu Restricted and then what happened??!!
This has never happened before! I am on Ubuntu 12.04

---

### Post by mastablasta on 2014-01-16
interesting. how about a bit more information? [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Bucky Ball on 2014-01-16
*Thread moved to **Multimedia & Video**.*

Can't boot machine, blank screen, hardware failure, unusable system. That's urgent. Most the posts here; urgent. The majority of posters here would consider their issue to be urgent. 

Consequently, I have moved the thread and changed your thread title to something more descriptive of *your* issue in the hopes you might have a better chance of getting support. Good luck.

Try a terminal and type:

```
alsamixer
```

Anything muted in there? Using the right sound card? Click F6 to see what's available. I generally use Pulseaudio Volume Control to adjust sound which can be installed with:

```

sudo apt-get install pavucontrol
```

---

