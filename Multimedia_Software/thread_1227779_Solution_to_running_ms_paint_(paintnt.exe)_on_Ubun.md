---
title: "Solution to running ms paint (paintnt.exe) on Ubuntu 8.04 Hardy Heron (32bit)"
date: 2009-07-31
forum: Multimedia Software
---

### Post by jmwilli25 on 2009-07-31
This solution may already be posted somewhere, but I couldn't find it. I pieced together my solution from others, did a complete reinstall of mspaint, and was very detailed in my explanations.

Solution to running ms paint (paintnt.exe) on Ubuntu 8.04 Hardy Heron (32bit).

Get wine, first open a terminal and type

     sudo apt-get install wine

Reboot computer

Download mspaint [here]("http://download.microsoft.com/download/winntwks40/paint/1/nt4/en-us/paintnt.exe") <---click this
After downloaded move the paintnt.exe file from it's current location 
to the desktop, this is only for convenience and is not required.

Now download the necessary .dll [here]("http://www.dll-files.com/dllindex/mfc42u.zip?0VGlXAYMiP") <---click this
The .dll necessary is currently in the mfc42u.zip you just downloaded 
so you need to right-click mfc42u.zip and select "Extract Here". Then move the extracted folder, mfc42u, to the desktop.

Now click Applications on your panel and mouse-over Wine and then click 
"Browse C:\ Drive". A file browser window will open. Two folders should
be present, "Program Files" and "windows". Doulbe-click "windows" and this
is where you need to put your newly downloaded files.

First drop and drag the paintnt.exe file from your desktop to this folder. Now go back to your desktop and open the mfc42u folder to find, "mfc42u.dll" and "readme.txt" just ignore the readme file. Now drop and drag the mfc42u.dll file to the same place as the paintnt.exe .

Open a terminal and type

     sudo sysctl -w vm.mmap_min_addr=0

     sudo wine paintnt.exe

     sudo wine MSPAINT.EXE

NOTE: MSPAINT.EXE is intentionally in capitals.

mspaint is now working on your computer.

Addendum: To make a shortcut right-click on your top panel then click "Add to Panel..." Now double-click "Custom Application launcher". Name it what you want, then in the command line type

     sudo wine MSPAINT.EXE

Finally click on the icon that looks like a spring under a board. Choose an icon. Click okay, then okay again. And voila! You have just installed mspaint on your computer and created a shortcut.

---

### Post by vinutux on 2009-07-31
Wow...goooood.....But who want the [COLOR="Red"]craps[/COLOR] like mspaint ?

---

### Post by Grenage on 2009-07-31
Seriously, you *want* to use mspaint?

---

### Post by jmwilli25 on 2009-08-08
> **Grenage said:**
> Seriously, you *want* to use mspaint?

There are some of us out there that are familiar with the program and enjoy it's simplicity. Like I have read many places, there are plenty of other open source solutions to needing mspaint, but that is no reason not to post a guide to obtain mspaint. I would much rather have someone attempt the installation and tell me if there were any problems rather than question it's validity. Thanks for the constructive input though...

---

### Post by Tek-E on 2009-08-08
lol mspaint?? :popcorn:
I suppose its a personal choice but gimp is so much better and far more advanced than mspaint in my opinion.

---

### Post by Neon Lemmy Koopa on 2009-08-09
Gimp is indeed advanced but if you do things like design games or so, ms paint is convenient for designing sprites and small scale graphics.  Advanced is good, but so is simple.

This is only my opinion.

---

### Post by digitalsp on 2009-08-09
:lolflag: I remember that app since Windows 1.0 - I still wake up some nights screaming no no no

---

### Post by Tek-E on 2009-08-11
> **Neon Lemmy Koopa said:**
> Gimp is indeed advanced but if you do things like design games or so, ms paint is convenient for designing sprites and small scale graphics.  Advanced is good, but so is simple.

This is only my opinion.

I can definatley agree with that.  I have seen some people make some rather neat sprites using mspaint.

---

