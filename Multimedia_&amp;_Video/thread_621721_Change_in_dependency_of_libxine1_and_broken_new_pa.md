---
title: "Change in dependency of libxine1 and broken new package"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by chandru.in on 2007-11-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/164801](https://bugs.launchpad.net/ubuntu/+source/xine-lib/+bug/164801) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I recently ran
```
sudo apt-get dist-upgrade
```

To my horror I found that "libxine1" depended on gnome packages while I'm a KDE user.  The fact is libxine1 depends on libxine1-plugins which depends on libxine1-gnome and so all this.

I know I can circumvent this by installing libxine1-misc-plugins instead and did so.  Now none of my video files played with kaffeine I keep getting the error
```
No video drivers initialized
```

Why all this confusion what was wrong with the previous dependencies of libxine1?  Also, why is libxine1-misc-plugins so badly broken?  Has anyone else experienced the same problem?

](*,)

---

### Post by chandru.in on 2007-11-26
Has no other Kubuntu user experienced this?

---

