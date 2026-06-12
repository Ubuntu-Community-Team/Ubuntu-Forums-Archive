---
title: "just play WAV file from CLI, no GUI"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by boondocks on 2007-10-06
I have a few small WAV files.

They are associated with certain events like-
a.  File system getting full.
b.  Process not running.
etc.


I need to play a WAV file from the command line, without any kind of GUI.
Something like -
    wavPlayer   /home/me/files/wav/knockknock.wav

So I need a utility that just plays a wav file and then exits immediately and completely.

This way, when I am in the room but not looking at my Ubuntu system - I can still be notified.

---

### Post by Total_Biscuit on 2007-10-06
Did you try aplay (comes with alsa)?

---

### Post by Lord Illidan on 2007-10-06
No need to be limited to wav files..try mpg123 or ogg123 or even the mighty mplayer for your CLI multimedia needs!

---

