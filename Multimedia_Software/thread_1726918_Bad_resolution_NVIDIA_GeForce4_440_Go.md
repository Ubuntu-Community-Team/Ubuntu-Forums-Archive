---
title: "Bad resolution NVIDIA GeForce4 440 Go"
date: 2011-04-11
forum: Multimedia Software
---

### Post by Gageat on 2011-04-11
First of all, hi everyone. This is my first post here, so I thought I could say hi first.

Well, at the matter at hand. I Have a Dell Inspiron 8200 (Yeah, an old computer, but it's the only one I have) with Xubuntu 10.10 installed on it, since it's the best destro for me.

I noticed that installing my Video card driver caused my computer to show a black screen when I turned it on, so I searched a lot of fixes here and in other forums, and the one that worked for me was this one: [http://www.nvnews.net/vbulletin/showpost.php?p=1068062&postcount=26](http://www.nvnews.net/vbulletin/showpost.php?p=1068062&postcount=26) (if posting these links is not accepted please remove it) and finally! my video card was able to use OpenGL... but... that fix was meant for a resolution of 1600x1200... and I have a resolution of 1400x1050, and right now those 200x150 pixels of difference don't appear, they go out of the screen (sorry if it is difficult to understand, I'm still training my English). I Tried Hex Editing the EDID, but I can't figure it out how to find the resolution values. 

Everyone seems to have a resolution of 1600x1200, I can't find any fixes for it

EDIT: Well, if no one can fix this, then another question; Does anyone know  how can I open and edit the file on the link i posted above? that would  greatly help, though, I doubt I can fix it immediately.

Yes, I have spent 5 hours trying to find the solution, and right now I'm just ONE step ahead of reaching it... please helpe me! :(

---

### Post by Gageat on 2011-04-11
Well, nevermind, after an hour working I finally worked it out. I'm posting the fix if someone needs it (altough I doubt it) it was a problem with the xorg.conf, specifically, with the Screen Identifier;

I Uninstalled the Driver, then Installed the one from "Additional Drivers". But this time I didn't downloaded nor used that fix I posted on the link before.
The normal code that comes with the driver has one problem (sorry, i forgot to make a backup, but i'll try to be as clear as posible): in the Section "Screen", the identifier appears as "Default Screen" (i think). You only have to erase the whole text, and replace it with what I have here.

> 
Section "Screen"
         Identifier    "Videocard0"
         DefaultDepth    24
         Option    "AddARGBGLXVisuals"    "True"
         Option      "UseDisplayDevice" "DFP-0"
EndSection

Section "Module"
         Load    "glx"
EndSection

Section "Device"
         Identifier    "Videocard0"
         Driver    "nvidia"
         Option    "NoLogo"    "True"
EndSectionApparently, having "Default Screen" tries to activate the screen "without" the driver, so putting Videocard0 fixes it.

I think it can be used to fix some other problems like this. To think I spent 7 hours trying to fix this, just to know that the solution was the first thing I thought about.

---

### Post by Bill Grabowski on 2011-12-24
Gageat,

Thank you VERY much for finding the solution to the problem of the blank screen after reboot and after installing the proprietary nVidia drivers for the NVIDIA GeForce4 440 Go on my old Dell Inspiron 8200 with XUGA in 1600x1200 mode, running Ubuntu 10.04 LTS. Your changes to xorg.conf that appeared after the drivers were installed did the trick, and I salute you for persistence and inspired problem solving. It sure helped me.

Bill

---

