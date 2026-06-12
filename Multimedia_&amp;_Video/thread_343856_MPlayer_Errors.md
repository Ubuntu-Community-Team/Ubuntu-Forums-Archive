---
title: "MPlayer Errors"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by ax4413 on 2007-01-22
I have MPlayer installed and can play all media files from the shell using the command: 

*mplayer /directory/filename*

However i can not get mplayer to work in GUI mode from the application menu. Depending on which media type i try to open i get the following error message:

[I]Error opening/initializing the selected video_out (-vo) device.

Requested audio codec family [mp3] [afm=mp3lib] not available. Enable it at comilation[/I]

All and any help will be gratefully received. Additionally other than renaming files with spaces in the name is there any way to play them from  the shell using the mplayer command eg

 *mplayer /directory/ file name *

---

### Post by maranellored on 2007-01-22
to play files with spaces in their names,
use back slash and space. For eg.

**mplayer Play\ this\ file.avi**

if the name of the file is [B]Play this file


[/B]and ur other query, please search around the threads and u'll surely find a solution
p.s. i'm too lazy to post one ;)

---

### Post by DeadEyes on 2007-01-22
Hi maranellored,
When mplayer is loaded right click on it and select preferences then try changing your video and/or audio drivers. I think mplayer needs to be restarted for changes to take affect.
I have about ten different choices of each in mine. For audio ALSA is selected and gl2 for video. Not sure what the pros and cons of the different ones are, but this combo works for me.

---

### Post by ax4413 on 2007-01-24
Thanks DeadEyes that very nearly solved the whole problem for me. The video is working correctly now  and the audio still plays. I still receive the following error message though:

*Requested audio codec family [mp3] [afm=mp3lib] not available. Enable it at comilation*

The error message occurs when new media is loaded. It doesn't seem to affect any thing but its there non the rest. I have searched several  forums and can find multiple refferances to the error but no resolution.

---

### Post by frolle on 2007-01-24
The error message says it all :) You will find where to do it in options.

---

### Post by maranellored on 2007-01-24
well the best way to get rid of that message is to choose **ffmpeg** as ur audio codec when u choose it from preferences

that should get rid of that error

---

### Post by Copter on 2007-02-12
> **maranellored said:**
> well the best way to get rid of that message is to choose **ffmpeg** as ur audio codec when u choose it from preferences

that should get rid of that error

same thing here. thnx, problem solved :)
copter :]

---

### Post by gkokaisel on 2007-03-03
ahh I see, Mplayer isn't a very intuitive player. You have tell it what codec to use. Not quite sure what the benefit of this player is, I mean unless one likes to have to manually select what codecs to use in order to play something correctly. Gxine, VLC, the totem movie player...just auto detect, and the quality is no different if not better. Well, it was an educational experience anyway.

---

### Post by detectiveinspekta on 2007-03-15
I still have not managed to get rid of this message.

I do not have a audio codec named ffmpeg in mplayer. Audo plays fine though, I still get this message.


Also I couldn't select mplayer as the default application for avi files, it just wouldn't click down.

---

### Post by panch0 on 2007-03-16
You can try using another GUI like KPlayer. KPlayer runs the command line MPlayer behind the scenes so it doesn't give any popup messages, and it never pops up any messages on its own. If there is an error, it will say Error in the status bar, and you can click it if you want to see the MPlayer output.

---

