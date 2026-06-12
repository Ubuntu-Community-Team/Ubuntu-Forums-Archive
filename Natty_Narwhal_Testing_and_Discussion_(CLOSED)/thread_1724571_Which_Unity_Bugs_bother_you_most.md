---
title: "Which Unity Bugs bother you most?"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Bazon on 2011-04-08
As [the classic gnome-panel desktop will be dropped in 11.10](http://www.omgubuntu.co.uk/?p=12299), it becomes increasing important to give the developers feedback where the community suffers most under unity.

I know, the forum here is not the place for feedback, but launchpad is! *("affects me", comments, fixes...)* So maybe, this thread can be some kind of runway to link to the different issues that are still left. 
*(or maybe it dies soon or maybe it gets fused into the unity mega thread.... ;-) )*



So let's start:
For me, I don't like how workspace management has changed. In my opinion, when I'm on one workspace, I should not see anything going on on the other workspaces to avoid distraction and keep order.
These bugs break this:
[should be possible to display only the launchers on the current workspace](https://bugs.launchpad.net/unity/+bug/683170)
[Application icons should only display windows from the current workspace in the window spread](https://bugs.launchpad.net/unity/+bug/689733)

Further, it is now hard to select text document windows:
[very hard to distinguish/select text documents in the expose window spread](https://bugs.launchpad.net/unity/+bug/734253)

Also, [I lose Firefox-Globalmenu very often](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/752684).

And finally for now, [it is not possible to paste something in the dash, neither by ctrl+c, nor by context-menu, nor by mousemiddleclick.](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/736222)

*(Speaking of context-menus: i really miss them in unity, although this is no special bug...)*

**which bugs bother you?**

---

### Post by marin123 on 2011-04-08
it would be nice to have multiple window management. for example when i have 2 or more firefox windows opened, i have to click the firefox icon and then it spreads all of the windows and i have to choose one. it would be better if i could right-click firefox and choose from window title.

and i would like to set downloads folder in launcher instead of home folder...

---

### Post by mc4man on 2011-04-08
> These bugs break this:
Application icons should only display windows from the current workspace in the window spread

The problem there is that the scale option/binding "Window Picker for Window Group" does pull from all workspaces, there is no "Window Picker for Window Group on Current Workspace Only" in the scale plugin.

Since this orig. came up there has been many  opportunities to clarify  what the intention was for the click (or 2nd click) on launcher icon, none has been forthcoming except for MS comment which has not be acted upon.
(quite the opposite actually

Personally I want the current way to stay, though if it's decided (later) to create a new action for the click on icon that's alright as long as the current scale -  "Window Picker for Window Group",  can be bound to something of the users choosing (atm you can't set a binding, it's taken by unity

---

### Post by tekstr1der on 2011-04-08
By far, my biggest pet peeve is the lack of ability for a unity launcher icon to minimize its respective window.

Very often you'll want to take a quick glimpse at a minimized/hidden window, but then quickly return to your current window. In any other dock, the expected behavior is to click the minimized app's launcher to maximize/restore, then click it again to minimize.

Currently, the Unity launchers will maximize/restore a window, but clicking again does nothing. It then becomes necessary/frustrating/distracting to have to hunt down the minimize button on the title bar or in the global menu and click that.

There's a bug on this issue:

[https://bugs.launchpad.net/ayatana-design/+bug/733349](https://bugs.launchpad.net/ayatana-design/+bug/733349)

but due to the fact that the behavior is "by design", it'll be a tough change to get through to Ayatana unfortunately.

---

### Post by r-senior on 2011-04-08
The ones where it crashes, locks up or windows don't display correctly. :(

The other stuff is just user-interface niggles that I would hope would be worked around with configuration options when that stage comes. I can live with all that for the time being, but basic reliability is critical and could make or break Unity IMO.

---

### Post by ikt on 2011-04-08
The one I'm just about to write a long blog post about.

---

### Post by VMC on 2011-04-08
> **r-senior said:**
> The ones where it crashes, locks up or windows don't display correctly. :(

The other stuff is just user-interface niggles that I would hope would be worked around with configuration options when that stage comes. I can live with all that for the time being, but basic reliability is critical and could make or break Unity IMO.

True for me as well. I have gotten use to the DE niggles. 
Recently, no crashes. Not to say I haven't tried to crash it - Right now its like a Timex...it keeps on ticking.

---

### Post by seeker5528 on 2011-04-08
> **tekstr1der said:**
> Currently, the Unity launchers will maximize/restore a window, but clicking again does nothing. It then becomes necessary/frustrating/distracting to have to hunt down the minimize button on the title bar or in the global menu and click that.

If you never run multiple instances on an application and never run MDI applicatiosn like Gimp, that sounds all well and good.

For me personally I like the current behavior, if you do have multiple windows of the same app, the window switching is consistent with the desktop switching and I like having a visual representation more than I like having a list. Having said that, I would also like like to see a list of windows when right clicking the launcher of an open application, the way Docky does it. 

Outside of that I would rather see the work in this area going into making the application launching and the window and desktop switching work together in a more integrated way. Which could perhaps resemble some of the following.  

After clicking on the workspace switcher, while viewing your desktops....

[list]Select a desktop and left or middle click a launcher icon to launch the application on the selected desktop.[/list]

[list]If left clicking the icon of an app that is already running, raise that apps windows on all desktops, with additional left clicks cycling through that applications windows if there are desktops where that application has more than one window.[/list]

[list]'Alt'+'Tab' to cycle the windows on the selected desktop.[/list]

As it is now when you click on 'Workspace Switcher', select a desktop, then click an application launcher icon, the results are not very consistent/predictable, in particular if after doing it once you select a different desktop and do it again and 'Alt'+'Tab' doesn't work at all. 

Later, Seeker

---

### Post by Starks on 2011-04-08
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/739068](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/739068)
"Cycling through app windows and apps themselves need improvement"

Nuff said.

---

### Post by mc4man on 2011-04-08
> 
As it is now when you click on 'Workspace Switcher', select a desktop, then click an application launcher icon, the results are not very consistent/predictable.

There was a short time when it seemed to open on highlighted ws. Now it will but the ws has to have a window already on it. (so apps are added to workspace w/ window focus not ws focus

As far as a bug I'm surprised is yet unfixed is nautilus appmenu on desktop focus,  the places dropdown is very useful if not using maxed windows

---

### Post by scottmuz on 2011-04-09
The desktop lockups. Had about 6 since I've upgraded a week ago.

---

### Post by elegant55 on 2011-04-09
I like the way the gnome-shell uses to manage the work space where the apps view show the open windows on current workspace.

Besides the launcher the apps view actually works as a task manager. Compared with classic task manager it requires some extra mouse travel but in exchanger gives user a glimpse of the contents inside the windows.

Compiz scale works similar but it can't show the windows which has been minimized.

---

### Post by Bazon on 2011-04-09
> **tekstr1der said:**
> By far, my biggest pet peeve is the lack of ability for a unity launcher icon to minimize its respective window.
(...)
There's a bug on this issue:

[https://bugs.launchpad.net/ayatana-design/+bug/733349](https://bugs.launchpad.net/ayatana-design/+bug/733349)
.

Oh yes, I hate that, too, "affected" + "subscribed".

I don't think user expects NOTHING to happen when he clicks anywhere, because he makes his clicks with purpose. + we are used to from gnome window switcher and varios linux docks.

although:
i tried that with an apple computer in a shop, and there, the behaviour is the same: nothing happens when you click on a launcher of an already launched application. an, on mac os, it is even worse: you can't even change the window with the dock icon, when you have 2 or more windows from the same application open. I really how apple users are supposed to do this "intuitive" (as it is always claimed mac os is). probably by moving windows that way, the desired window isn't covered any more. *(actually, i see mac users moving windows all the time, seems to be a mac os illness... ;-) )*

anyway, copying mac-behaviour is the wrong way IMHO.
apple dictates users what to do and how to do it, linux users like to decide on their own.

---

### Post by lucazade on 2011-04-09
Added and subscribed.. won't fix doesn't sound good.
An option in a future release would be nice.

---

### Post by bonfire89 on 2011-04-23
I wish I could somehow not have the global menu bar while using chrome.

---

### Post by r-senior on 2011-04-23
What happens if you edit the /usr/share/applications/chrome.desktop file and amend the exec line:

```
Exec=env UBUNTU_MENUPROXY=0 <application>
```

---

### Post by teachop on 2011-04-23
Horizontal overlay scroll controls leaving strange artifacts when I scroll in vertical direction.  Very annoying.

---

