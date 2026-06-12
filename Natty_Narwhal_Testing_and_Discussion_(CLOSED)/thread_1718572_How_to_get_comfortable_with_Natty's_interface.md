---
title: "How to get comfortable with Natty's interface"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by julianb on 2011-03-31
What do you use to switch from one window to another? Is there a way that makes it seem like a comfortable experience?

Here are the methods I'm accustomed to: using the dock (osx), only works when there are not multiple windows of the same application; "squeezing" the side buttons on the mouse (osx)

using the panel (windows XP, ubuntu 10.10).

On Natty i am using "alt-tab" but I wonder if there are good strategies I don't know about.

Alt-tab is the ONLY way I know of to pull up minimized windows in Natty - is there another way?

When I want an extra terminal windows, the only way I have found to do that is to click the top left "menu" button, type "terminal" and press enter; is there another way?

---

### Post by terry_gardener on 2011-03-31
to open a new instance/window of a program. middle click the icon for the program in the launcher. 

reopen minimised windows.
click the app icon in the launcher and the last window for that app will open. 
if you have multiple windows open for the same app press the icon twice and you will get a scale affect for the windows. 

the triangles on the left side of the app icon in the launcher represents the number of windows for that app is open.

---

### Post by teh603 on 2011-03-31
You could just try Kubuntu. Same Ubuntu, with a traditional look and feel instead of... well, you get the idea.

---

### Post by kansasnoob on 2011-03-31
IMHO go at it slowly and with the greatest amount of patience :D

Ubuntu made it quite easy to take this a step at a time. If Unity seems overwhelming just Alt>SysReq>K and select either classic or classic w/o effects.

If the global menu messes with your head look here:

