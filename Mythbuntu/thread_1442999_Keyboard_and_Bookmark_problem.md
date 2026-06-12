---
title: "Keyboard and Bookmark problem"
date: 2010-03-30
forum: Mythbuntu
---

### Post by Sctmon on 2010-03-30
I am having a minor issue with the keyboard not responding after resuming playback of a video file from a saved bookmark.

If I play a video file, save a bookmark then exit to the main menu, select the same file to play again followed by either 'Play from beginning' or 'Play from bookmark', once the file is playing, mythtv does not respond to the keyboard. 
I have to use the mouse to select another application and then select mythtv again before it responds. Changing to another workspace and back also does it but simply using the mouse to click somewhere on the currently running mythtv doesn't.

Any suggestions?

---

### Post by garrison on 2010-03-30
From what I know, this is an issue where the pop-up fails to return window focus to Myth's internal player. I did happen across a [chat log]("http://mythtv.beirdo.ca/ircLog/channel/1/2010-01-22") where some fellow wrote:

> I think in trunk the Qt-based popup was replaced with a mythui popup, so it doesn't trip the bug, anymore

Hopefully a fix will work it's way into repositories soon, but I've already started to get accustomed to using Ctrl-Alt-Arrows to quickly shift desktops and restore focus.

If you find an interim fix, please post it.

---

