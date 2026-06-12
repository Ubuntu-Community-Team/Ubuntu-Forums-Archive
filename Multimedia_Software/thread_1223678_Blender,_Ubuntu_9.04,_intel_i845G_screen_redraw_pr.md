---
title: "Blender, Ubuntu 9.04, intel i845G screen redraw problem."
date: 2009-07-26
forum: Multimedia Software
---

### Post by Intertricity on 2009-07-26
I have a Sony PCG-TR2a, in windows Blender worked just fine, but in Ubuntu, I get this type of problem:

[http://intertricity.com/projectr/blenderProblem.png](http://intertricity.com/projectr/blenderProblem.png)

Any clue what could be going wrong? :\

---

### Post by mikejedw on 2009-07-26
I ran into something similar.  It might be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/353763").

---

### Post by mikejedw on 2009-07-26
Oh, sorry, forgot the most helpful bit.  You can get around the problem for now by launching Blender from the command line like so:

LIBGL_ALWAYS_SOFTWARE=1 blender

Runs Blender in software GL mode.  A little slow when using the Game Engine in fully textured mode, but more than okay for just about everything else.

---

### Post by Yunow on 2009-07-28
Yes!!! works...

Blender for linux have a blender-softwaregl...

```
#!/bin/sh
BF_DIST_BIN=`dirname "$0"`
BF_PROGRAM="blender" # BF_PROGRAM=`basename "$0"`-bin
exitcode=0

LD_LIBRARY_PATH=${BF_DIST_BIN}/lib:${LD_LIBRARY_PATH}

if [ -n "$LD_LIBRARYN32_PATH" ]; then
	LD_LIBRARYN32_PATH=${BF_DIST_BIN}/lib:${LD_LIBRARYN32_PATH}
fi
if [ -n "$LD_LIBRARYN64_PATH" ]; then
	LD_LIBRARYN64_PATH=${BF_DIST_BIN}/lib:${LD_LIBRARYN64_PATH}
fi
if [ -n "$LD_LIBRARY_PATH_64" ]; then
	LD_LIBRARY_PATH_64=${BF_DIST_BIN}/lib:${LD_LIBRARY_PATH_64}
fi

export LD_LIBRARY_PATH LD_LIBRARYN32_PATH LD_LIBRARYN64_PATH LD_LIBRARY_PATH_64 LD_PRELOAD

"$BF_DIST_BIN/$BF_PROGRAM" ${1+"$@"}
exitcode=$?
exit $exitcode

```

---

### Post by Intertricity on 2009-08-01
Thanks a bunch you guys :)

---

### Post by Nickemans on 2009-08-08
Sorry for the noob question, but how do you use that code that fixed the problem?
Cheers!

---

### Post by AROtotheN on 2009-08-13
@Nickemans just open your terminal and type:

```
LIBGL_ALWAYS_SOFTWARE=1 blender
```

this will actually launch Blender, and your Blender session will be drawn in softwareGL, worked for me, too. ={D

Aaron

---

### Post by Nickemans on 2009-08-14
> **AROtotheN said:**
> @Nickemans just open your terminal and type:

```
LIBGL_ALWAYS_SOFTWARE=1 blender
```this will actually launch Blender, and your Blender session will be drawn in softwareGL, worked for me, too. ={D

Aaron

Ah cheers!
Is there any way to make a link or launcher or something with that code in it so you don't have to open a terminal and type that in every time you want to launch blender?
I don't think I could remember all that :P

---

### Post by AROtotheN on 2009-08-14
Nope, unless a more experienced user knows how to make one...

I tried searching for a way to launch terminal and the code using the same launcher, but came up with no success. I'd love to know how to create one as well.

in the mean time.

LIBGL_ALWAYS_SOFTWARE=1 blender

LIBGL_ALWAYS_SOFTWARE=1 blender

LIBGL_ALWAYS_SOFTWARE=1 blender

LIBGL_ALWAYS_SOFTWARE=1 blender

see? Now I have it memorized!!!

---

### Post by Nickemans on 2009-08-15
Hahaha nice :P
Thanks!

---

### Post by Siljrath on 2009-08-16
> **AROtotheN said:**
> Nope, unless a more experienced user knows how to make one...

I tried searching for a way to launch terminal and the code using the same launcher, but came up with no success. I'd love to know how to create one as well.

in the mean time.

LIBGL_ALWAYS_SOFTWARE=1 blender

LIBGL_ALWAYS_SOFTWARE=1 blender

LIBGL_ALWAYS_SOFTWARE=1 blender

LIBGL_ALWAYS_SOFTWARE=1 blender

see? Now I have it memorized!!!

sry for folks in gnome or other stuff, but in openbox, i set up my old blender keyboard shortcut which i had originally configured with the command as just *blender*, and now to *terminator --command="LIBGL_ALWAYS_SOFTWARE=1 blender"*, n thats a far more minor an inconvenience to have a terminal open in the background when starting from just pressing tux and 3, than not having the graphics running, or having to remember to type in  *LIBGL_ALWAYS_SOFTWARE=1 blender*.  ;)  so if you're in openbox, just add the code bellow to your rc.xml (which will give you the same keyboard shortcut as me).  otherwise, you can likely find success by adding *terminator --command="LIBGL_ALWAYS_SOFTWARE=1 blender"* to the appropriate section in creating a button in gnome, or a menu, or wherever.   be sure to change terminator to the name of your terminal app.   ... n i think that should work for ya.  :)


```
    <keybind key="W-3">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>3D Graphics</name>
        </startupnotify>
        <command>terminator --command="LIBGL_ALWAYS_SOFTWARE=1 blender"</command>
      </action>
    </keybind>
```
if u dont like keyboard shortcuts, n prefer menus, you could also just replace *blender* with *terminator --command="LIBGL_ALWAYS_SOFTWARE=1 blender"* in your menu.xml.

still, this is just a workaround, and not a fix to the original problem.
i have the same issue with blender2.48a & i945 (as opposed to i845).

but it is very nice to at least have it back to some kind of functional level.  :)
thnx guys

---

### Post by ReaperSWE on 2009-08-16
Just had the exact same drawing issue here, this workaround fixed it all! I was so pleased by the simple solution, that I decided to pitch in with what I can help.

> **Nickemans said:**
> Ah cheers!
Is there any way to make a link or launcher or something with that code in it so you don't have to open a terminal and type that in every time you want to launch blender?
I don't think I could remember all that :P

Go to your home folder, make a new empty file, enter:
```
#!/bin/bash
# Blender workaround launcher
LIBGL_ALWAYS_SOFTWARE=1 blender
```
Open a new terminal, do **sudo chmod +x filename**
Now you should be able to run that script to launch blender in software GL mode.

Assuming you're using the Ubuntu Main Menu, open the Main Menu editor (rightclick the menu icon), find the Blender launcher, and change the Command property where your script is. (browse)

---

### Post by Nickemans on 2009-08-17
Sweet!
Haven't been able to try any of these since my Ubuntu laptop crashed yesterday and needs the motherboard replacing! D=

Kinda like "oh snap" wise.
C=

---

### Post by AROtotheN on 2009-09-16
Reaper!!! Wow man!! Your first post and you drop that?!~?!

AWESOME!!

Now I have a functioning Blender Launcher on my Cairo-Dock.

Many thanks!!

Aaron

---

### Post by nocentis on 2009-09-16
I was looking for this everywhere, thanks for the help :P

---

### Post by phanichalla on 2010-03-16
Thanks a lot.
:popcorn:

---

