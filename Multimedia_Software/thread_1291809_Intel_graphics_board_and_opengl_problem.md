---
title: "Intel graphics board and opengl problem"
date: 2009-10-15
forum: Multimedia Software
---

### Post by tenshikun12 on 2009-10-15
Dear sir or madam,

I recently installed Ubuntu Jaunty Jackalope and have the intention to use it for my job and possibly get rid of windows as soon as I can.

However, I use a program called Visual Molecular Dynamics (VMD), which needs OpenGL to run a 3D display of molecules. This gives me two problems:

[LIST]
[*]The first one is that, if I have Composite enabled, the OpenGL window does not show properly, it blinks, turns invisible and does not show the title bar (although it is there, since I can maximize and minimize the window clicking on the blank space where these buttons should be.

This problem can be solved by disabling Composite (I read my solution from [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Disable_Composite_Extension):](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Disable_Composite_Extension):)

Simply edit the /etc/X11/xorg.conf with your preferred editor and root privileges, and add these lines at the bottom:

```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```

Then reboot (or log out and then back in, but preferably reboot) and the problem is solved.

[*]My other problem, however, happens both with Composite enabled and disabled: VMD seems unable to quit.

The fact is, I open VMD from the console, and this launches two windows (as expected): the main window where you control the visualizations, and the OpenGL display, which although doesn't blink any more and has a title bar (disabling Composite), doesn't show the best of its quality in the images. Furthermore, I can still write commands in the console.

If I then try to quit the program, either by writing "quit" in the console, or by closing the main window, only the main window closes, but both the console and the OpenGL keep open. I have to kill the process in order to close it.
[/LIST]

I contacted VMD and they told me this might be a problem of my Intel 965M graphics chipset, and I indeed found a lot of posts in this forum on that, but they all seem to finally succeed. I have tried all those methods and had no luck whatsoever.

If any of you has had similar problems, or knows any solution to the problem, it would be real help since I am completely lost.

Thank you very much in advance.

Angel

PS: I'm attaching the output in the console of the VMD with composite enabled (if it's disabled, it simply does not write the Warning). Although I write vmd > output_VMD.txt, the output console prints two messages before the attachment:

```
[: 338: i686: unexpected operator
[: 338: i686: unexpected operator
```

---

