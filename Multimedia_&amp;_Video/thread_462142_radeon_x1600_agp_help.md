---
title: "radeon x1600 agp help"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by wlc3069 on 2007-06-02
I just recently made the switch from xp, to vista and i hated the way vista slowed down my machine. It used so much of my system to idle that it would run a lot hotter than it used to. So instead of reinstalling xp i thought i would give linux a try. So i surfed the web and it seemed that Ubuntu had the largest community behind it so i gave it a try.
Now that you know my situation, let me tell you about the problem. Well I decided to run Ubuntu Studio, and everything installed beautifully and my machine is running faster than ever, besides my video card. At first i had no OpenGL support so i followed a few threads in the forum and i got things working.
glxinfo | grep rendering shows that direct rendering is enabled, so i thought that 3d rendering was enabled, but when i go to start a 3d application or game it will either crash or display a error message that reads "Unable to Enable 3d Mode-Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings."
What does this mean, and what can i do to solve the problem?
I really love Ubuntu, and i'd love to keep it, but without the use of 3d apps and games i don't know that i could.
Thanks for reading and for any help that anyone may have, it's very much appreciated! :)

---

### Post by benx009 on 2007-07-15
well, what 3d game r u trying to run?  i think u were probably trying to run a 3D game of glchess, in which case, it would show that error anyways regardless of whether u have 3D acceleration or not.  to fix that problem, you can download and install the python-opengl package from synaptic, and the [python-gtkglext package]("http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437") from sourceforge.

to simply test whether or not 3D acc. is running or not, just do "glxgears" (w/o the quotes) in a terminal.  if u see the gears spinning w/o glitches, and u have decent FPS's, then ur 3D acc. is fine.

---

