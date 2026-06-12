---
title: "How to edit Flac profile in Sound Juicer?"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by ubuhick on 2007-09-06
I want to change the compression of the FLAC encoding to "8" (smallest size).

In Sound Juicer, I have found the edit profile option and under FLAC I see this line:

audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc

My question is what do I need to edit in that line to make the FLAC encoding an "8" or best?


It is easy to see what to change when editing the ogg profile:

audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux


On another note, I did figure out the work around with the Sound Juicer profile bug.  Originally when I tried to edit profiles, I couldn't even make an entry in the window.  As it turns out, one must close the "edit GNOME Audio Properties" window and then you access the profile window.

---

### Post by ubernoob on 2007-09-08
i dont know how sound juicer works. But if you want flac, i guess you want the best quality. I'm not sure if sound juicer supports cdparanoia to rip from the cd, so you should consider using grip instead of sound juicer.

This is the recommended command for grip/flac:
[http://www.hydrogenaudio.org/forums/index.php?showtopic=45939](http://www.hydrogenaudio.org/forums/index.php?showtopic=45939)

---

