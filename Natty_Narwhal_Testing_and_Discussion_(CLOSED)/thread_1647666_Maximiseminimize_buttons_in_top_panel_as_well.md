---
title: "Maximise/minimize buttons in top panel as well"
date: 2010-12-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-12-17
After today's updates I am now getting the desktop up and there are no entries in the top panel (except for the Ubuntu icon) until I mouse over the area, then the File, Edit menus appear.
What I am getting though is a copy of the top bar of an open window.
For example the max/min/close buttons and "Ubuntu Forums -Post New Thread - Mozilla Firefox" that appears at the top of a normal page is being repeated in the top panel.
So it all appears twice - but the File/Edit/View/Preferences etc are not there.

---

### Post by mc4man on 2010-12-17
I think that's intended, though I don't see any min, max,exit buttons in the top bar

It's telling you the name of the window that has focus, then a mouse over gives that windows menu options
(with the exception of some apps/windows where it's not yet implemented. - for instance synaptic, and at least here firefox, a few others I'm sure
(Desktop edition login

---

### Post by Quackers on 2010-12-17
If I am in UF for instance the top panel duplicates exactly the menu bar of UF, including the max/min/close buttons.
If I mouse over the top panel the UF title disappears but leaves the max/min/close buttons. The File/Edit etc headings never appear on mine until I close any open window.
Also the title from my last open window can still be present in the top panel while another window is open - even if the window for the old title is closed.

I can't take a screenshot because as soon as I open the screenshot program "Take Screenshot" appears in the top panel.

---

### Post by cariboo on 2010-12-17
Use the Grab current window setting in gnome-screenshot. See screenshot.

I haven't been able to figure out how to take a screenshot of the gnome-screenshot window yet. :)

**Edit**: Ooops I should have looked at the screenshot first.

---

### Post by Quackers on 2010-12-17
I tried that but it just shows "Take Screenshot" in the top panel :-(

---

### Post by terry_gardener on 2010-12-17
quackers 

i have same thing, think it is intended. 

see screenshot

---

### Post by mc4man on 2010-12-17
I see now about the min,max.close - that's only when in fullscreen

Otherwise  with multiple windows - when closing one, if returns focus to the previous in order of opening or to last opened in order
ie. 
open 1234, close 4, focus goes to 3
open 1234, close 2 focus goes to 4

Don't see any 'left over' titles in bar.

---

### Post by Quackers on 2010-12-17
mc4man I will investigate further :-)
terry_gardener, how did you get that screenshot! I can't do that :-)

Here's my attempt

---

### Post by mc4man on 2010-12-17
Here I don't get the doubled deal, when maximized all is sent to menu bar

(maybe because or true-hide.?, will try on laptop that has intelli-hide

Edit : no doubling with max. window with intelli-hide or disabled - all is sent to menu bar

> how did you get that screenshot
just hit the Prt Scr key

---

### Post by Quackers on 2010-12-17
mc4man you don't have a top bar in firefox?

---

### Post by terry_gardener on 2010-12-17
quackers 

the way i did the screen shot is i press the printscreen button on the keyboard.

---

### Post by Quackers on 2010-12-17
Thanks for that terry_gardener :-)
As some of my buttons don't work, and I don't have a printer I assumed print screen wouldn't do anything! What a dullard! :-)  Nice one!

---

### Post by mc4man on 2010-12-17
> mc4man you don't have a top bar in firefox?
you must excuse my ignorance in terminology - what's a top bar?

screen shows my 'normal' firefox, unmaximized

Also note - all maximized windows transfer fully to menu bar, even app windows not designed for natty - ie. amarok-1.4, ect

---

### Post by Quackers on 2010-12-17
mc4man, I'm sure it's my terminology that's awry :-)
What I mean is this. In your first screenshot in post #9 you have the File Menu etc which is the menu bar - as I understand it :-) - but above it you don't have another bar with the max/min/close buttons in it. Your top bar (??) shows the Ubuntu logo, which to me indicates that that is the top panel - not the top bar of the FF Window ( is that the border?)
In comparision here is my print screen screenshot

---

### Post by mc4man on 2010-12-17
What you're seeing in post 9 screen is the 'top bar' of fiefox (close,min,max 'location description') merged into the menu bar of unity.

That's why it's not doubled, though atm firefox menu items can't be accessed from the menu bar so they stay with firefox.
Why your's is doubling not sure, could propose a few idea's if it doesn't get right. 

Maybe these three screens can help show
screen 1 - vlc maximized, merged into menu bar
screen 2 vlc maximized, menu exposed in menubar
screen 3 - set vlc to keep it's menu items in the gui, maximized - compare screen 1 and 3

---

### Post by Quackers on 2010-12-17
I see. Thanks for that.
I am not getting that merging for some reason, as you point out.
Here are 2 screenshots with 2 open windows (not firefox) with gparted window active in the first one and ccsm active in the second.

---

### Post by cariboo on 2010-12-17
The merging as you call it only happens when an applications is running full screen

---

### Post by Quackers on 2010-12-17
Nice festive avatar cariboo907 :-)

I'm not getting that "merging" in full screen. I wonder if it's because my Unity side bar thing isn't hidden, so technically I'm not using the full screen?

---

### Post by mc4man on 2010-12-17
As cariboo907 has mentioned only in fullscreen, (don't know what else to call it, merged seems descriptive

Are you using the Classic login to run unity?

Anyway the compiz redo re-enabling the patch have shown up in main server, maybe update.

---

### Post by Quackers on 2010-12-17
> **mc4man said:**
> As cariboo907 has mentioned only in fullscreen, (don't know what else to call it, merged seems descriptive

Are you using the Classic login to run unity?

Anyway the compiz redo re-enabling the patch have shown up in main server, maybe update.

No further updates available for me yet.

It's set to autologin and Unity starts automatically. That's all I know :-)

---

### Post by Quackers on 2010-12-17
No, that wasn't it. I see what you mean now. Screenshot below shows gparted maximised. Earlier screenshot of FF is explained by cariboo907's comments :-) 
So it's just FF windows that double up the top bar.

---

### Post by castrojo on 2010-12-17
The window widgets are supposed to be in the top panel when the you maximize the application (to save space)

When you're using windows in their non-maximized mode the window widgets are attached to each window like normal.

Currently BOTH of them show up for testing, like we did for application menu testing for last cycle, basically by rendering both we can make sure that the top panel is showing what it's supposed to show -- so basically if the top panel shows something different than the window, report a bug.

So, as of now having a double set of window widgets is "normal" for testing.

---

### Post by Quackers on 2010-12-17
Excellent :-) Thank you castrojo.

