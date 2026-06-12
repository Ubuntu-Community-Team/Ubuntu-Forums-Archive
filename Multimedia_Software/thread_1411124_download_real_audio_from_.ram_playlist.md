---
title: "download real audio from .ram playlist"
date: 2010-02-19
forum: Multimedia Software
---

### Post by stefansjs on 2010-02-19
Hello all,
   I am trying to download streaming real audio to .mp3 files.  I found a post at [http://ubuntuforums.org/archive/index.php/t-542276.html](http://ubuntuforums.org/archive/index.php/t-542276.html) explaining how to use mplayer to save a pcm .wav file as I listen.  This is a great start.  I am hoping that somebody can do me one better, though.  

I'd like to be able to either 
(1) save without listening (i.e. not in real time) or 
(2) encode directly to mp3 (if it's not too much processing).

The other I'd like to be able to do is save each song in the playlist separately to different files on the disk.  It'd be especially awesome if I could use the file name included in the stream to name the file written to the disk.  

thank you

---

### Post by andrew.46 on 2010-02-19
Hi stefansjs,

> **stefansjs said:**
> I am trying to download streaming real audio to .mp3 files.  I found a post at [http://ubuntuforums.org/archive/index.php/t-542276.html](http://ubuntuforums.org/archive/index.php/t-542276.html) explaining how to use mplayer to save a pcm .wav file as I listen. 

Nice post that one :). I was a a little fresh and new back then but that technique still works well enough.

> I'd like to be able to either 
(1) save without listening (i.e. not in real time) or 
(2) encode directly to mp3 (if it's not too much processing).

If you mean that you would like to save the stream while you are not present I suspect you will have to create a script and run this from cron. This is what I still do every Sunday night to r[ecord my favourite radio broadcast]("http://www.andrews-corner.org/ftgws.html"). It is a small matter to put lame in such a script rather than oggenc...

> The other I'd like to be able to do is save each song in the playlist separately to different files on the disk.  It'd be especially awesome if I could use the file name included in the stream to name the file written to the disk.  

That could be a bit tricky, can you give the address of this stream?

All the best,

Andrew

---

### Post by stefansjs on 2010-02-21
Well, in my case I am not streaming from a live broadcast, but rather from an authenticated website.  So, unfortunately even if I gave the URL to my stream, you still wouldn't be able to access it without either having a particular IP address or authenticating.  What I'd like to do is download directly from the server at the rate that I can rather than at the rate I can listen.  It seems like the command given in this guide uses mplayer to save to a .wav file as it plays the .ram file.  What I'd like to do if possible is bypass the playing of the file and just go directly from the .ram stream to .wav without playing it.
thanks

---

### Post by andrew.46 on 2010-02-22
Hi stefansjs,

> **stefansjs said:**
> What I'd like to do if possible is bypass the playing of the file and just go directly from the .ram stream to .wav without playing it.

Well, you may very well still have to save as wav and then convert to mp3 but there is a method to download the file much more quickly by adding the following to your MPlayer commandline:

```
-bandwidth 1000000
```

You will find that this speeds up the download process *markedly*. To convert to mp3 at the same time usually involves using using named pipes / mkfifo, which I admit I have not experimented much with so hopefully others can help out here :).

All the best,

Andrew

---

### Post by stefansjs on 2010-02-22
Upon further inspection, I've discovered a couple of things that get me closer but don't quite answer my question.  First of all, I discovered that the .ram file is just a list of rtsp streams.  I also discovered the -dumpstream -dumpvideo -dumpaudio -dumpfile options for mplayer.  I've tried using these options but I think I've hit a snag with my .ram file.  it has rtsp streams with .mp3 files in it:
> rtsp://128.2.20.69:554/johnston s07/rep and listening week 7 s07/1 Virga Jesse floruit - A.mp3
rtsp://128.2.20.69:554/johnston s07/rep and listening week 7 s07/2 Virga Jesse floruit - B.mp3
rtsp://128.2.20.69:554/johnston s07/rep and listening week 7 s07/3 Symphony No. 8 in C minor - i. Allegro moderato.mp3
rtsp://128.2.20.69:554/johnston s07/rep and listening week 7 s07/4 Symphony No. 8 in C minor - ii. Scherzo Allegro moderato.mp3
rtsp://128.2.20.69:554/johnston s07/rep and listening week 7 s07/5 Symphony No. 8 in C minor - iii. Adagio Feierlich langsam .mp3
rtsp://128.2.20.69:554/johnston s07/rep and listening week 7 s07/6 Symphony No. 8 in C minor - iv. Finale Feierlich, nicht sc.mp3

Every time I try to -dumpaudio or -dumpstream it saves a file (roughly 4 MB) to my computer, but mplayer can't play it and opening it with Audacity displays a 4 second audio file chocked full of glitches.  I suspect this might have to do with the fact that mplayer thinks that these mp3 streams are real audio streams and storing them incorrectly.  At the very least, I'm confused about the rtsp mp3 streams.
I now have 2 issues:
1) The files aren't playable
2) The dumpstream options don't allow for individual dumping of files in the playlist.  
Any scripting and/or command-line options to handle each file individually (especially if it'll keep the original filenames in tact) would be greatly appreciated.

---

### Post by stefansjs on 2010-02-24
Alright, I'm still investigating, but I can't seem to get to a solution.  I'm really hoping that somebody in this forum can help me.  I've read a bit more about rtsp to discover that it's just a streaming protocol and doesn't really have anything to do with real audio (although real audio could be streamed over rtsp [http://en.wikipedia.org/wiki/Rtsp](http://en.wikipedia.org/wiki/Rtsp)).  I've also discovered that my computer is dumping the audio to a stream.dump file that I can't play.  I think it might have something to do with the line towards the bottom here about the output that says "invalid chunksize!"
> stefan@stefan-laptop:~$ mplayer -playlist Downloads/rep_and_listening_IV_week_7.ram -dumpaudio
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://128.2.20.69:554/johnston s07/rep and listening week 7 s07/1 Virga Jesse floruit - A.mp3.
Resolving 128.2.20.69 for AF_INET6...
Couldn't resolve name for AF_INET6: 128.2.20.69
Connecting to server 128.2.20.69[128.2.20.69]: 554...
Cache size set to 640 KBytes
Cache fill: 18.75% (122880 bytes)   
REAL file format detected.
Stream mimetype: audio/X-MP3-draft-00
[real] Audio stream found, -aid 0
demux_real: invalid chunksize! (0)
realrtsp: Stream EOF detected
Core dumped ;)

Exiting... (End of file)

Please, if anybody knows what's going on or knows a better place to be asking this question, help me out.
thank you

---

### Post by andrew.46 on 2010-02-24
Hi stefansjs,

> **stefansjs said:**
> Please, if anybody knows what's going on or knows a better place to be asking this question, help me out.

If the stream is definitely mp3 leave out *-dumpaudio* and use instead:

```
-dumpstream -dumpfile test.mp3
```

Andrew

---

### Post by stefansjs on 2010-02-28
Well, overall mplayer seems to be inconsistent for me.  For the rtsp streams that actually work, it seems to be doing when I use -dumpstream and creates perfect .m3 files.  Thanks for that.  However, there are a bunch of streams that just don't work whatsoever.  This is what mplayer says:
> MPlayer interrupted by signal 13 in module: open_stream
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

I tried uninstalling and reinstalling mplayer, but that didn't seem to do a thing.  I'm really not sure what's going at all right now.  I've tried googling the error and I mostly get an mplayer bugreport that claims that this problem was solved.

---

### Post by andrew.46 on 2010-03-01
Hi stefansjs,

> **stefansjs said:**
> I tried uninstalling and reinstalling mplayer, but that didn't seem to do a thing.  I'm really not sure what's going at all right now.  I've tried googling the error and I mostly get an mplayer bugreport that claims that this problem was solved.

One problem is that you are actually using quite an elderly version of MPlayer. If you are keen there are some guides on these forums that would lead you through building a more recent version...

Andrew

---

### Post by stefansjs on 2010-03-01
I am still running 8.04.  I wonder if that's why my version of mplayer is so old.  Are there newer versions in the repos?  Can you direct me to some of these guides on updating mplayer?
thank you

---

### Post by andrew.46 on 2010-03-01
Hi stefansjs,

> **stefansjs said:**
>  Can you direct me to some of these guides on updating mplayer?

There is a decent enough guide here:

[Howto] Successfully install the svn MPlayer under Hardy Heron 
[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

written by some fellow with obviously too much time on his hands :).

Andrew

---

### Post by stefansjs on 2010-03-01
Hey, thanks so much.  Your responses have been very helpful, and thanks for the mplayer guide.  I've just got one little problem that's been bothering me that would save me a bunch of time if you know the answer.  mplayer seems to know the name and author of each file I'm playing
> Playing week4/track10dump.rm.
REAL file format detected.
Stream mimetype: audio/X-MP3-draft-00
[real] Audio stream found, -aid 0
demux_real: invalid chunksize! (0)
Clip info:
 name: Rigoletto - I/iv: Pari siamo!... io la lingua
 author: Studer, Cheryl, sop/Luciano Pavarotti, ten/et al./Metropolitan Opera Orch & Chorus/James Levine

It'd be great if I could either rename the .rm file to the name (in this case "Rigoletto - I/iv: ...etc") or use an mplayer command line option so that I can save the wave file.
e.g.:
```
mplayer -ao pcm:fast:file="Filename here" week4/track10dump.rm
```

Thanks in advance

---

### Post by andrew.46 on 2010-03-02
Hi stefansjs,

Hmmm... I am not so sure about this one although I suspect it could be scripted. You will need to have a look at MPlayer's *-identify* option but I will admit that I have not used this with a stream before...

All the best,

Andrew

---

### Post by stefansjs on 2010-03-15
Andrew.46, I hope you're still reading this thread even though it's closed.  I found out what the problem is that I'm having.  My rtsp streams have filenames with foreign character accents in them.  When this happens mplayer crashes.  For example (note the "a" with umlaut):
> ~$ mplayer -dumpstream -dumpfile "rep/week9/track2-dump.mp3" -noconsolecontrols "rtsp://128.2.23.13:554/johnston s07/rep and listening week 10 s07/02 Symphony No. 4 in G - ii. In gemächlicher Bewegnung.  Ohn.mp3"

MPlayer SVN-r30809-4.2.4 (C) 2000-2010 MPlayer Team

Playing rtsp://128.2.23.13:554/johnston s07/rep and listening week 10 s07/02 Symphony No. 4 in G - ii. In gemächlicher Bewegnung.  Ohn.mp3.
Resolving 128.2.23.13 for AF_INET6...
Couldn't resolve name for AF_INET6: 128.2.23.13
Connecting to server 128.2.23.13[128.2.23.13]: 554...
librtsp: server responds: ''


MPlayer interrupted by signal 13 in module: open_stream
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
MPlayer SVN-r30809-4.2.4 (C) 2000-2010 MPlayer Team

Is there a way to escape these characters, even if I have to modify each character manually?

---

### Post by andrew.46 on 2010-03-16
Hi stefansjs,

> **stefansjs said:**
> Andrew.46, I hope you're still reading this thread even though it's closed.  I found out what the problem is that I'm having.  My rtsp streams have filenames with foreign character accents in them.  When this happens mplayer crashes.  For example (note the "a" with umlaut):

Is there a way to escape these characters, even if I have to modify each character manually?

You may have a case to bring to the mplayer-users as this should not happen. They will however ask for a sample stream that can be tested...

Andrew

---

