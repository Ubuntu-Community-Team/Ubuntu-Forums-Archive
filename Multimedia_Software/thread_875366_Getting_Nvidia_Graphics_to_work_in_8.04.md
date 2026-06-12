---
title: "Getting Nvidia Graphics to work in 8.04"
date: 2008-07-30
forum: Multimedia Software
---

### Post by farlander762 on 2008-07-30
I have two computers both running Ubuntu 8.04.  Below is what I did to make the graphics work properly.  The procedure was virtually the same for each machine.  I hope this helps someone in need.  It looks worse than it is.

Machine 1:
GeForce 4, 128MB, dual monitor

Machine 2:
GeForce FX 5200, 128MB, single monitor, 3D

Staring with a fresh install:

1.  Install Ubuntu (really...you must do this).

2.  **Do not** click on the Restricted Drivers balloon that pops up.

3.  Either wait on the Update Manager to tell you that you need to do 215 updates (literal number) or go *System - Administration - Update Manager* and get the updates started.  You don't want to miss out on the possibility of an updated driver.

4.  Once all of the updates are done go *System - Administration - Restricted Drivers * and enable the Nvidia (glx) driver.  It will ask you to reboot, ignore that for now.

5.  Go *System - Administration - Synaptic Package Manager* and click *Search*.  Run a search for **Nvidia**.  

6.  When the search completes look for **nvidia-settings** and mark it for installation.

7.  Click *Apply*.

8.  Once Synaptic gets finished, close it and whatever game you were playing and reboot the confuser.

9.  Once you get Ubuntu back up, if you have two monitors one of them will likely be off.  No worries.  Log into Ubuntu as normal and go *System - Administration - NVIDIA X Server Settings*.  (I can't tell you how many times I have almost started these instructions with "*Start*".)  

10.  Inside this window click *X Server Display Configuration*.

11.  Somewhere about this point if you are using two monitors it should ask if you want the second monitor set for *Disable*, *Separate X Screen*, or *TwinView*.  More than likely *Twinview* is what you want.  If I remember correctly, the program popped up a box asking which I wanted, if it doesn't you can select the mode where it says *Configuration*.  

12.  Now set the resolution and refresh rate you want for each monitor.  The monitor you are adjusting is selected in the *Layout* box.

13.  Here's where it gets tricky.  The permissions settings will not let you do this the easy way (it didn't let me anyway).  Click on *Save to X Configuration File.*

14.  Open a terminal window by going to *Applications - Accessories - Terminal*.

15.  Type (case is very important in Linux)
```
sudo gedit /etc/X11/xorg.conf
```
Type in your password and a text editor will open.

16.  Go back to the **Save X Configuration** box.  Make sure that **Merge with existing file** box is checked and click *Show preview...*.

17.  Highlight the entire text of the box and press *Ctrl + C* (copy).  

18.  Go to the text editor window and highlight the entire text.  Press *Ctrl + V* (paste).  

19.  Click *Save*.

20.  Close the text editor and quit the **NVIDIA X Server Settings** program (and anything else that may be open).  

21.  Reboot.

22.  If everything went properly it should work correctly now.  Enjoy.  If it doesn't, you shouldn't have been heeding my advise.  This is my seventh post!!


:)

---

