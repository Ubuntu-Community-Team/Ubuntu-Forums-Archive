---
title: "handbrake-cli on Jaunty 9.4: libstdc++6 not satisfiable"
date: 2009-11-29
forum: Multimedia Software
---

### Post by mrdek11 on 2009-11-29
Hi!
I'm trying to install handbrake-cli on my Jaunty 9.04 system using this deb: [http://handbrake.fr/rotation.php?file=HandBrake-0.9.4-Ubuntu_CLI_i686.deb]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.4-Ubuntu_CLI_i686.deb")

However, when I try to install it, it says: ```
Dependency is not satisfiable: libstdc++6 (>= 4.4.0)
```

I can't figure out why a package built specifically for 9.4 would have unmet dependencies...
Does anybody have any idea what I can do?

Thanks,
Derek

[edit]
Turns out I wasn't reading the deb name closely enough. It is for HandBrake 9.4, NOT Ubuntu 9.04.

[http://forum.handbrake.fr/viewtopic.php?f=13&t=13309&p=65114&hilit=ubuntu+9.4+install#p65114](http://forum.handbrake.fr/viewtopic.php?f=13&t=13309&p=65114&hilit=ubuntu+9.4+install#p65114)
[/edit]

---

### Post by bumanie on 2009-11-29
Try going to synaptic package manager and typing libstdc++6 in search and then see if there is a package 4.40 or greater. If not installed, mark for installation and see if handbrake will install after that.

---

### Post by mrdek11 on 2009-11-29
> **bumanie said:**
> Try going to synaptic package manager and typing libstdc++6 in search and then see if there is a package 4.40 or greater. If not installed, mark for installation and see if handbrake will install after that.

Thanks for the tip!
It looks like the newest package is 4.3.3-5ubuntu4 :(

---

### Post by JohnAStebbins on 2009-11-30
You can also get handbrake 0.9.4 for ubuntu 9.04 from this PPA
[https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa](https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa)

---

