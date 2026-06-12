---
title: "playing files from a DVD using VLC"
date: 2009-06-16
forum: Multimedia Software
---

### Post by pythonscript on 2009-06-16
I have a set of files that are copied from a DVD, and under Windows, VLC media player gives me an option when I right click on the folder to "Play folder using VLC media player" (or something like that). It starts playing the DVD, starting with the menu, letting me navigate through the DVD menus just like I was using a remote on my DVD player (selecting subtitles, "play movie" "scenes" etc).
On ubuntu jaunty, however, there is no such option, and when I open VLC, choose open Disc (or folder, file, whatever the case, the problem still persists) it will start playing the DVD, but it doesn't start from the menu, so I can't select subtitles, scenes, etc. Is there any way to run VLC on ubuntu with this option from Windows? This is hands down my *favorite* option from VLC in windows, and it seems a shame to have to boot into Windows just to play my DVD files properly. I don't care about using the terminal; I just want a solution that will do exactly what VLC on windows does, but with the ubuntu version. Thanks in advance!

---

### Post by mc4man on 2009-06-16
In regards to dvd's on hdd in file format (VIDEO_TS

The option to open a folder (either the VIDEO_TS or a folder containing a VIDEO_TS) is media -> open directory.

In all 0.9.x and 1.x versions that is broken, basically vlc will load all the files in the VIDEO_TS into a playlist randomly and start playback there.
(And actually there will be one or 2 that would take you to the menu, but there should only be one item in the playlist when opening a VIDEO_TS

It will work correctly in most cases if you right click on the folder (the VIDEO_TS or folder it's in) and go 'open with' -> "Open With   VLC media player"
(if vlc isn't listed choose 'Open With Other Application' and find it

---

### Post by pythonscript on 2009-09-06
Thanks for the tip. That's working perfectly now.

---

