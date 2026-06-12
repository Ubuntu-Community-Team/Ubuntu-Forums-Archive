---
title: "Nvidia breaks anything needing linux-restricted-modules (eg WIFI) ;("
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by Ubuntiac on 2007-08-30
What I'm trying to do should be simple:

1. Have my Nvidia card run with accelerated 3d
2. Have my Atheros wifi card work

Trouble is that Atheros needs linux-restricted-modules and installing the Nvidia card removes it. Either works fine without the other, but then that's not much good for playing Tremulous now, is it? ;)

Note:My card (8600GT) is too new to be able to use the older nVidia driver.

Seems that I'm not the only onw from these previous (unanswered posts):
[http://ubuntuforums.org/showthread.php?t=525011](http://ubuntuforums.org/showthread.php?t=525011)
[http://ubuntuforums.org/showthread.php?t=526610](http://ubuntuforums.org/showthread.php?t=526610)
[http://ubuntuforums.org/showthread.php?t=529120](http://ubuntuforums.org/showthread.php?t=529120)

Thanks for any ideas!

---

### Post by 5-HT on 2007-08-30
yup, that's the problem with the restricted modules lumping everything together into one package :(. If you must use a newer nvidia driver than is provided in the repos, you'll need to get your wireless running without restricted modules. I'm not sure of which driver your card needs, but easiest thing would be to just compile it yourself.

Another thing you could do is keep the restricted modules, but divert the nvidia-common files somewhere off to oblivion, or to get rid of 'em and install the nvidia binaries from nvidia's site. Read up on dpkg --divert if you want to go that route. The only problem is upon updating restricted modules, but if you divert it properly that might not be an issue. However, the first option is by far the easiest and will cause less headaches in terms of system administration.
cheers,

---

