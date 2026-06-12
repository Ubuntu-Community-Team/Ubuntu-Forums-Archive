---
title: "How to shut down the frontend?"
date: 2009-03-08
forum: Mythbuntu
---

### Post by Last_911 on 2009-03-08
Okay, so it will be abundantly clear how big a noob I am as soon as I ask this question:

How do I shut down the frontend so the display will go back to my computer monitor instead of the TV?

As soon as I start up the computer (running Mythbuntu 8.10) the video output is sent to the TV, not the PC monitor. I don't have my remote up and working yet and the TV is in the living room so I can't very easily run anything from the TV screen when my keyboard and mouse are in my office.

I've searched the forums, to no avail, but I'm sure the answer is out there...

Thanks for helping out this beginner.

---

### Post by mookie60 on 2009-03-09
Fellow noob,

I haven't gotten mine running yet, but after having been through the setup stuff a lot lately I did notice the following section that may be what you're looking for:

applications>system>mythbuntu control center (MCC)

from within the MCC select "System Roles" and near the bottom of the page is a section titled "Desktop Role".   

I'm not sure how it might work from there on out, but it seems to relate to your question.

---

### Post by 4dognight on 2009-03-09
I think what your after is to have Myth frontend running on your TV, and still be able to use your PC from the monitor. If you set up your video card to run with a second screen, you can achieve this. If its a nvidia card go into the nvidia settings and configure it there.

---

### Post by Last_911 on 2009-03-09
Thanks 4dog . . .
 
It's very awkward trying to operate using the keyboard and mouse in the office and the TV in the living room (lots of walking and yelling!). How can I get the display to remain (or return) to the PC monitor after the frontend is running? As soon as I boot up, the display goes directly to the TV and I don't know how to get it back to the PC (or if this is even possible). Is there a way to get back to a terminal or Gnome or something on the PC?
 
Thanks for your help!

---

### Post by 4dognight on 2009-03-09
Is your video card an Nvidia?

---

### Post by Last_911 on 2009-03-09
Yes. I'm sorry, I should have mentioned that.  It's an GEForce5200FX (I think that's right!).

---

### Post by 4dognight on 2009-03-10
You want to set up twinview in your nvidia settings. You can access it either from the MCC, or the menu under system. 

This way you will have 2 separate X screens. One is your PC and the other your TV. You start mythtv frontend on the TV and then you also have your normal desktop on the pc monitor at the same time. 

You can then leave the frontend up and running and still have a desktop.

There is lots of how to out there. search for twinview and mythtv, should produce lots of hits.

---

### Post by newlinux on 2009-03-10
I have a similar setup (computer connected to TV via S-video and a CRT monitor via VGA at the same time with nvidia card). I have it using both monitors without twinview/xinerama - instead I just have two X displays. You can set this up using nvidia-settings (install it if it isn't and then run it with sudo). If you choose to go with twinview/xinerama you can set that up there too. I found that when setting them up  with nvidia-settings the settings didn't stick between reboots. I ended up having nvidia-settings overwrite my xorg.conf and then the settings stuck between boots.

Some background below... (but there are probably better how-tos).


[http://www.mythtv.org/wiki/Running_MythTV_Dual_Headed](http://www.mythtv.org/wiki/Running_MythTV_Dual_Headed)

---

### Post by Last_911 on 2009-03-11
Thanks for all your help, folks. I'm not sure I've got 'twinview' in my nVidia driver, but I could be an idiot...I'm using the nVidia propietary driver 173, as recommended by Mythbuntu during setup. If I go to the nVidia setup menu, there's a button to 'Detect Displays' (or something like that), but it only detects the TV, not the PC monitor. Without another display device, I don't see how I can set up dual displays.
 
All I want to do is have the output of Myth go to both my TV _and_ my PC monitor. (I only use the PC for Myth.)
 
Oh well, I'll keep searching and maybe I'll find the answer.
 
Google is my friend!
 
Thanks!

---

### Post by mathog on 2009-03-11
> **Last_911 said:**
> 
 
All I want to do is have the output of Myth go to both my TV _and_ my PC monitor. (I only use the PC for Myth.)
 

I think you may have problems with "focus".  

My system has X11 configured with two screens: screen 0 is the monitor and screen 1 is TV-OUT.  (Search in this forum, somewhere or other I posted the xorg.conf recently).  Normally TV-OUT is run entirely with a remote control via lirc, and the monitor isn't used for anything.  The problem is, if I do use the monitor, for instance, open an xterm, that will shift the X11 server's focus from the myth window to the xterm window, and those are on different screens.  After that lirc (IR remote) events may not be delivered to mythtv since the focus is on screen 0, but myth is running on screen 1.  Keyboard events are definitely not delivered, they naturally go to the xterm.

You want to have the same video image appear on both screens?  I think that may be possible if you set up twinview, which gives you two screens, but they show the same thing in the overlap region.

If you want to be able to watch two different things at the same time by having a mythfrontend on screen 0, and a separate mythfrontend on screen 1, well, good luck with that.  I'm pretty sure you will get lirc events intended for the TV screen instead delivered to the Monitor screen when the focus is on it.  Either that or lirc will deliver to both mythfrontends (it works by name, and they have the same name).  Also, if you use VDPAU it only does one stream at a time, and the two frontends would probably fight over who controls it.

---

