---
title: "pulseaudio &gt;= 0.9.30 in Intrepid??"
date: 2008-12-18
forum: Multimedia Software
---

### Post by night-wing on 2008-12-18
Hello.

I've tested Fedora 10 for a week and I must say, that it works much better on my two notebooks, as intrepid does. Especially Pulseaudio works better and all system sounds run perfectly.

Fedora 10 works with pulseaudio 0.9.30. Intrepid with 0.9.10.

Is there any way to get a newer pulseaudio work in intrepid? Maybe
via external repos?

Regards
nightwing

---

### Post by markbuntu on 2008-12-18
You would need to compile it from source as far as I know. Someone might have made some debs somewhere in launchpad.....

I don't have big hopes really for ubuntu and pulseaudio. ubuntu does not even provide pavucontrol in the desktop seed.

0.9.13 is still unstable and the Fedora version is heavily patched. The best we can hope for is maybe 0.9.12 in Jaunty.

---

### Post by night-wing on 2008-12-19
But it's a shame, that after gutsy gibbon, ubuntu isn't able to play even system sounds or shutdown sounds. That are a lot of steps backwards.

Why can't the programmers make a new release more stable instead of putting more and more features in it, which only few use.

---

### Post by racb on 2008-12-21
I backported jaunty's 0.9.13 yesterday and stuck it in my PPA for use with intrepid. I did it for bluetooth support. The package seems to install and work; I haven't tried it with bluetooth yet.

[https://launchpad.net/~racb/+archive](https://launchpad.net/~racb/+archive)

---

