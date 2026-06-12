---
title: "Unity Papercuts"
date: 2011-04-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aaaantoine on 2011-04-26
These are not as critical as my [VirtualBox not working](http://ubuntuforums.org/showthread.php?t=1739768), but I was wondering if anyone else has any input on the following, or other nitpicks of their own.

1. I prefer to Maximize and restore windows by way of double-clicking the title bar.  The restore functionality works even with Unity, which surprised me considering the top bar doubles as the drop-down menu.  However, when restoring using this method (and this method only, it appears), the window restores itself about 150-200 pixels to the right of its previous position.

2. The window controls do not offer tool-tips.  None of them.  Close / Minimize / Maximize / Restore controls do not have tool-tips explaining what the button does.  I mean, I could guess on my own, and I've been using these controls for years, but what about new users?

3. I'm used to being able to drag a window to different workspaces.  I understand that this behavior was dropped in favor of utilizing the semi-maximized windows feature, which gets triggered by dragging to the top, left or right.  Could we add some behavior when dragging a window to the bottom?  Minimize may seem logical.  But, I would personally like to have the screen zoom out to the Workspace Expo view, and the cursor reposition according to what desktop you were focused on.  Then, when you release the mouse button after dragging the window where you want it, the expo zooms back in on the desktop you have moved the window to.

4. I feel as though the Workspace switcher should be on a static location on the Unity bar, either at the top or just above the trash bin.  That way, when using the mouse only, I can utilize muscle memory to jump to the workspace switcher instead of having to first find it on the bar.

---

### Post by sgage on 2011-04-26
I think it would be useful to be able to paste into the F2 "run program" dialog. I have a couple of long command lines that I have written in a file. With the old Gnome, you could copy&paste right into the F2 box, and from then on it would be in the history. With Natty you have to type it in manually. I tend to just use a terminal instead, but I'd rather that I could just type a couple of letters into the F2 dialog and have the history come up from which I can pick my app.

---

### Post by cariboo on 2011-04-26
@sgage, there is a bug for the Alt-F2 paste problem, see bug #[lpbug]736222[/lpbug]

---

### Post by sgage on 2011-04-26
> **cariboo907 said:**
> @sgage, there is a bug for the Alt-F2 paste problem, see bug #[lpbug]736222[/lpbug]

Thanks Cariboo - I've gone and given it my "me too".

---

### Post by mc4man on 2011-04-26
> **aaaantoine said:**
> 


3. I'm used to being able to drag a window to different workspaces.  I understand that this behavior was dropped in favor of utilizing the semi-maximized windows feature, which gets triggered by dragging to the top, left or right.  Could we add some behavior when dragging a window to the bottom?  Minimize may seem logical.  But, I would personally like to have the screen zoom out to the Workspace Expo view, and the cursor reposition according to what desktop you were focused on.  Then, when you release the mouse button after dragging the window where you want it, the expo zooms back in on the desktop you have moved the window to.

Nothing was really dropped, natty is just using a certain default set of  plugins w/ some things enabled, some not, ect. You're free to set up pretty much as you want as far as plugins used and what's enabled, bindings, ect. for that plugin. ( with some bindings reserved for unity and some possible conflicts you'd need to resolve

So for instance grid - you don't have to use or if you do something can be set for bottom edge but only from what's available (minimize doesn't appear to be an option

Or you can disable grid and use either rotate or wall to do edge flipping
(I use rotate and it works just fine, there is an erroneous conflict as shown in screen, I have both enabled just fine

As far as expo it doesn't use a window drag to initiate so it's not a papercut to change a plugin

---

### Post by ZarathustraDK on 2011-04-26
Here are my pet-peeves:

1# Dash needs some love. There needs to be more categories in there that the user can choose from. Currently there are only 4 (Media, Internet, All and Find files). If you've had no prior experience/instruction in how dash works, then you can get stuck looking for programs, as you either have to "guess" the name by typing in dash, or go hunting through the "All programs" category. An administration category and preferences category would be nice (difference being "does it require root or not to use"). Typing in dash is for after people learn the names of the programs, newbies don't know, so...

2# The background-color of the icons in the quickbar seem random at best. Is there some kind system I'm missing? It would be neat if background-colors were coded as per the application-category. Example: currently Chromium, Banshee and Writer all have blue backgrounds while Firefox has orange, doesn't really make much sense in terms of grouping in the quickbar. Rather, Firefox and Chrome should both have the same background color because they're internet-centered apps, while Banshee and Writer should have different colors because they relate to media and text-processing respectively. Using this color-coding would give the user an immediate idea about the applications use, without requiring the user to necessarily recognize the icon itself (important to new users who don't know much about all the apps that experienced users are used too).

3# Loose the "Lenses"-buttons, or make them less imposing. Users already have both in the dash-button in the left uppermost corner. OTOH that same button need to be a bit more prominent, it's one the most important buttons in the whole interface and currently it's a diminutive dull grey square, half the size of the quickbar icons, with a white Ubuntu icon on it. Imagine trying out Linux for the first time, would you consider the current button as more "important" than the quickbar-icons?

4# Not quite a papercut in the sense that it's a major alteration to Gnome: Make it possible to easily assign different wallpapers to different workspaces. We have Expo as standard now, so 1-up that eye-candy by making expo interesting to look at and people interested in using it. A bit of anecdotal "evidence": I find myself using expo at times for no other reason than to see it and/or get a fresh wallpaper.

5# CCSM should be installed by default, and have a global "restore defaults" button if people manage to muck it up. Face it, Compiz has a big draw on a lot of newbies, and newbies don't know they need CCSM to mess around with, basically, the whole appearance and behavior of the desktop. Coming from any other OS you'd expect that kind of functionality to be built-in from the start.

Just my 0.02$ ;)

Kudos to the devs btw, Natty went from barely usable (errors etc.) to stable on me in like a week. Was genuinely afraid we wouldn't make it this time. :)

---

