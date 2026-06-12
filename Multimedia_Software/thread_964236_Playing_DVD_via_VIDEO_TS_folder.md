---
title: "Playing DVD via VIDEO_TS folder"
date: 2008-10-30
forum: Multimedia Software
---

### Post by oRioN84 on 2008-10-30
Greetings everyone, I'm a bit stumped on an issue I've been having and haven't found a reasonable solution as of yet. Here's my situation:

Before switching to Ubuntu (8.04) recently, I had used WinDVD v6.0 in WindowsXP to play DVDs. I usually rip the DVDs to my computer via DVD Decrypter and they are stored in a VIDEO_TS folder. With WinDVD, I could choose "Open Folder" and select the VIDEO_TS folder (without going inside it) and it would come up with the DVD menu, I could click "Scenes" or "Play DVD" etc, and it would play the whole thing through until the end.

I'm looking for a native Linux DVD player that can do the same thing. I currently use Mplayer - but upon choosing to "Open File" and browsing to the VIDEO_TS folder, it takes me inside and I have to choose individual VOB files. The first one, for example, plays the menu of the DVD but I can't click "Play" or anything, it's just like a raw video and not interactive.

I would rather not burn them to DVDs because I don't prefer to use this method. I'm fond of being able to load a VIDEO_TS folder (without going inside) and just have it play the DVD from start to finish, interactive menus and everything. Is this possible to achieve on Linux, or even by running a Windows program thru Wine?

I will try to give as much info about my Linux as possible: I am using Ubuntu Linux v8.04 Hardy Heron, Kernel version is 2.6.24-21-generic

Thanks

---

### Post by mc4man on 2008-10-30
many players will play back from video_ts, either from player side - 'open directory' or from a right click on a video_ts - 'open with' or if nothing's shown continue to 'open with other application' or in some cases " use a custom command' ( when the apps default lainch command is unsuitable 

Vlc, totem-xine, xine-ui all work well with a video_ts from either direction (vlc 0.9.x has a problem opening a directory, use the r. click 'open with'


side note

Once you've used the 'open with other application' what you've picked should show up in the 'open with' list. (there is a small bug there - let's say I pick vlc in the 'open with other application'. It won't show up in the 'open with' until I pick something else, in other words it's always 1 pick behind.

---

### Post by caljohnsmith on 2008-10-30
Try VLC Media Player from the repositories; if you go to File > Open Directory, you can tell it to open the "VIDEO_TS" folder, and I think you should even get the DVD menus and everything. Give it a shot and let me know how it goes. :)

---

### Post by oRioN84 on 2008-10-31
Thank you kindly for the timely responses. I downloaded the VLC player and it works great. I can open the VIDEO_TS folder and it plays all VOB files automatically. Main menu is not interactive, but it's easy enough to skip ahead one chapter and start the movie. All the responses are much appreciated, and I'm going to check out those other media players that were suggested just to get a feel for them. Thanks again, problem solved!

---

### Post by mc4man on 2008-10-31
vlc should be able to have disc navigation (working menus) from a video_ts. By default the launch command is 'vlc %U' which isn't so good. To change
Right click on Applications -> edit menus. Highlight sound & video and then right click on vlc ->  properties. Change the command to this
```
vlc %f
```

Sometimes it's better to r. click on the video_ts -> open with vlc (or open with other application ect. as described above

---

### Post by kwaanens on 2009-02-25
Just a heads up, since I'm reading this thread: Did you know that in addition to this, you can drag&drop an ISO, or other DVD image onto VLC and play the DVD, with menus and all?

---

