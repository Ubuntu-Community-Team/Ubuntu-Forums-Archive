---
title: "BBC Radio player crashes"
date: 2009-06-10
forum: Multimedia Software
---

### Post by ajgreeny on 2009-06-10
For the last couple of days (not sure exactly how long) I have not been able to get the BBC radio player to run without crashing Firefox.  It did run fine but suddenly not.  I have tried firefox with a new profile and no different, and I have also tried firefox -safe mode in terminal and it crashes with a segmentation fault, but no other useful information.  I can find nothing more in any logs on the machine and am getting a bit fed up with it, as nothing I have done seems to be the cause.  Just out of interest, I tried to install helix-player to get the BBC streams, but that also crashes with a segmentation fault if started from the terminal, and will not start at all from the menus

Has anyone else got the same problem at the moment, or can you suggest a way out.  I can still listen to the streams with mplayer (or gnome-mplayer) but I wonder what is going on.  Is it a BBC stream change of some sort?

Allied to this, I have a question regarding recording of the stream which is in another thread [here]("http://ubuntuforums.org/showthread.php?p=7435085#post7435085").

---

### Post by ajgreeny on 2009-06-12
For anyone with the same problem, a lot of searching has shown that the problem is the mozilla-mplayer package which is at fault.
The solution seems to be to uninstall *mozilla-mplayer* and instead use *gecko-mediaplayer*, both of which are available in the repos.  Both also use mplayer as the back-end which actually does the playing so all is well again.

---

