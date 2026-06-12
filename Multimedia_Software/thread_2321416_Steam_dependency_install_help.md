---
title: "Steam dependency install help"
date: 2016-04-22
forum: Multimedia Software
---

### Post by at35z on 2016-04-22
Hi there,

I installed steam on Ubuntu 14.04.3 64bit and whenever I start it, It says:

[IMG]http://i.imgur.com/19MMvGf.png[/IMG]

I enter my password, then the following is written out:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.6)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue: 


```

I press ENTER and Steam launches... yet every time I launch it, this message pops up.

What can I do?

---

### Post by Kerry Lange on 2016-04-22
> **at35z said:**
> 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.6)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue: 


```

I'm having exactly the same issue.

---

### Post by Kerry Lange on 2016-04-22
Actually, I just found the solution a few minutes later (at least what worked for me).  I used the following in terminal:

```

sudo apt-get install libc6:i386 libgl1-mesa-dri-lts-vivid:i386 libgl1-mesa-glx-lts-vivid:i386

```

---