[http://ubuntuforums.org/showthread.php?p=10613605#post10613605](http://ubuntuforums.org/showthread.php?p=10613605#post10613605)

Basically take it one bite at a time and if you can't stand anymore restart gdm and select a UI you're familiar with :D

---

### Post by r-senior on 2011-03-31
> **julianb said:**
> What do you use to switch from one window to another? Is there a way that makes it seem like a comfortable experience?
Just click on the icon in the launcher or, if the window is visible, click inside it.

I prefer to leave the launcher always visible (see Unity Plugin in Compiz Config Settings Manager) but that's more about maximising windows and shouldn't make a whole lot of difference to switching.

Perhaps have a look at the Compiz Config Settings Manager and see what the key bindings are, especially for the following plugins: Scale, Static Application Switcher and, if you switch workspaces a lot, Desktop Wall.

---

### Post by enochpc on 2011-03-31
One option I found to help with the transition is to install AWN and install the Menu widget.  You can use the Unity interface and if you get frustrated, you can easily access the old style menu without leaving Unity.  Has helped me decide to give Unity a try anyway.

---

### Post by stanz on 2011-03-31
> **kansasnoob said:**
> Alt>SysReq>K and select either classic or classic w/o effects. :D

That option should be in 'keyboard shortcuts'?
I'll look, cause my dell laptop don't have a 'SysReq' key!
:guitar:

---

### Post by kansasnoob on 2011-03-31
> **stanz said:**
> That option should be in 'keyboard shortcuts'?
I'll look, cause my dell laptop don't have a 'SysReq' key!
:guitar:

Same as print screen. There are other ways to restart X or get back to gdm.

Once booted you can go to Preferernces > Keyboard and set things so Crtl>Alt>Backspace will restart X.

---

### Post by mc4man on 2011-03-31
> **stanz said:**
> That option should be in 'keyboard shortcuts'?
I'll look, cause my dell laptop don't have a 'SysReq' key!
:guitar:
You'd only need a keyboard shortcut if compiz/unity froze, otherwise how about just a simple power button > log out 
(or when you boot up just choose Classic at login screen

> SysReq' key!
Your 'print' or Prnt Scrn or however it's termed
(you can also enable the Ctrl+Alt+Backspace to kill X in Keyboard > Layouts > Options

---

### Post by kansasnoob on 2011-03-31
I actually had to look, but if power button still appears in the upper right hand corner just click on it and select logout. that should drop you back at the login screen.

---

### Post by julianb on 2011-04-01
I am using natty on a netbook with 9 inch screen so i LIKE that the UI has changed to be more small-screen-friendly. I appreciate the tips because i never would have known about "click twice on the icon you want on Unity's left bar to switch windows", nor "middle click on the icon you want on Unity's left bar to open a new window". 

(on my machine, you have to press both mouse buttons at once to simulate a middle-click). 

There are going to be a LOT of people either frustrated, or asking questions about how to use this UI. It's more like OSX than it has ever been before, but still different enough to confuse me. 

It seems like ubuntu has been most successful as a desktop/laptop OS and the motivation for change was that the old UI wasn't ideal for netbooks and tablets. Hopefully Ubuntu can pick up new netbook/tablet users without alienating the current users.

---

### Post by cubeist on 2011-04-01
> **julianb said:**
> I am using natty on a netbook with 9 inch screen so i LIKE that the UI has changed to be more small-screen-friendly. I appreciate the tips because i never would have known about "click twice on the icon you want on Unity's left bar to switch windows", nor "middle click on the icon you want on Unity's left bar to open a new window". 

(on my machine, you have to press both mouse buttons at once to simulate a middle-click). 

There are going to be a LOT of people either frustrated, or asking questions about how to use this UI. It's more like OSX than it has ever been before, but still different enough to confuse me. 

It seems like ubuntu has been most successful as a desktop/laptop OS and the motivation for change was that the old UI wasn't ideal for netbooks and tablets. Hopefully Ubuntu can pick up new netbook/tablet users without alienating the current users.

I'm also using natty on a netbook (10") and I love the interface. It's the first linux I have installed that is perfect out of the box.

One thing that I changed for netbook use is to make all windows open full screen.  In CCSM, under the place windows tab, select open full screen.

Also if you click "Super, tab" all the icons in the launcher will light up with a number/letter you can press to switch windows. Very slick.

Correction
Under the window rules, in the category "Maximized" enter the value "class="
Under place windows, select Placement Mode to Maximize

---

### Post by stanz on 2011-04-01
> **mc4man said:**
> You'd only need a keyboard shortcut if compiz/unity froze, otherwise how about just a simple power button > log out 
(or when you boot up just choose Classic at login screen


Your 'print' or Prnt Scrn or however it's termed
(you can also enable the Ctrl+Alt+Backspace to kill X in Keyboard > Layouts > Options

This dell has the Prnt Scrn. I've looked into this abit-and find when compiz/unity freezes up or whatever--I loose keyboard shortcut capabilities.
But...this is just a dell...
:)

---

### Post by julianb on 2011-04-01
so far no success with compizconfig-settings-manager ...

i had to  look up online just to find out what ccsm stood for :)

---

### Post by VinDSL on 2011-04-01
> **r-senior said:**
> I prefer to leave the launcher always visible (see Unity Plugin in Compiz Config Settings Manager)[...]
Heh!  Thank you!

I keep telling ppl...

This is the single biggest thing you can do to "get comfortable with Natty's interface", e.g. NEVER hide the launcher.

I also turn off the backlight, make the icons as small as possible, and enable MT Grab Handles.

The frames on windows are very small these days, especially on "light" themes.

MT Grab Handles makes resizing windows uber easy!

To save some clicking, go directly to the Unity Plugin using CLI...

```

~$ ccsm -c UNITY

```

This brings up the Unity Plugin in CCSM.

Here are some visuals, of what I change...  ;)


[INDENT][IMG]http://vindsl.com/images/unity-behaviour.png[/IMG]


[IMG]http://vindsl.com/images/unity-experimental.png[/IMG][/INDENT]


[IMG]http://vindsl.com/images/unity-mt-grab-handles.png[/IMG]



Here are the changes, in action...



[INDENT]**Ubuntu 11.04 / Conky 1.8.0 / Lua / Unity / Metric Weather Stats** (Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-1-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-apr-2011.png")[/INDENT]



Anyway, those are the biggies!

I change a few other small things, but Unity is rather brittle right now, and easily broken.

Soooo, let's just leave it at that...  :D

---

### Post by teachop on 2011-04-01
> **VinDSL said:**
> 
Here are some visuals, of what I change...  ;)

Thanks for this post, it really helps.  Some of these should be considered for default settings!

---

### Post by davepoth on 2011-04-01
I switched back to Ubuntu Classic straight away. I'm running a netbook, and the new interface seems to get in the way to me. It's quite underpowered anyway, so having all of this extra guff perched on top of Gnome made it quite laggy. I just hide the top and bottom panels and that gives me 1024 x 598 to work with. If it ain't broke and all that.

---

