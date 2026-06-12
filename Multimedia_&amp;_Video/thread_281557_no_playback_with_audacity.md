---
title: "no playback with audacity"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by Langstracht on 2006-10-21
Starting up Audacity results in a error window which states "There was an error initializing the audio i/o layer. You will not be able to play or record audio".

All the other audio programmes I use (amaroK, XMMS, Rhythmbox) play just fine.

Any ideas as to how to get Audacity to work much appreciated.

---

### Post by voided3 on 2006-10-21
Hello. Go to Audacity's site on sourceforge (just google "audacity"), they have their own forum. What I did to get rid of that error was to change the open command form "audacity" to "aoss audacity" with root privellidges. They said it initializes the sound driver, or something to that extent. However, upon opening the program and afer loading a sound file of any format, I get an error still. From what I could tell on Audacity's site, it's a bug they are working on, but the weird thing is the first time I ran the program I had no errors and was capable of playing sound and editing it.... Go figure, but I think the Audacity site/forum will help you out. Good luck!

---

### Post by Ambimom on 2006-10-21
Try this:

Go to System Preferences Sound and turn off ESD.

For some reason, Audacity won't work unless the ESD Sound is turned off.

When you exit Audacity, turn it back on.

There's other posts on this forum that explain this.  It's a quirk of Audacity.

---

### Post by pressman57 on 2006-10-21
Neither solution worked for me. A more detailed explanation can be found at:   [http://audacityteam.org/wiki/index.php?title=Linux_Issues](http://audacityteam.org/wiki/index.php?title=Linux_Issues)

---

### Post by Langstracht on 2006-10-22
Sorry for the delay in reporting, bit of a busy weekend.

In any event, good news.  And bad.

Turning off ESD eliminated the error message ... AND I actually do get sound now.  Thanks to all.

However, while OGG files perform fine ... MP3's have adopted a chipmunk air.  Anyone know why they wouldn't play at the "right speed"?  Or how to adjust it?

Any and all help appreciated.

---

### Post by CatKiller on 2006-10-22
> **Langstracht said:**
> MP3's have adopted a chipmunk air.  Anyone know why they wouldn't play at the "right speed"?

I've heard that this can happen if the file is a variable-bitrate one, when the software is expecting fixed, or vice versa. I can't say that that is the cause of your specific problem though.

---

