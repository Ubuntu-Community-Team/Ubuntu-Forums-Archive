---
title: "[SOLVED] VLC fullscreen respawns X11 output windows"
date: 2008-09-18
forum: Multimedia Software
---

### Post by [TCK] on 2008-09-18
System: Kubuntu 8.04 w/ KDE 4.1
Graphics card: ATI X1600 using fglrx driver
Dualscreen setup with different resolutions

Everytime I fullscreen a video in VLC 0.8.x an X window (with no title) appears in the taskbar.  The problem is, when deactivating fullscreen this doesn't disappear from the taskbar, and continuously fullscreening video results in multiple X windows appearing.  These can't be closed at all and can't be removed unless I log out or remove and re-add the task manager plasmoid.

After updating VLC to 0.9.2 the problem continues, but instead of untitled X tasks in the taskbar they're titled "VLC (X11 output)".

Perhaps unrelated, but at the start of every video VLC briefly flashes a black screen for half a second before playing as it should, fullscreen or not.  Bothersome but bearable.

I've attached my xorg.conf file and [**here**]("http://i130.photobucket.com/albums/p251/TCKOCR/VLCX-1.jpg") is a screenshot of the problem.

This could very well be a KDE problem, but VLC is the only program where fullscreen causes this.  No sign of this in Dragon Player or MPlayer.

---

### Post by [TCK] on 2008-09-19
Found a workaround which so far has worked.  By checking the "Only show tasks from the current desktop" box the problem no longer happens.  I only have one desktop enabled so it's not a big problem.

I'm more inclined to call it a KDE4 bug now.

---

### Post by angel_buntu2007 on 2009-01-26
[B]For me, the solution for this problem was this:

In VLC go to Tools Menu, Then Preferences
Go to the Audio Tab
Then in "Effects" make sure that the Visualization option is on "Default"
Save Changes, restart VLC and that should be it.:D[/B]

---

