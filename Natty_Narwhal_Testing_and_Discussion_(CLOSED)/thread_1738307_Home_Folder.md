---
title: "Home Folder"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by teachop on 2011-04-24
It is a small point but I think they should rename nautilus in the launcher to something other than "Home Folder".  It is disorienting when you are not in the home folder to see "Home Folder" as the title in the panel.

---

### Post by r-senior on 2011-04-24
Have you tried an update? Mine's showing as File Manager now.

---

### Post by CaptainMark on 2011-04-24
im up to date and i see home folder

---

### Post by teachop on 2011-04-24
I do seem to be up to date.  It is Home Folder...

---

### Post by r-senior on 2011-04-24
Hmm. Wonder how I managed that then. :)

I can only guess that at some point I dragged the "File Manager" icon onto the launcher from /usr/share/applications.

---

### Post by teachop on 2011-04-24
> **r-senior said:**
> Hmm. Wonder how I managed that then. :)

I can only guess that at some point I dragged the "File Manager" icon onto the launcher from /usr/share/applications.
Maybe we should wonder how I messed it up.  Just now I edited the .desktop file so says "File Manager" like yours.

But maybe I got here because I installed xubuntu-desktop after the ubuntu natty beta 2.  Perhaps there was a clash there?

I guess the question is, for people that have it saying "Home Folder", did you install xubuntu-desktop?

---

### Post by 3rdalbum on 2011-04-24
> **teachop said:**
> Maybe we should wonder how I messed it up.  Just now I edited the .desktop file so says "File Manager" like yours.

But maybe I got here because I installed xubuntu-desktop after the ubuntu natty beta 2.  Perhaps there was a clash there?

I guess the question is, for people that have it saying "Home Folder", did you install xubuntu-desktop?

No.

To the OP, well pointed-out. I hadn't noticed, but now it's going to annoy me :-)  Should definitely be fixed.

---

### Post by CaptainMark on 2011-04-25
+1

i didnt either, and yeah its gonna bug now i know its there

---

### Post by mc4man on 2011-04-25
The default would be home folder  but as seen you can change. There is an overall weakness in the unity panel when not using a maxed window  (any app,) - it then only shows the name of the .desktop that opened the window, nothing unique as far as location or file name, ect.

---

### Post by teachop on 2011-04-25
> **mc4man said:**
> The default would be home folder  but as seen you can change. There is an overall weakness in the unity panel when not using a maxed window  (any app,) - it then only shows the name of the .desktop that opened the window, nothing unique as far as location or file name, ect.
Then it seems the better rule to use a generic name like "File Manager" in the .desktop files, and not something that will be clashing half the time like "Home Folder".

---

### Post by mc4man on 2011-04-25
You could file a bug on - there are 3 .desktops already available in /usr/share/applications that all do about the same
Home Folder, File Manager, File Browser
(if one was to switch icons in launcher then a log out/in is needed to show change in display name

I'd prefer if the unity panel would _always_ reflect location or file name instead of just the .desktop's Name=

---

### Post by teachop on 2011-04-25
> **mc4man said:**
> I'd prefer if the unity panel would _always_ reflect location or file name instead of just the .desktop's Name=
Yes, and I bet it gets there before 11.10 releases.

---

### Post by seeker5528 on 2011-04-25
For me when I mouse over the file manager icon it says 'File Manager'. When I open it shows the name of my home directory. If I change directories the window title changes to the name of the directory I am viewing.

> **mc4man said:**
> The default would be home folder  but as seen you can change. There is an overall weakness in the unity panel when not using a maxed window  (any app,) - it then only shows the name of the .desktop that opened the window, nothing unique as far as location or file name, ect.

I'm not seeing that. For applications in general as far as I can recall (there could be exceptions?), the window title is always the same for me whether an app is maximized and showing the window title in the top panel, or un-maximized and showing window title in the window's title bar.

Firefox shows identification of the web site it is open to in the title bar or top panel.

Nautilus, PCmanFM, and Dolphin all show the directory you are viewing in the title bar or top panel. 

At lest that is what I am seeing on my machine.

EDIT: Looking at the .desktop files for Nautilus, none of them show 'File Manager' on the 'Name=' line, one shows 'Name=File Browser' and one shows 'Name=Home Folder', so I don't know where the launcher on the launcher panel is getting the 'File Manager' name from. I don't have any custom .desktop files in '~/.local/share/applications/' for Nautilus. Unless I deleted the original and later ran Nautilus and pinned it to the launcher.

Later, Seeker

---

### Post by teachop on 2011-04-25
> **seeker5528 said:**
> Firefox shows identification of the web site it is open to in the title bar or top panel.

Nautilus, PCmanFM, and Dolphin all show the directory you are viewing in the title bar or top panel. 

Firefox has the same issue for me.  Right now, not maxed, it is showing "Firefox Web Browser" in the panel.  Maximized, it says "Ubuntu Forums - Reply..."etc. LibreOffice Calc says "LibreOffice Calc" unless it is maximized (of course the Global Menu is deranged for LibreOffice too, but that is another thread).  Qt Creator say "Qt Creator" in the panel unless it is maximized.  They all are that way in the panel, as far as I can tell.  The place that "Home Folder" clashes is in the panel, not in the title bar.

---

### Post by seeker5528 on 2011-04-25
> **teachop said:**
> Firefox has the same issue for me.  Right now, not maxed, it is showing "Firefox Web Browser" in the panel.  Maximized, it says "Ubuntu Forums - Reply..."etc.

I must have missed something while reading the thread. When I mouse over the icon on the panel, I always see the same identification whether the app is minimized/maximized, opened/closed, it doesn't matter. Never occurred to me to look for that and I can't think of a reason why that would be useful to me for that text the change dynamically.

If I only have one window of an application open, I don't need the icon on the launcher panel to display anything other than the application name, if the same app has multiple windows open, either I will see the window I want when I click the app's icon or I will have to click again to get the scale view of all it's open windows, so I still don't need any thing other than the application name when mousing over the icon on the launcher panel.

EDIT: On a semi related note, I went into CCSM and enabled 'Scale addons' so on the rare occasion I can't tell from the thumbnails which of an application's open windows I want to switch to I can right click to zoom in and out.

Later, Seeker

---

### Post by teachop on 2011-04-25
> **seeker5528 said:**
> I must have missed something while reading the thread. When I mouse over the icon on the panel, I always see the same identification whether the app is minimized/maximized, opened/closed, it doesn't matter. Never occurred to me to look for that and I can't think of a reason why that would be useful to me for that text the change dynamically.
Icons are on the Launcher, not the panel.  We are speaking about the panel.  Up top.  Not the Launcher or title bar.  The OP was about the Panel saying "Home Folder" when nautilus was in some other directory.

---

### Post by mc4man on 2011-04-25
> EDIT: Looking at the .desktop files for Nautilus, none of them show 'File Manager' on the 'Name=' line,

The "File Manager" .desktop 
> [Desktop Entry]
Name=File Manager
Exec=nautilus
Icon=system-file-manager
ect.

> For applications in general as far as I can recall (there could be exceptions?), the window title is always the same for me whether an app is maximized and showing the window title in the top panel, or un-maximized and showing window title in the _window's title bar._

Well at least here on a 04/22 install unmaxed windows only show the .desktop name in the unity panel, when maximized then they show location or file name - _in the unity panel_

These are the 3 - I just use the default (nautilus-home.desktop)
What it shows in the 'tool tip' or the name in unity panel when not maxed doesn't particularly matter here - I know I'm using nautilus

---

