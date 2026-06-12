---
title: "Gnome Sound Recorder - Only records the sound of a sine wave"
date: 2011-08-22
forum: Multimedia Software
---

### Post by jeff.biggeek02 on 2011-08-22
Ok, so I could really kick myself for this, but I went to class today for the first time after a nice long summer with no school work and lots of programming. :) To my surprise, the gnome sound recorder in Ubuntu no longer seemed to work. When I tried to record sound, the little real-time sound level thingy in the bottom right stayed pegged/clipped out. Last semester, it moved based on the sound in the room. So, I assumed it might be a bug and continued recording the 3 hour lecture.

But then I got home, and just tried to listen to it.  I recorded 3 hours of a steady sine wave that sounded like someone was holding down a piano key or something.  Immediately, it occurred to me where I had heard that sound before.  This summer, I was experimenting with GStreamer, and had adjusted the default input source to be "Test Sound" instead of "PulseAudio Sound Server" in GStreamer's properties.  Doh! That would explain it...but I couldn't remember how to switch it back.

After some quick googling, I remembered a program called gstreamer-properties.  Sure enough, I ran that program from the terminal, and saw that my default input device was "Test Sound". After switching it back, Gnome Sound Recorder works properly again, and I can be entertained in class as my professor's yelling bounces the sound meter up and down.

I'm writing this into the forum so that it's searchable in case anyone else ever experiences the same issue.  They probably won't because you would likely need to be a programmer to have set that setting in gstreamer-properties, and smart programmers would have put the setting back when they were done with it! :)

---

