---
title: "Only fullscreen available with mplayer"
date: 2008-10-04
forum: Multimedia Software
---

### Post by borlosky on 2008-10-04
I'm having this weird issue with mplayer. when ever i open a file to watch, it immediately goes to full screen mode, but it also has the windowed mode controls still visible along with full screen controls. when i try to exit out of full screen mode, nothing, won't exit. but movies still play fine. and whats weirder, while it's in full screen i still see my menu bar but no title bar. so to close it i have to go to file, then exit player. but i shouldn't even see that menu bar while in full screen anyway....pls help. i can post screen shots once i'm back home and at that pc if needed...


::edited for spelling::

---

### Post by markbuntu on 2008-10-04
If you have the full screen box checked, mplayer will do that. Open mplayer, right click on the screen and select preferences and choose something other than full screen. If that doesn't work, try removing and reinstalling it.

---

### Post by goatnipples2002 on 2008-11-23
I've tried all the suggestions and the problem is still there. Anybody have an answer?

---

### Post by mgmiller on 2008-11-23
Open your home folder.
Hit ctrl h to make the hidden files visible. (or click on View > Show Hidden files).

Navigate to the folder called   .mplayer
Notice this folder name begins with a "."

Inside that folder click on the file called gui.conf to open it in gedit, or whichever your default editor is.

Scroll down to the line that reads 
load_fullscreen = "yes"

Or you can search for it by clicking on the "Find" button and putting:
"fullscreen"  (without the quotes) in the field.

and change it to read:
load_fullscreen = "no"

Save the file and try running mplayer.

---

### Post by borlosky on 2008-11-24
> **mgmiller said:**
> Open your home folder.
Hit ctrl h to make the hidden files visible. (or click on View > Show Hidden files).

Navigate to the folder called   .mplayer
Notice this folder name begins with a "."

Inside that folder click on the file called gui.conf to open it in gedit, or whichever your default editor is.

Scroll down to the line that reads 
load_fullscreen = "yes"

Or you can search for it by clicking on the "Find" button and putting:
"fullscreen"  (without the quotes) in the field.

and change it to read:
load_fullscreen = "no"

Save the file and try running mplayer.

will try that as soon as i get home, other suggestions haven't worked.


::edit:: tried what you suggested, and it's already set to "no". here's a screen shot of what it looks like, it's like it's stuck between full screen and regular maximized mode. i should also mention, it's totem player, not mplayer, i was mistaken.


anyway here's the screen shot (notice the 2 control bars at the bottom.) the leave full screen button does nothing, either does the hot key to go in and out of full screen mode ie: F11. i also have no title bar, so close/maximize/minimize buttons are not available as well.

[http://s29.photobucket.com/albums/c282/borlosky/?action=view&current=Screenshot-TotemMoviePlayer.png]("http://s29.photobucket.com/albums/c282/borlosky/?action=view&current=Screenshot-TotemMoviePlayer.png")

---

### Post by goatnipples2002 on 2008-12-10
I tried as well and no change.

---

### Post by mgmiller on 2008-12-11
In totem, what happens if you just double click on the image area?  That should also toggle it between full screen and normal modes.

Also, go to Edit > Preferences and select the "Display" tab and try unchecking the "Automatically Resize the window when a new video is loaded" option.  

Or if it's unchecked, try checking it.

---

### Post by borlosky on 2008-12-12
> **mgmiller said:**
> In totem, what happens if you just double click on the image area?  That should also toggle it between full screen and normal modes.

Also, go to Edit > Preferences and select the "Display" tab and try unchecking the "Automatically Resize the window when a new video is loaded" option.  

Or if it's unchecked, try checking it.

tried both of those options, no change.

---

### Post by mc4man on 2008-12-12
If your using gmplayer ( mplayer from the applications menu) then open it up, right click on the video screen -> preferences -> misc and see if 'fullscreen' is checked

---

### Post by mgmiller on 2008-12-13
Go to your home folder and hit ctrl/h to show hidden files.
Open .gnome2/Totem
There is a configuration file in there called "state.ini"
You could try editing it to change the "maximized=true" to "maximized=false".

You could also try deleting the file (or renaming it to be on the safe side).
I think totem will recreate it if it's not there.

EDIT:
this config file may also exist in your home folder in .config/totem
(~/.config/totem/state.ini)

Since I have been updating my Ubuntu without reinstalling since 2005, I don't know which is the "real one", although I suspect the .gnome2 is the way it's done now.

---

### Post by goatnipples2002 on 2008-12-22
Not sure what happened but it seems to work fine now. It may have been fixed with an update. I will post if anything changes.

---

### Post by DizzyC on 2008-12-22
> **mgmiller said:**
> Go to your home folder and hit ctrl/h to show hidden files.
Open .gnome2/Totem
There is a configuration file in there called "state.ini"
You could try editing it to change the "maximized=true" to "maximized=false".
.......
EDIT:
this config file may also exist in your home folder in .config/totem
(~/.config/totem/state.ini)

Since I have been updating my Ubuntu without reinstalling since 2005, I don't know which is the "real one", although I suspect the .gnome2 is the way it's done now.

It's in ~/.config/totem/state.ini...

I had the same problem. Was stuck in fullscreen... allthough it was not real fullscreen. The controls where still visible, only the window decorations where missing.

I edited the state.ini file. I had "maximized=false" and changed it to "maximized=true"

That solved it!
10x mgmiller

---

