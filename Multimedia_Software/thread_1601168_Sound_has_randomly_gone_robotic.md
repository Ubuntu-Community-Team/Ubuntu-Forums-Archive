---
title: "Sound has randomly gone robotic"
date: 2010-10-19
forum: Multimedia Software
---

### Post by Shay Guy on 2010-10-19
I upgraded to 10.10 several days ago. This is the second time I've had this problem since then, but the first time it was just a VLC problem, solved by restarting that program. Now it's affecting VLC, Audacious (tested to see if MIDIs were affected, too, which they are), Chrome, and Firefox, and not just Flash -- I tried the .ogg file embedded in [this page]("http://en.wikipedia.org/wiki/Waltzing_Matilda"), under "Lyrics," and it had the same problem. And while typing this, I've heard system tones similarly afflicted. It wasn't happening earlier today, and I can't think of what might have caused it.

Like the topic says, the problem is that the sound in all these environments has become what I can only describe as "robotic." Like it's extremely compressed. Evil R2-D2. It's not entirely divorced from what's supposed to be heard, because I've tried various YouTube videos with music and the rhythm is distinctly audible. In general, it's loud when it should be loud and quiet when it should be quiet.

Sometimes the melody is distinguishable, too; it works best if there aren't many different sounds supposed to be audible. I can make out the melody in that "Waltzing Matilda" .ogg, for instance, and ["Tsubasa wo Kudasai"]("http://www.youtube.com/watch?v=QKDaCckEt6M") isn't *too* bad -- I can actually make out the lyrics *and* the piano melody at the beginning (though I'm sure the K-On! version would sound much worse). The bass still translates into the same loud, robotic, constant-pitch sounds. (No, I'm not sure what note I keep hearing. Middle C, maybe?) ["Wakko's America"]("http://www.youtube.com/watch?v=eAII411eqPg") has a lot of its vowels and consonants recognizable as well, probably because of its relative simplicity. ["Bohemian Rhapsody"]("http://www.youtube.com/watch?v=fJ9rUzIMcZQ") is more problematic, but I can still make out the lyrics in the first 15 seconds or so, though they're still at that constant pitch. [This]("http://www.youtube.com/watch?v=H9PxwzP8jG0"), though? I can *barely* make out what *some* of the trumpets are supposed to be playing. [This Mario Paint Composer video]("http://www.youtube.com/watch?v=sffS2M8lT3s") is the closest to normal of all the ones I've checked, though it's still scratchy and all the "hearts" play that same bass note.

---

### Post by plzdontkillme11 on 2010-12-24
Hey man, I JUST had this problem a few minutes ago, and all I had to do is type "sudo alsa force-reload" after closing all audio applications in the terminal. Robotic sounding music, video, etc. is all fixed.

Seems you posted this a while ago, but I just thought I'd post a solution for people with similar issues.

Oh, and if you're using OSS4, do "sudo soundoff && sudo soundon."

---

