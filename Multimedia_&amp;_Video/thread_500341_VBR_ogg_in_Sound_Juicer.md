---
title: "VBR ogg in Sound Juicer"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by ricardisimo on 2007-07-13
Here's my audio profile settings in Sound Juicer for ripping into ogg vorbis:
```
audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=.8 ! oggmux
```
The only thing I've changed is the quality setting, from .5 to .8. When I examine the audio properties tab in any of the songs I've ripped, they are all at exactly 256 kbps, the odds of which are pretty slim, from what little i understand about VBR. But what this means is that the default settings for Sound Juicer do not use variable bitrate for ogg, which is a bit odd. How do I enable VBR in SJ for ogg. Thanks in advance.

P.S. - Yes, I did search the forum already for an answer to this. There are a million threads regarding VBR in mp3, and two unanswered posts regarding ogg. And the help page for oggenc doesn't even mention VBR.

---

### Post by Major_Kong on 2007-07-13
What program did you use to check the bitrate ? Totem ?

---

### Post by ricardisimo on 2007-07-13
Mainly I just looked at the audio tab within Nautilus' Properties dialog, but Rhythmbox, Amarok, Banshee, whatever... they all give the same info.

---

### Post by Major_Kong on 2007-07-14
If you use "0.8" instead of ".8" is there a difference ? (out of ideas)

---

### Post by vanadium on 2007-07-14
ogg is always vbr. There is no cbr ogg.

---

### Post by ricardisimo on 2007-07-14
OK, but shouldn't the 256 kbps vary from one track to the next, as it does with an mp3 encoded in VBR? Your "target" bitrate is 256, but one track will come out at an average of 247 kbps, the next at 231, etc. Every ogg file I've ripped is at *exactly* 256 kbps, not one bit more or less. You don't find that odd? Is the "targeting" that precise with ogg vorbis?

---

### Post by Major_Kong on 2007-07-14
The tag doesn't show you the actual avg. bitrate of the file, but the aprox. bitrate of the quality setting you selected. 
What's weird is that it doesn't change either you select .5 or .8 . Or did i misunderstood ?

---

### Post by ricardisimo on 2007-07-14
No, no... the quality does in fact change when I enter .8 instead of .5. That part is fine. What I'm asking is this: how do I know it's VBR, if the bitrate is always exactly 256 kbps? With mp3s it's very easy to tell; pretty much any application that deals with them will tell you that the song in question is, say, "~237 kb/s", with the tilde letting you know that this is an approximation. Even without the tilde, the fact that you have a song at a non-standard bitrate is normally a good enough sign of VBR. But this is not the case with my ripped ogg files.

Am I alone in this? Would anyone be willing to check their own archives to see if they can find any indication of VBR in their ogg files? Thanks in advance.

---

### Post by Major_Kong on 2007-07-14
Now i get it. Sorry, i misunderstood.

That's normal. The 256 kbps you see is the quality .8 setting (the nominal bitrate), it's not the real avg. bitrate. It's written in the .ogg i suppose, and gstreamer based players just read that.
If you use audacious, for .e.g., it will show you the bitrate changing while you play the file.

> To get an idea of the average bitrate for each quality level:

q -2 = 32 kbps (in aoTuV beta 4 and above)
q -1 = 45 kbps
q 0 = 64 kbps
q 1 = 80 kbps
q 2 = 96 kbps
q 3 = 112 kbps
q 4 = 128 kbps
q 5 = 160 kbps
q 6 = 192 kbps
q 7 = 224 kbps
[http://www.hydrogenaudio.org/forums/index.php?showtopic=15049](http://www.hydrogenaudio.org/forums/index.php?showtopic=15049)

---

### Post by ricardisimo on 2007-07-17
Thank you very much. You're absolutely right... Audacious (et al.) does indeed show the true bitrate as it fluctuates up and down. I'm assuming that the "256 kbps" is written as part of the tag rather than being any actual calculation on the part of Nautilus or the rest. That's kind of weird, but whatever. Thanks again.

---

### Post by hugmenot on 2007-07-28
This is called "nominal bitrates".

---

