---
title: "Can't change WAV-files tags"
date: 2009-05-17
forum: Multimedia Software
---

### Post by Bjor on 2009-05-17
I all, I have a [Edirol R-09HR WAVE/MP3 recorder]("http://www.edirol.com/index.php/en/products-mainmenu-421/field-recording-mainmenu-390/r-09hr"). I use it to digitalise my vinyl-albums.
When I try to fill in the tags (id3 I think) in Amarok this is what I get: "Sorry, the tag for XXXXXX.WAV could not be changed".
So I've tried other programs like Rhythmbox, Easytag, Ex Falso, Cowbel, ... , everything I've found on synaptic, but nothing can change the tags. Some programs like cowbell and kid3-qt don't even recognize the files.
I do have writing permissions on the files.
I can change the tags on files that are recorded in mp3 format.
I'm really stuck with this problem, the files are unasable for me without tags. :-&
Any idea what the problem is?

---

### Post by squaregoldfish on 2009-05-17
WAV files can't have tags. Therefore, no program will be able to add tags to them.

Steve.

---

### Post by Bjor on 2009-05-17
Thats a reasonable explanation ;).

Are there no ways to let amarok recognize these tracks?
I mean, on a friends pc in windows i've tried these files, Itunes and mediamonkey could tag the files, probably the tags weren't saved in the file itself, but in a seperate database.

For me is this a real big issue as I need studio grade wav-files, i really don't want to recode them to another format as no other format can handle the resolution and I had very bad experiences with recoding from wav to flac, with pops and digital noise and everything!

I've got around 1000 albums to digitalize, so tags are a must.

---

### Post by squaregoldfish on 2009-05-17
Hmm. My first guess would be that if you name your wav files with a common structure (Artist - Title.wav, for example), you might be able to get a music player to interpret them and add them to the database that way. I don't know enough of the workings of any music players to know if that will work, but it would be my starting point.

Steve.

---

### Post by Bjor on 2009-05-17
I've tried that one, but it doesn't work on Amarok...
thanks anyway

---

### Post by squaregoldfish on 2009-05-17
If you don't mind playing with other music players, this might help you:
[URL="http://www.mail-archive.com/rhythmbox-devel@gnome.org/msg03838.html"]
http://www.mail-archive.com/rhythmbox-devel@gnome.org/msg03838.html[/URL]

---

### Post by Bjor on 2009-05-17
in fact I love amarok, so a amarok solution would be good.
But eitherways, I've tried it in Rhythmbox and I can't change the tags, like was explaind in your link.

---

### Post by mc4man on 2009-05-17
> I had very bad experiences with recoding from wav to flac, with pops and digital noise and everything!

Kind of surprised there, on a live jaunty cd so a bit limited in testing. Anyway took one of the .wav samples from your link (piano/24/96) and used flac

Came out fine, though will save and test the file later on main box with good sound system

flac --bps=24 --sample-rate=96000 -8 02_Piano_24bit96kHz.wav

don't have amarok installed but sounded fine thru mplayer

> ubuntu@ubuntu:~$ mplayer 02_Piano_24bit96kHz.flac
MPlayer SVN-r29154-4.3.2 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 02_Piano_24bit96kHz.flac.
Audio only file format detected.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 96000 Hz, 2 ch, s32le, 2559.4 kbit/41.66% (ratio: 319926->768000)
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio)
==========================================================================
AO: [alsa] 96000Hz 2ch s32le (4 bytes per sample)



---

### Post by zero777zero on 2009-05-17
there are no standard tags for wav, i suggest you convert them to flac which is a lossless compression and uses tags

---

