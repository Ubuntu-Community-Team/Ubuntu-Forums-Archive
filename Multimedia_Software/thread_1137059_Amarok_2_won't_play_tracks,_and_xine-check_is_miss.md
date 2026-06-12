---
title: "Amarok 2 won't play tracks, and xine-check is missing"
date: 2009-04-25
forum: Multimedia Software
---

### Post by andycs on 2009-04-25
So a few days ago I upgraded to Jaunty, and it went reasonably painlessly. The only thing that's a big annoyance is that Amarok upgraded to Amarok 2, and now I can't for the life of me get it to play music. My entire library shows up OK, but whenever I try to play something, absolutely nothing happens.

In addition, in trying to run xine-check for diagnostic purposes, I find bash doesn't know what xine-check is, even though I have xine-ui and xine-console installed. Possibly most mysteriously, I even have a working manpage for xine-check; just not the program itself.

Is there anything I can do?

---

### Post by wolandt on 2009-04-25
got the same problem but also suffer from some collection items missing

---

### Post by mc4man on 2009-04-25
you could try searching this just forum (Multimedia & Video) for amarok 2 and find useful stuff

2 things to ck. if installed

```
sudo apt-get install phonon-backend-xine libxine1-ffmpeg
```


(to search a specific forum use 'advanced' search or go to a forums main page and there is a ' search this forum' option

There's also useful info in this forum (read only)
[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

---

### Post by andycs on 2009-04-25
I did check most of the posts about Amarok 2 before posting, and none of them seemed to have the same problem. I already checked for libxine1-ffmpeg, following advice from another thread, and that was already installed - phonon-backend-xine wasn't installed, but didn't fix any problems - xine-check still doesn't work, and Amarok 2 still won't play tracks.

---

### Post by rws265 on 2009-04-26
I had the same problem after upgrading to Jaunty. Amarok did not like my Nvidia audio. My solution was to run Xine and select the alsa mixer. Odd way to go about it but it worked for me.

---

### Post by andycs on 2009-04-27
Fantastic, thanks - that seems to have fixed it, strangely. To clarify, what I did was open the xine video player, get into settings by hitting Alt+S, then:

Under the 'gui' tab, change 'Configuration experience level' to 'Advanced' or higher
Go to the 'audio' tab, which will now show a number of options
Under 'audio driver to use', select 'alsa'
Close xine

After that, Amarok showed the same error message on startup, but instead of giving out errors a-plenty when trying to play tracks, it seems to be working.

---

### Post by tjma2001 on 2009-04-27
i got it working by deleting my .xine and .kde directory.. there is probably one specific entry/file that needs to be deleted but i was too impatient to get my music working..

---

### Post by animal671 on 2009-04-27
I just deleted xine-config from the .kde directory and then restarted Amarok. Music is playing again...

---

### Post by lidex on 2009-04-28
Was pulling my hair out trying to get Amarok 2 working. Thanks for the tip to install phonon-backend-xine. Works perfectly now! Wonder why it's not pulled in as a dependency. Oh well, thanks mc4man.

---

### Post by Lupi on 2009-04-29
I installed libxine1-ffmpeg and now it works.

---

### Post by reswob on 2009-04-29
I did the same and it works.  Thanks!

---

### Post by Andrevv on 2009-04-30
It is some problem with configuration files of Xine in /home folder but I don't know which one is it. I have deleted .xine folder and it is working correctly now.

---

### Post by Idiot_Box on 2009-05-03
This fixed mine.

Close Amarok, make sure no processes running
make sure the following are installed: phonon-backend-xine libxine1-ffmpeg

Deleted:
/home/tom/.kde/share/apps/amarok - FOLDER
/home/tom/.kde/share/config/amarok* - All Amarok Files
/home/tom/.xine - FOLDER

Closed all audio/video programs
Started Amarok, working normally

---

### Post by nadeepa on 2009-06-13
It worked for me..
thanks

---

### Post by Jaguarandine on 2009-06-14
deleting the .xine folder worked for me. Thanks!

---

### Post by Sir Rodness on 2009-07-04
> **Lupi said:**
> I installed libxine1-ffmpeg and now it works.
This also worked for me.

---

### Post by Rusodelapaternal on 2009-07-04
muy muy muy bueno. GRACIAS ahora puedo usar Amarok.

El Ruso

---

### Post by Fenris_rising on 2009-07-05
Just installed jaunty today. i also had to do the : phonon-backend-xine libxine1-ffmpeg to get Amarok working :D Well done all!

regards

Fenris (Now over a year of Ubuntu :D )

---

### Post by Dex Luther on 2009-10-01
Installing libxine1-ffmpeg also worked for me, thanks! I'm also wondering why it wasn't already installed as a dependency. It seems like a pretty big thing to leave out seeing as Amarok doesn't even work at all without it.

---

### Post by c0ldfuse on 2009-10-11
I encountered this problem yesterday and struggled with it for quite some time.

I loaded all the libraries and packages described in a few different fix questions on here but didn't have any luck getting it to work.  Randomly this morning while in package manager, I noticed it didn't see the xine-backend as installed despite literally minutes earlier seeing it as installed when I tried to apt-get it (so frustrated decided to go back and make sure everything was good).

Problem solved :shrug:.

---

### Post by rob22941 on 2009-10-15
I'm having this same problem. I'm running 9.04 and I can't find these .xine folders to delete under the filesystem. Would there be a command for the terminal to search for them? Any input do you need any information from me? Thanks much gents and ladys.

---

### Post by achase79 on 2009-10-16
open up a window to your home folder and his ctrl+H to show hidden files.  Now you will be able to see the .xine folder

---

### Post by rob22941 on 2009-10-17
Alright here is what I did:
Deleted:
/home/robert/.kde/share/apps/amarok - FOLDER
/home/robert/.kde/share/config/amarok* - All Amarok Files
/home/robert/.xine - FOLDER

I'm still having trouble with Amarok 2. It isn't allowing me to adjust or create new playlist's for my ipod or allow me to add new songs. I can only play my songs. However, Rhytmbox is now allowing me to edit playlists. But still not allowing me to add new songs. ...to cut to the chase... I would prefer to use RhythmBox. Would there be folders/files I could edit to have full capabilities with RhythmBox for my ipod rather then Amarok2? If that isn't possible what else is there to do for Amarok? Thanks much.

---

### Post by Ram0ne on 2009-10-23
> **mc4man said:**
> you could try searching this just forum (Multimedia & Video) for amarok 2 and find useful stuff

2 things to ck. if installed

```
sudo apt-get install phonon-backend-xine libxine1-ffmpeg
```


(to search a specific forum use 'advanced' search or go to a forums main page and there is a ' search this forum' option

There's also useful info in this forum (read only)
[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

This fixed it for me with Karmic

---

### Post by Skerit on 2009-10-24
You'd think libxine1-ffmpeg would be a dependency of Amarok2 in Karmic by now, but no. It still isn't.
Ah well, amarok2 managed to crash on something as trivial as a migration from Amarok1.4
No big loss.

---

### Post by quill3033 on 2010-01-13
> **Idiot_Box said:**
> This fixed mine.

Close Amarok, make sure no processes running
make sure the following are installed: phonon-backend-xine libxine1-ffmpeg

Deleted:
/home/tom/.kde/share/apps/amarok - FOLDER
/home/tom/.kde/share/config/amarok* - All Amarok Files
/home/tom/.xine - FOLDER

Closed all audio/video programs
Started Amarok, working normally




Thank you!  this worked for me. It's working great now. On Linux Mint Helena on the eeepc 1000h.

---

### Post by quill3033 on 2010-01-15
but it seems to have lost its shoutcast radio list :-(

---

### Post by HammerHed on 2011-05-26
> **Idiot_Box said:**
> This fixed mine.

Close Amarok, make sure no processes running
make sure the following are installed: phonon-backend-xine libxine1-ffmpeg

Deleted:
/home/tom/.kde/share/apps/amarok - FOLDER
/home/tom/.kde/share/config/amarok* - All Amarok Files
/home/tom/.xine - FOLDER

Closed all audio/video programs
Started Amarok, working normally

This fixed mine 100% - thanks so much. I am running 11.04, Amarok was working 100% then suddenly stopped, I could not get it to add anything to a playlist or play anything at all.

---

