---
title: "Wine - media player, power point can't find files"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by TravMan63 on 2007-06-23
I've started a new thread as this one covers windows media player too - hoping if THAT is fixed it will fix the other ..... [-o<...
(I've also posted for help on google wine groups and wine...)

other ubuntu thread
[http://ubuntuforums.org/showthread.php?t=470842](http://ubuntuforums.org/showthread.php?t=470842)

--- now the issue ---
Running Xubuntu 7.04

I have successfully installed PowerPoint2003 and Windows Media player 6.4 (and IEs4Linux) (v6)

Both execute 'ok' - I can load and play ppt files with embedded wavs etc...

Both of these applications have this one error in common:

Neither will open (insert) a media file - WMP reports 'check path and file...' and PowerPoint did have the same error - now it just halts on attempting to insert a file.


I believe it is NOT a 'directory issue' (Powerpoint can browse and open ppt files), and I'm not sure that WMP is needed to play an embedded file (at least not in windows ([http://www.playsforcertain.com/tutorial.htm#Multimedia_in_Microsoft_PowerPoint](http://www.playsforcertain.com/tutorial.htm#Multimedia_in_Microsoft_PowerPoint))), and a mciqtz.drv file is somehow involved...

I've attempted LOTS of things including sidenet.... but can't get this resolved... 
(regarding the mciqtz.drv file - I believe that file is required for playback, and may be a cause of powerpoint halting)

And - as a note about Open Office 2.2 (which I tried 1st) - Impress is NOT 100% compatible with the presentations created in PowerPoint, (wav ebedded doesn't play , and while movies DO play, they are very slow and only play about 3-5 seconds of the clip - xine plays same files perfectly) and it's also much slower on transitions etc... (this 'slower issue' has been reported by other users of impress as well)

One thing I hope to try is ppt player on a ppt file with the correct wmv/mpg linked to it - but can't provide that myself...)

Any 'winers :-({|=' out there that can give me a hand?

Many Thanks to all those who have helped so far...

TM

---

### Post by TravMan63 on 2007-07-03
bump

---

### Post by TravMan63 on 2007-07-30
This problem is fixed - partially.

Media player still does not find files.

Powerpoint does - the problem was with a missing dll (mciqtz32.dll - I THINK that 's the name)
it was missing from the windows\system32 folder.

Somehow - I'm guessing by running a 'wine configurtor program' (like wine-doors - but - it wasn't that one)... I had two installs of wine... (or windows - there was a c drive, and windows folders in the same directory - and under 'c drive' was windows again)...

Powerpoint opens the ppt and plays it fine, unless there are videos in it - they will not play.

TM

---

