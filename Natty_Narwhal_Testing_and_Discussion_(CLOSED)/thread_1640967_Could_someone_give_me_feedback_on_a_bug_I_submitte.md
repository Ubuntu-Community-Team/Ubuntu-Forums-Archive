---
title: "Could someone give me feedback on a bug I submitted?"
date: 2010-12-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by simpleblue on 2010-12-08
I've submitted a bug and I wanted some feedback on what I can improve on. I did search for an identical bug but I am not sure how to just search within 11.04 bugs and not all of the Ubuntu versions at once.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/687466](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/687466)

Thanks. I just want to give a little back if I can so if someone could give me some resources and some tips it would be greatly appreciated.


Also, I find that many links did not help me in 11.04 as much of the info seems inapplicable:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Pressing Alt-F2 does not work. To access you must goto terminal and type "ubuntu-bug"


And "Finding the right package" ([https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage)) uses the menu system to find out what is causing the bug, and the menu system is not in this version.

---

### Post by efflandt on 2010-12-08
If I close the calculator or other program by closing the window with window controls (X), instead of Quit in icon right click, I do not have that issue unpining the Unity icon.

If I follow the procedure you outline in the bug report, true, the next time you open the calculator, there is no Unity icon for it.  But if you then close the calculator (X) and restart it, the Unity icon reappears and everything is back to normal.

So that is a relatively minor issue at this point of development, because most people probably close a window by clicking on the (X) in the window (which works fine) instead of taking more mouse clicks to right click the Unity icon and Quit from there.  But it is something to look at when they have time.

It was not too long ago that "Pin to Laucher" did not exist, and sometime between then and now when I was playing with "Pin to Launcher" all my panels disappeared.  Although, a simple **sudo restart gdm** from console got everything back to normal after that happened.  So things are progressing.

---

### Post by simpleblue on 2010-12-08
> **efflandt said:**
> ... a relatively minor issue at this point of development, because most people probably close a window by clicking on the (X) in the window (which works fine) instead of taking more mouse clicks to right click the Unity icon and Quit from there.  But it is something to look at when they have time.
I agree that it's not a big issue at this point. Though I do think that it can be a bothersome issue, especially to a person who does not know what sequence of actions is causing it. So I think that it's a good idea to file this for future reference.

---

