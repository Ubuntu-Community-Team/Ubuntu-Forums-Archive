---
title: "Sound Juicer, GStreamer: how to rip CD to mono MP3, left ear only?"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by Bill Statler on 2007-06-12
I'd like to rip a stereo CD, and turn it into a mono MP3 that only plays in the left ear.  (Or, I guess it would be more accurate to say that I want a stereo MP3 in which the right channel is silent, and the left channel contains a mono version of the CD.)

(Why?  Because my wife is hearing-impaired in her right ear -- she has some hearing, but sounds are distorted.  Also, she just got one of those nifty Bose noise-cancelling headphone sets.  I'd like to make MP3s for her that would play in just her good left ear.)

I understand the basics of how to edit a GStreamer pipeline in Sound Juicer.  Here's what I'm using to make a high-quality *stereo* MP3:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 quality=2 ! id3mux
```

And here's how I modified the pipeline to make a *mono* MP3:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=3 bitrate=96 quality=2 ! id3mux
```

The "mode=3" tells lame to make a mono MP3, and I've cut the bitrate in half.  It works, but the mono sound comes out of both speakers.  Anyone know how to make it come out of only the left side?

(Okay, okay, the easy solution is to cut the wire going to the right side of her headset!  I know.  But that's so... inelegant.)

I'm currently using Ubuntu 6.06 and Sound Juicer 2.14.4.

Thanks for any suggestions.

---

### Post by Bill Statler on 2007-06-21
Answering my own question, in case anyone else wants to know:

I couldn't find a way to do this entirely in Sound Juicer, so I installed Audacity, which is a sound-editing program.  Here's what I'm doing:

1.  In Sound Juicer, Edit > Preferences, and set the output format to "CD Quality, Lossless (FLAC audio)".

2.  Use Sound Juicer to rip the CD to a bunch of FLAC files.

3.  In Audacity, Edit > Preferences > File Formats, and set the MP3 bit rate to half of what you'd normally use for a stereo MP3 (i.e., if you'd normally encode a high-quality MP3 at 192 kbps, use 96).

4.  Project > Import Audio to load one FLAC file.

5.  From the track pop-down menu, Split Stereo Track.  This produces two mono tracks marked Left and Right.

6.  (Assuming you want the final mono sound to come only from the left speaker...)  On the Right track, from the track pop-down menu select Left Channel.  Now both tracks should be marked as Left.

7.  For each of the two tracks, move the Gain slider to the left until it reads -6 dB.

8.  Project > Quick Mix.

9.  File > Export As MP3.

Done!  That is, done with one track.  This is a bit tedious, and I'd like to automate it.  It looks like sox might be the appropriate command-line tool for this, but it's going to take me a while to understand "man sox" well enough to do it.  If I figure it out, I'll post here.

---

