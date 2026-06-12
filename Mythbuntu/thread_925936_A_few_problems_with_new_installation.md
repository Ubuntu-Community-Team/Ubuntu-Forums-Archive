---
title: "A few problems with new installation"
date: 2008-09-21
forum: Mythbuntu
---

### Post by raptorjr on 2008-09-21
I have been using MythTV for 3-4 years but this is my first attempt with installing Mythbuntu, and now i have some problems that i haven't had before. I hope that someone can help me. Don't really know if these errors is Mythbuntu specific or not. The version off MythTV i used before is a little bit older.

1. After the system starts and mythbackend and frontend is autostarted i try to watch LiveTV i get the following error:

2008-09-20 17:26:22.067 TV: Attempting to change from None to WatchingLiveTV
2008-09-20 17:26:22.067 Using protocol version 40
2008-09-20 17:26:23.721 GetEntryAt(-1) failed.
2008-09-20 17:26:23.722 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo
2008-09-20 17:26:23.722 TV Error: LiveTV not successfully started

But if i kill mythbackend and start it manually in a terminal window, LiveTV works. It would be nice if the autostarting would work, especially for the rest of the family =)
(Note: Same error as jeff45, but his solution don't change anything for me.)

2. In my old system i was able to run the frontend with suid root. I've tried to set every possible file to use suid root like mythfrontend and mythfrontend.real. But when playing something it is still using "USleep with busy wait" as video time method. Is it possible to use realtime priority with Mythbuntu?

3. When playing recordings or LiveTV the volume is nice. But when playing a movie with mplayer(and sometimes the internal player) the volume is very low. It can't be the recording because i didn't have this problem on my old system.

4. Almost related to 3, some movie files don't have sound at all with the internal player, but they worked fine in my old system, and they work with mplayer. I really would like to have the same interface for all my videos and the internal player is better integrated and the one used with recordings and LiveTV. I only
use mplayer when i really have to. Once again, easier for the family to need to learn only one player. And since it worked before with the internal player i guess something is missing now.

5. I have a PVR-250 tvcard with IR. I also have a Imon VFD with IR, but i use the IR on the tvcard. But if i have the VFD connected and lirc_imon module is loaded, the input from my remote get all messed up. The same remote button can give different codes when pressed some times, making it impossible to make a lircd.conf. If i don't connect my VFD everything works perfect with the lircd.conf that came with the system. Would be nice to be able to use the VFD also.

A lot of problems, but maybe i can get help to find the solution for some of them?

Thank you.

---

