---
title: "ubuntu 11.04 unity wont run on hp machine"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hunterkasy on 2011-04-12
I have a hp pavilion a1007w with the standard hardware that comes with the machine.  I decide to test out 11.04 so I did a upgrade from 10.10 to 11.04. upgrade went well, and when I rebooted and logged in, it said something about my hardware is not compatible to run unity.  also it said to select classic at next login.

is this normal or a bug?

also if it is normal, I read somewhere that in 11.10 ubuntu will not be shipping with the classic version as an option.  if that is true will ubuntu be able to work on older machines? or would we have to switch to kde or xubuntu?

---

### Post by arpanaut on 2011-04-12
With this integrated video chip "SiS Mirage 2 Shared video memory (UMA)" that came stock you are pretty much out of luck running Unity 3d, it will run Classic or unity 2d just fine... If you want 3d you would need to find an AGP video card that is supported for 3d acceleration.  A gforce 6000 or higher or Something higher than a Radon Pro 9800. 
Unfortunately most of the AGP stuff is going the way of the Dodo.

---

### Post by hunterkasy on 2011-04-12
> **arpanaut said:**
> With this integrated video chip "SiS Mirage 2 Shared video memory (UMA)" that came stock you are pretty much out of luck running Unity 3d, it will run Classic or unity 2d just fine... If you want 3d you would need to find an AGP video card that is supported for 3d acceleration.  A gforce 6000 or higher or Something higher than a Radon Pro 9800. 
Unfortunately most of the AGP stuff is going the way of the Dodo.

thanks for the info.

I have another question,  you said I should be able to run classic (which I am) and I should be able to run unity 2d. my question is, how do I run unity 2d?

---

### Post by awam66 on 2011-04-12
You download Unity 2d from the repositories and install it.

---

### Post by kansasnoob on 2011-04-12
The proper package name is 'unity-2d' and it is in the repos, but there is also a good ppa with newer and fairly reliable packages:

[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

Full disclosure: I do NOT like Unity :(

---

### Post by hunterkasy on 2011-04-12
> **kansasnoob said:**
> The proper package name is 'unity-2d' and it is in the repos, but there is also a good ppa with newer and fairly reliable packages:

[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

Full disclosure: I do NOT like Unity :(

thanks for all your help on here (everyone) I have it installed and it is running,  for me unity don't bother me at least not yet. I don't do any business work or any work at all.  I just mostly use fire-fox, watch movie listen to music and games mostly flash Internet games.  

The reason I asked how to use unity 2-d is, I assumed it would have been installed along side 3-d because unity is going to be the default.  and I just assumed if the pc is not 3-d combat-able 2-d would be the default then

---

