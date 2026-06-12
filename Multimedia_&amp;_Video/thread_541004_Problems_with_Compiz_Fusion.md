---
title: "Problems with Compiz Fusion"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by light-angel on 2007-09-02
I've been trying to install Compiz Fusion using two different guides. all worked out fine but at the end when i type  "Compiz --replace &" or "compiz --replace" the window borders are gone and none of the 3D effects works :???:

also when i write compiz --replace in the console this appears:
[HTML]
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070828
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'
[/HTML]

when i write Compiz --replace & this appears:
[HTML]
light-angel@Heaven:~$ Compiz --replace &
[1] 6255
light-angel@Heaven:~$ bash: Compiz: command not found

[1]+  Exit 127                Compiz --replace
light-angel@Heaven:~$
[/HTML]

I've taken this measures to make it work :

1. I've written Option "AddARGBGLXVisuals"  "True" in the xorg file, at the end of the device section and then write Compiz --replace & .

2. I've write emerald, kwin, kde-window-manager in the command option in the window decorator on the compizconfig settings manager.

None of this works so far.

guides I've follow:

This is the main one
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

i use this for the xorg configuration
[http://ubuntuforums.org/showthread.php?t=499368](http://ubuntuforums.org/showthread.php?t=499368)
_____________________________________________________________________________
about my system:

Dell Dimension 3100
Video: Dell Graphics i915
Processor : Intel Pentium IV 2.8
RAM : 256 MHz

---

### Post by smithman89 on 2007-09-02
First, it seems that your compiz isnt fully updated (hence the first error stating that one package is from 7/8/07, and needs to be compatible with a newer package 8/28/07).  Try updating your compiz.  Second, if the window borders go away, go to the compiz config settings manager and select window manager, that gives you the borders.  
Thirdly, the second command you gave, it has to be lower case:  compiz --replace &
Hope this helps :D

---

### Post by light-angel on 2007-09-02
thanks for all, but i still a little help, how do i update the compiz? do i use something like apt-get update compiz-fusion?

i tried using kwin and kde-window-decorator and nothing happend :S

by the way, i refer to the command option in window decoration, there is where i put emerald, kwin or kde-window-manager

---

### Post by smithman89 on 2007-09-02
im not familiar with KDE, all i would say is check the package manager and if necessary, re install compiz-fusion, or if available update it.

---

