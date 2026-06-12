---
title: "Problem with nvidia driver"
date: 2009-02-09
forum: Multimedia Software
---

### Post by alexjm on 2009-02-09
Hello & welcome me here. (& sorry for my bad English, it's my native language)
i have this problem:
I've put a new cooling system to my graphic card (9800gt) and from then i can't log in in ubuntu (either in vista, i have a double boot). My pc boots normally, i choose to continue with ubuntu (the last kernel of 8.10), it seems that ubuntu is loading, but when it comes to autologin and show me the desktop, i have a black scree, while the computer is still working.
I try to log in with ubuntu recovery mode, and there i choose "xfix" and i can log in normally.
I think that i should remove the nvidia drivers and then reinstall them.
I am correct, and if yes how should i do this?
Thanks..

---

### Post by Ataris on 2009-02-09
I wouldn't recommend that.

Do the instructions in my post on this thread: [http://ubuntuforums.org/showthread.php?t=870013&page=2](http://ubuntuforums.org/showthread.php?t=870013&page=2)

If that doesn't work, I have another solution that I know will work. If you can run 3d just fine, however, then starting up the PC in recovery mode may have fixed the problem.

I have experienced this problem many times and used different solutions. Ubuntu isn't quite there yet with reliability, I'm afraid.

---

### Post by alexjm on 2009-02-09
> **Ataris said:**
> I wouldn't recommend that.

Do the instructions in my post on this thread: [http://ubuntuforums.org/showthread.php?t=870013&page=2](http://ubuntuforums.org/showthread.php?t=870013&page=2)

If that doesn't work, I have another solution that I know will work. If you can run 3d just fine, however, then starting up the PC in recovery mode may have fixed the problem.

I have experienced this problem many times and used different solutions. Ubuntu isn't quite there yet with reliability, I'm afraid.

how  i download the envyng?
sudo apt-get install envyng-gtk    ????

---

### Post by alexjm on 2009-02-09
neither i can enable the 3d effects, or i can use nvidia settings..

---

### Post by norwoods on 2009-02-10
i used synaptic to install nvidia driver 180.27 from

[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

and all seems good. be sure to change the

apt sources.list entries
Display sources.list entries for:

drop down list box from jaunty to intrepid and follow the instructions.

---