---

### Post by mc4man on 2010-12-17
> so basically if the top panel shows something different than the window, report a bug.

So would you consider screen in post9 a bug - no doubling

---

### Post by castrojo on 2010-12-17
Actually that's what it's supposed to look like! (eventually anyway)

I'm not sure for firefox (it seems to be the special case for everything), let's see what chriscoulson has to say about it. 

It's probably best to hold off on the bug reports for now as this just landed today and there's a bunch of confusion. DBO will drop by later and clarify.

---

### Post by mc4man on 2010-12-17
I do see what Quackers was initially talking about (other than firefox), I think

If you open nautilus, go fullscreen and start navigating thru folders it will double, but the menu bar listing doesn't always get updated, it can stay on a previous location. (if it stays doubled

At the same time, when only one listing is in unity's menu bar than it's always correct.
(hard to explain, pretty easy to see.

(or if you wait long enough it seems to catch up

---

### Post by Quackers on 2010-12-17
Yes, I see that now and again, where the top panel can show what you were last looking at - not what you are currently looking at.

---

### Post by mc4man on 2010-12-17
So here's your deal with firefox

Open firefox, un-maximize and close
Re-open firefox, maximize and it shouldn't double 

Close firefox while maximized, re-open and it should double

---

### Post by Quackers on 2010-12-17
Hmm, just tried that twice...no change. Still doubles up, but it's ok. At least I know why now. I'm happy :-)  see?

---

### Post by mc4man on 2010-12-17
No big deal, on my desktop I never use maxed windows, almost never on laptop (can't use scroll on desktop
( - though kinda surprised - fairly demonstrable here, generally speaking - 
windows that are maximized on the desktop never double
windows that open maximized usually do

---

