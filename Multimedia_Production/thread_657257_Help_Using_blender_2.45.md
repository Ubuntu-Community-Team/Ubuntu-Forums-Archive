---
title: "Help Using blender 2.45"
date: 2008-01-03
forum: Multimedia Production
---

### Post by doublez on 2008-01-03
I started using ubuntu not to long ago on an extra laptop I had because I wanted to try it out. I use blender as a hobby on my main comp with xp and want to use it on ubuntu too. The blender in the repository is 2.44 and the newest version is 2.45, so I want to use the newest version. I downloaded it (linux ver of 2.45) off the blender website but I'm having problems using it. I extracted it to my home folder, then tried opening the "blender Player", nothing happened so I tried "blender", a dialogue comes up with run in terminal, display, cancel, and run. I tried all of them and nothing worked. What do I do?

---

### Post by eye208 on 2008-01-03
I guess there are some unresolved dependencies. Blender depends on several other software packages (libraries etc.). These must be installed as well, otherwise Blender will not run.

Usually when you install from the repositories, these dependencies will be resolved automatically. But this time you installed manually, from another source, so the package manager was bypassed.

Probably the easiest way to install all the required packages is by installing the 2.44 version of Blender from the repository, then uninstalling it again but keeping all the other packages which were installed along with it. Make sure to install version 2.45 to a different folder so that one version does not overwrite files of the other during that process. Or just install version 2.45 to your home folder. You can run it from there as well.

---

### Post by doublez on 2008-01-03
I got blender to work, I was missing a file so I redownloaded the files of blender.org. (of course it had to be something obvious) Now the next thing is to get indigo to work. It's a windows program so I'll have to run it under wine, right?

[http://www.indigorenderer.com/joomla/](http://www.indigorenderer.com/joomla/)

---

