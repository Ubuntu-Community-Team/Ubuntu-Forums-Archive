---
title: "Sound troubles (terratec)"
date: 2005-12-19
forum: Multimedia &amp; Video
---

### Post by TripleSix on 2005-12-19
I've just recently installed Ubuntu (breezy), and all went kinda smooth, until I came to my soundcard, which is a Terratec DMX 6fire 24/96. 

From the beginning the audio was..weird. All the sounds played sounded like they were slowed down by a factor of 3, and stuttering. Then I (re)installed gstreamer, totem-xine, video and audio codecs (MP3 etc), and I disabled the sound server startup (which at least seemed to fix the slowing down part a little bit). Since then it seemed to work fine for the most part. I could play MP3's and movies fine

But later I tried to play an internet radio stream in Rhythmbox, and the same problem occurred. Stuttering audio (no, not buffering problems in the stream!). And it seems that every xx msecs of audio is played twice. (I hear a short echo). Maybe an important clue. On top of it all I can't get any sounds anymore in totem when I try and play an MP3 or movie.

Another thing is that I can't reset my audio preferences output in stereo. It accepts all other options (4.0, 4.1, 5.0, 5.1, AC3 throughput), except stereo.

Both default output and input are ESD.

I'm kinda new to this linux stuff- but I've shown this problem to my brother; an experienced linux user, and he couldn't figure it out also.. Thats why I'm posting this here..

Hope you guys can help!

---

### Post by TripleSix on 2005-12-20
Update: Sound works now, although the streaming audio problems persists

But there's another problem: I've set up 5.1 audio in alsamixer, and i'm playing MP3's thru xmms. The problem here is that the basses in the audio sound terrible, especially in the heavy tracks. The MP3's are fine and have always sound crystal clear in Windows. Any thoughts?

---

### Post by savage on 2006-03-01
I don't have any sure answers for you, in fact I'm looking for an answer to a different sound issue. With sound do keep in mind the issues with mp3 or any compressed codec. You may want to read the MP3 page on Wikipedia or similar. Streams can have sound issues that have nothing to do with buffering because of their quality. I use Streamtuner and sort streams according to bitrate.

For the mp3's that are on your machine ask yourself some questions if you haven't. Has there been any change in hardware. If your soundcard is in your machine, are there new cards nearby? Pull new cards then try. Maybe the encoder used isn't as compatible, I don't know the technicalities of this, maybe this doesn't matter? Are the sound settings right, go over them bring them all down then push them up one by one, in both XMMS and from the Volume Control panel. It is possible to have digital distortion. Try different settings, use alsa or whatnot, fiddle with the mixers. [Search]("http://www.google.com/search?q=linux+Terratec+DMX+6fire") for information concerning Linux and your soundcard or the chipset on it.

Good luck, sorry if this to late, maybe it will help someone else.

---

