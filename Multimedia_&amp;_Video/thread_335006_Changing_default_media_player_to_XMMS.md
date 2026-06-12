---
title: "Changing default media player to XMMS?"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by johnc4510 on 2007-01-09
Hi all, I purchase a new cordless desktop and have gotten most of the hotkeys to work. My problem is that when I select the hotkey for the music player, it launches Rhythm Box, but I prefer XMMS. I can't seem to find where to change the default at. Any ideas? Thanks in advance.

---

### Post by tweedledee on 2007-01-09
> **johnc4510 said:**
> Hi all, I purchase a new cordless desktop and have gotten most of the hotkeys to work. My problem is that when I select the hotkey for the music player, it launches Rhythm Box, but I prefer XMMS. I can't seem to find where to change the default at. Any ideas? Thanks in advance.

I'm guessing, but try System/Preferences/Removable Drives & Media -> Multimedia, and change the "Portable Music Player" command.  I don't know what command is being issued by your hotkey, though.

If that doesn't work, you can use xbindkeys instead of Metacity to launch XMMS.  Instead of setting up the metacity shortcut, install xbindkeys and use it to trap the keypress (you may need to use xev to figure out what keycode it corresponds to).  You can lots of help on xbindkeys in the forums and at the xbindkeys main site (the program is in the repos).

Last, you may want to look into Audacious as a replacement for XMMS: it's basically the same thing (a branch of a branch from the XMMS project), but is still being actively developed.  It's not the repos, but they provide an Ubuntu .deb, and I've found it more reliable than XMMS and it certainly looks better.

---

