---
title: "Subtitles from .vob"
date: 2008-01-19
forum: Multimedia Production
---

### Post by Tyconic on 2008-01-19
First things first, I am very much a n00b to dvd ripping/decoding/what have you (although this question is more about playback, I guess). 

I was wondering if it was possible to access subtitles with only the original .vob files? For instance, using mplayer to switch between orig language, subtitles, and dubs.

My understanding is that subtitles are encoded as part of the .vob file, however, when I play the movie (as with mplayer) I get just the original language. So far I have been using dvdrip to extract subtitles into .sub, .ifo, and .idx files, but this seems like I am just duplicating data.

Could anyone shed some light on this issue for me? 
Thanks in advance.

---

### Post by disturbed1 on 2008-01-20
I could never get mplayer to always display the correct subtitles from vobs, dvds seem to work. I just use VLC. In VLC you can right-click on the video and choose between different subtitles and audio streams. 

For mplayer - y and g *should* cycle through the subtitles, F (shift+f) displays forced subs, r and t change the subtitle position. For more commands type man mplayer in the terminal for the manual page.

---

### Post by Tyconic on 2008-01-20
Hmm, it doesn't look like y and g do anything for me, except to bring up the text 'Subtitle delay: 0ms' and not much else

Shift+F only works after I have already loaded subtitles with -vobsub

---

### Post by Tyconic on 2008-01-20
VLC is pretty awesome though! Thanks for pointing it out, works perfectly. I actually discovered some "hidden" commentary subtitles. :cool:

Also, sorry for the double post.

---

### Post by disturbed1 on 2008-01-21
> **Tyconic said:**
> VLC is pretty awesome though! Thanks for pointing it out, works perfectly. I actually discovered some "hidden" commentary subtitles. :cool:

Also, sorry for the double post.

Glad it worked out for you. 

You could toy around with the settings (Preferences -> Settings) check the advanced box to show more. If you happen to change a wrong setting, you can delete the .vlc (thats a period in front of vlc) folder in your home directory. This is where the config file is held.

---

