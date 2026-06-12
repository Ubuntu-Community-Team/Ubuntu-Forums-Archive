---
title: "Window Managers/Plugins and Mythfrontend"
date: 2007-11-20
forum: Mythbuntu
---

### Post by err_ok on 2007-11-20
Hi guys and gals,

I'm trying to get mythtv and compiz working together on my system, already you can use the widget layer as a kind of 'System Menu' to access the ccsm/mythbuntu control centre/terminal/system tray and various other applications/widgets. Also the cube is used as a nice menu switcher to move between plugins (currently the layout is mythfrontend/mythvideo/mythmusic/mythnews). However this is where i ran into problems.

Does the mythfrontend override the window manager when it comes to placement?

I would like to have mythfrontend start on a different workspace and i'm having trouble while using them Place plugin in the Git version of Compiz Fusion, it works fine with other programs just not myth. Is there anyway to give compiz priority or set it to run on different workspaces?

Aaand another question; loading up standalone myth plugins is a useful feature but is there anyway to implement a confirmation on exit thing similar to the mythfrontend.

Any help would be great! Thanks for your time!

X posted: MythTVtalk.com

---

### Post by foxbuntu on 2007-11-20
As far as I know, Mythfrontend starts on the default desktop or workspace. However it can be moved, but I'm not sure it will work on the cube due to the way it renders its pages and text on the fly.

Im not sure where you would like a confirm on exit for your second question. Please provide more detail.

---

### Post by superm1 on 2007-11-20
Something to keep in mind is that typically compiz has an override option for "fullscreen" applications by default.  If you want to be moving it around and have it composited you will have to install compizconfig-settings-manager and uncheck that option.

---

### Post by err_ok on 2007-11-20
i haev the ccsm installed and have also have tried using the fullscreen overide it doesn't seem to work. I was reading on the compiz forum that certain programs like amarok take priority over compiz in certain areas i.e. window placement could this be the case with the mythfrontend do you think there would be a way around it if it was.

> Im not sure where you would like a confirm on exit for your second question. Please provide more detail.

You can run an invidual plugin using; 'mythfrontend <plugin>' however when you press esc it quits to the desktop without a prompt or anything. Do you think you can get a prompt similar to that on the main frontend?

For example: if you make a symlink to 'mythfrontend.real' called a plugin name i.e. mythvideo then it changes the title to mythvideo instead of mythfrontend.real. Which i'm using to get it to play in compiz. Could this symlink also enable the prompt or something or would that take a bit of coding.

---

