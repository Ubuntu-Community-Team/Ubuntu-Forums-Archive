---
title: "Cloning selected application windows on dual screen setup"
date: 2011-06-06
forum: Multimedia Software
---

### Post by DrPotoroo on 2011-06-06
I often have situations where I am doing a presentation from my netbook and want to have some things visible on only my screen, some things visible only on an attached projector and some things visible on both. The thing I want visible on both could easily be any application window - for example a Libre office document or a terminal. If the projector screen is behind me I will want to be able to enter data into these windows and see what I'm doing by having that window cloned on my netbook screen. At other times during a presentation I might have Impress slides showing on the projector and be using separate speaking prompts on my netbook screen.
 
Does anyone know a way that individual windows can be cloned across displays, instead of cloning the entire display? I know of options to clone a window across workspaces, but haven't found a way to do it across displays. Can it be done?

---

### Post by DrPotoroo on 2011-06-07
Well, answering my own question it appears the closest one can get is to use the compiz clone output plugin. [http://forum.compiz.org/viewtopic.php?t=123&f=114](http://forum.compiz.org/viewtopic.php?t=123&f=114) gives a run-down on how compiz can be configured to break a single display into multiple "virtual" displays. (Hint: where the above link refers to things like /apps/compiz/general/screen0/options/... just look for a corresponding option in the CompizConfig Settings Manager (ccsm from a terminal). Doing this can allow you to test how the compiz clone plugin works when you don't have a second display on hand.

The plugin doesn't quite do what I want. It basically allows you to use shortcut keys (shift + win key + left mouse click by default) that lets you drag one display onto another to clone the whole display. You can then drag the cloned display back to the original to return to having separate displays. So while I can't clone just one window, it is an easier solution to my problem than laboriously going through the monitor settings when I want to switch to a cloned display.

Dragging a display onto another display with different resolution scales the source display to fill the target display. Not ideal, but it will do.

I've attached some screenshots showing a single display broken into three virtual displays. One screenshot shows the three virtual displays with independent content, the other shows the top left display cloned onto the wide bottom display - demonstrating how the image gets stretched.

---

### Post by DrPotoroo on 2011-06-10
Having tested the compiz clone output plugin now with my netbook (Lenovo S10e) now I have discovered this isn't going to work because multi displays+compiz with my system in Natty is SLOOOWWW. I also have the problem that the screen isn't drawing properly. For example, if I drag a window around the background fills up with images of the window. Sometimes the background fills with garbage, and sometimes window elements don't appear at all.

Turning off effects the system runs nicely - but I can't use compiz without effects can I?

If anyone has any tips to tweak performance I would greatly appreciate it.

---

### Post by DrPotoroo on 2011-06-13
Okay, now I feel silly. Firstly because I keep replying to my own thread; secondly because I was all set to roll back to Lucid on my netbook (where I thought I'd had better dual screen performance in the past) before I remembered I'd had similar problems on Lucid before.

In case anyone out there is having a similar problem with performance when working between two monitors, maybe this could help you, too. I eventually discovered with my Lenovo S10e that whenever you arrange monitors side-by-side in the Monitor Preferences tool the system will run VERY slowly, screens won't draw properly and programs like mplayer will sometimes fail to work at all.

In contrast, arranging my external display in Monitor Preferences so it is placed *above* the built-in display gave me very good performance. I had discovered this in Lucid, but then since above/below was the usual physical arrangement I was working with while using Lucid I forgot about this after upgrading to Natty, and then it so happened I wanted to use a side-by-side arrangement.

---

