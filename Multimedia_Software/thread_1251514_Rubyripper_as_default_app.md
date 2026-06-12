---
title: "Rubyripper as default app?"
date: 2009-08-27
forum: Multimedia Software
---

### Post by Bartender on 2009-08-27
Searched but did not find.  How to make Rubyripper the default for Audi Disc?  

I went to Places>Computer, right-clicked on Audio Disc, clicked on Open with Other Application, then "Use custom command", then "Browse".  Found 'ruby' and 'ruby 1.8'.  Tried them both, both were added to the "Open with Other Application" list, but neither one seems to do anything.  You can click it into the custom command box, then Open, then get out and come right back and it's gone.  Popped in another Audio CD, Sound Juicer is still the default.

---

### Post by mc4man on 2009-08-27
It was really easy to do, even in hardy where there is no custom command box in file management for default actions on removable media.

Basically one way was to set your usual prefs. in the gui, then use the command line rr to rip silently in the background upon inserting  audio cd's.
If you wanted something different than the usual then you'd just use the gui or make the needed changes in the gui and auto rip

More suited for a lot of ripping using the same parameters

not sure if that;s what you had in mind, if so there is a potential issue.

The command used is ```
rrip_cli -a
```

The problem at the moment seems that versions higher than 0.5.4 don't respect the -a, so the background rip will fail waiting on a response that isn't forthcoming. (unless someone can script in the equivalent of 'enter' on the keyboard or knows the proper 'new ..?' command

( you could test your version by putting a cd in, then opening a terminal and running command. If it wants a response instead of starting the rip then a no go there.

(I have version 0.5.4 on one machine where it works perfectly


If you just want to autostart rr  in the gui mode than use this as your command
```
rrip_gui
```

---

### Post by Bartender on 2009-12-27
Hey, I found it!

Applications are stored in usr/bin.  If you want to make some other application your default, and it's not in the list of default apps that appear when you just ask for other apps, you've got to find the one you want in usr/bin, click on it, and see if the app that you wanted starts up.

Rubyripper was a bit confusing, because there are "ruby" and "ruby 1.8" files floating around in the Ubuntu filesystem and I don't think they have anything to do with Rubyripper.  But I noticed two folders that had icons with a ruby in them, and the icon looked sort of familiar to the Rubyripper icon.  So I clicked on "rrip_gui" and Rubyripper opened.  

OOOh, looks like progress.

So I wrote "rrip_gui" down on a piece of paper, then did this.

1 - Put in an audiobooks CD, then right-clicked on the "Audio Disc" icon that appeared on the desktop.
2 - Left-click on "Open"
3 - Left-click on "Edit"
4 - Left-click on "Preferences"
5 - New window comes up, left-click on "Media" tab
6 - New window comes up called "Media Handling".  Left-click on the drop-down arrow to the far right of "CD Audio"
7 - Click on "Open with Other Application"
8 - New window comes up called "Add Application".  Left-click on "Use a custom command"
9 - Browse to File System, usr/bin/rrip_gui, highlight it, click "Open"
10 - I closed all the windows, restarted the PC just to be safe, popped in the next audiobook CD, Rubyripper started instead of Sound Juicer!!

I are one leet hackerz dude whatever that means I'm it

EDIT:  2 steps forward, one back.  I finished ripping one audiobook CD and popped in the next one.  Although I already had RR up, another copy of RR appeared.  So after all that, it may be simpler to just go as far as the #6 instructions above and tell GNOME to "Do Nothing" when an Audio CD is inserted.  That way I can open RR once and just keep asking it to scan the drive when a new CD is inserted like I'd been doing before.  Sheesh.

---

