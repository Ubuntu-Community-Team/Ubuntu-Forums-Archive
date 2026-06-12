---
title: "Movies - Converting VBR MP3 or AC3 audio streams to CBR MP3"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by PeterDB on 2007-12-25
Hi,

Being a former Windows user, I kinda got used to using Gspot, VirtualDub and Nandub to check for used codecs and format, but most importantly to transcode my movies, so they could play on my Archos player.

Unfortunately, the Archos player doesn't really support AC3 or VBR MP3 audio streams in movies well, so I need to transcode them. However, I can't find a good alternative for Ubuntu.

My question(s):

1. What is a good replacement for Gspot in Ubuntu or what can show me codec and format information from a movie.
2.  What can I used to convert AC3 or VBR MP3 in movies (avi DivX and Xvid) to CBR MP3?

/P.

---

### Post by ron999 on 2007-12-25
Hi
The answer to question 1 is 'MediaInfo'.
It's a command line application but it's simple to use.
You just enter MediaInfo <name of file>

Here's an example:-

[B]ron@ron-desktop:~$ MediaInfo /home/ron/trial4.avi
General #0
Complete name : /home/ron/trial4.avi
Format : AVI
Format/Info : Audio Video Interleave
Format/Family : RIFF
File size : 2.70 MiB
PlayTime : 1mn 5s
Bit rate : 338 Kbps
Writing application : Lavf0d.50.5.0

Video #0
Codec : xvid
PlayTime : 1mn 5s
Bit rate : 197 Kbps
Width : 160 pixels
Height : 128 pixels
Aspect ratio : 5/4
Frame rate : 12.000 fps
Resolution : 24 bits
Bits/(Pixel*Frame) : 0.803

Audio #0
Codec : MPEG-1 Audio layer 3
Codec profile : Joint stereo
PlayTime : 1mn 5s
Bit rate : 125 Kbps
Bit rate mode : CBR
Channel(s) : 2 channels
Sampling rate : 48 KHz
Resolution : 16 bits
StreamSize : 1001 KiB
Writing library : Lame
[/B]

If you're using Ubuntu there's a deb available. Look for version 0.7.5.4 here:-[http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612]("http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612")
8)

---

### Post by PeterDB on 2007-12-25
thanks, MediaInfo does look to be a solid and simple tool. Do you know if there is a UI for it?

---

### Post by disturbedite on 2007-12-25
its really not a good idea to convert lossy formats to other lossy formats, as you lose quality.  but if you must, convert them to 320 br.

---

### Post by PeterDB on 2007-12-25
thanks for the reply.

unfortunately, I am aware of this, incl. the severe loss incurred when coverting from AC3 to  any MP3 format, surround sound is truly lost. However, rather have the sound in MP3 format and be able to watch the movie, than not.

But the question still remains, is there an easy app to do this with, or is it really all CLI stuff?

/P

---

### Post by ron999 on 2007-12-25
Hi - This is a GUI method.

You ** 'Open'** the file in 'Avidemux'. Install Avidemux with Synaptic if necessary.

Leave the Video tab (On the left hand side) set to '**Copy**'.
Change the Audio tab to '**lame**' and click 'configure' to set it to CBR. 
Leave the Format tab set to** AVI**.
Then '**Save**' it as movie.avi or whatever.

That should leave the video content unchanged and the audio changed to mp3 in an avi wrapper.

It will take a long time to do the job, depending on your CPU speed and the length of the movie etc.

Try it out first with a short clip.
Compare the codecs used  'before and after' using MediaInfo.
:cool:

---

### Post by disturbedite on 2007-12-26
> **PeterDB said:**
> thanks for the reply.

unfortunately, I am aware of this, incl. the severe loss incurred when coverting from AC3 to  any MP3 format, surround sound is truly lost. However, rather have the sound in MP3 format and be able to watch the movie, than not.

But the question still remains, is there an easy app to do this with, or is it really all CLI stuff?

/P
if your player supports ogg (or even better yet, flac), i'd use one of those formats instead, cuz they're free & they support surround sound.

---

### Post by PeterDB on 2007-12-27
Hi Ron, thanks for the steps, I will give them a whirl this afternoon.

@disturbedite: Unfortunately, the player doesn't support Ogg or Flac. Archos does make okay devices, but truly perfect they are not. I know, that I am going to move away from using the player and getting an ITX based Media Center style system setup, since that is really the only way forward.

---

