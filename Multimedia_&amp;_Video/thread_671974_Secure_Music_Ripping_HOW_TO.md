---
title: "Secure Music Ripping: HOW TO"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by mekkah on 2008-01-19
I've read several posts about people asking how to make secure rips of their CD's alá Exact Audio Copy. Most common answer is: use GRIP, run EAC trough Wine or use RubyRipper. I object by following PERSONAL reasons:

**1. EAC:** The whole point of moving to moving to Ubuntu for me, is to stop depending on Windows software. What's the point of moving to Linux if you still keep using Windows software? If i wanted to use Windows software, i'd still be running XP.

**2. RubyRipper:** Is still in the beta stage & quite buggy. I've had some problems with corrupted FLAC rips and decided to wait for an more stable release.

**3. GRIP:** is the ripper of choice for most people, mainly because it supports CDParanoia. I don't really fancy the interface & find it tricky to setup & have problems with special characters in the file names.

Ripper Of My Choice: **SoundJuicer** (Bundeled with Ubuntu)
Many people don't seem to realise that SoundJuicer is an CDParanoia frontend, just like GRIP. All you have to do, is a simple change in the configuration and SJ will be just as accurate. Also, SJ don't mess around with special characters. Editing the track info sure is a little trickier, since SJ makes use of the Musicbrainz database, but since SJ doesn't produce an extraction log like EAC, i don't see why that should matter. You can fix that after the ripping. To me, all that counts is an as accurate rip as possible.

**HOW TO MAKE SECURE RIPS WITH SOUNDJUICER IN 4 EASY STEPS:**

1. start the terminal and type: **gconf-editor**
2. goto: **apps/sound-juicer**
3. look at the paranoia key. it should say 16. Change it to **255** to enable full paranoia.
4. close the configuration editor (you can always change it back if you want to).

Now you'll rip CD's with full CDParanoia, just like in GRIP. 

**SOME EXTRA TIPS**
I recommend following folder hierarchy & file names:
**Album artist - Album/Number. Track Artist - Track Title**

Use **Kid3-qt** as your main tagger. It's far more complex than both Ex Falso & Easytag. Kid3 Supports embedded cover art, Track lookup from multiple sources, guessing from filenames & converting between ID3V2.4 and ID3V2.3, directory renaming & title formating.

If you can (and wish), use OGG instead of MP3. The setting: "CD QUALITY, Lossy" uses the Quality 5 setting, which is more than enough for most average users.

---

### Post by OoooMatron on 2008-01-19
Nice post. I have been using EAC in wine, i must admit. Will chekc out kid3-qt. I have been using easytag.

---

### Post by disturbed1 on 2008-01-19
What version of RubyRipper are you using?

I never encode with RubyRipper, just have it output to wav, and encode the files by hand.

It should be noted that the methods described above about SoundJuicer and Grip are **NOT** secure ripping. Only RubyRipper and EAC (in this thread) do. RubyRipper always rips the track twice and compares md5 checksums to ensure it is an accurate rip, and continues to rip the same song until the md5s match, or a correction can be made.

Using the SoundJuicer and Grip method does not guarantee anything but a slower rip, since it only attempts to correct the data once. Forget about an accurate rip if you have caching drive with these 2 softwares.

---

### Post by dasunst3r on 2008-01-19
What does it mean to rip music securely?

---

### Post by disturbed1 on 2008-01-19
Easiest to read this ;)
[http://wiki.hydrogenaudio.org/index.php?title=Secure_ripping](http://wiki.hydrogenaudio.org/index.php?title=Secure_ripping)

---

### Post by vanadium on 2008-01-19
There are two issues

1) How do you know if there has been an error in ripping a track? There is no logging facility.
2) Apparently no-one is able to create variable bitrate lames with soudjuicer. This is due to gstreamer. Ogg in fact is a better format, but fact is that any digital music player and most current DVD players play mp3, not ogg.

An additional problem is that cdparanoia is not anymore state-of-the-art, not anymore maintained and not adequate for drives that cache audio data (and most drives do nowadays)

I also would like to move away from any Windows application although wine works great.

---

### Post by disturbed1 on 2008-01-19
Here's the log from RubbyRipper from a badly scratched disc. The final result was perfect. I tried using Grip, and SoundJuicer, they didn't cut it, and either errored out, or produced skipping/clicking tracks.
```

This log is created by Rubyripper, version 0.4.4
Website: [http://code.google.com/p/rubyripper](http://code.google.com/p/rubyripper)

Cdrom player used to rip:
HP DVD Writer 1040d EH24
Cdrom offset used: 0

Ripper used: cdparanoia -Z
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-wav

CDDB INFO

Artist    = Grip Inc
Album    = Nemesis
Year    = 1997
Genre    = Metal
Tracks    = 11

01 - Pathetic Liar
02 - Portrait Of Henry
03 - Empress (Of Rancor)
04 - Descending Darkness
05 - War Between One
06 - Scream At The Sky
07 - Silent Stranger
08 - The Summoning
09 - Rusty Nail
10 - Myth Of Man
11 - Code Of Silence

STATUS

Starting to rip track 1, trial 1#
Starting to rip track 1, trial 2#
Analyzing files for mismatching chunks
1 chunk(s) didn't match 2 times.
Starting to rip track 1, trial 3#
Error(s) succesfully corrected, 2 matches found for each chunk 
MD5 sum: 6a0a1ddca7514b2a5af79e92e6a26efc

Starting to rip track 2, trial 1#
Starting to rip track 2, trial 2#
Analyzing files for mismatching chunks
3 chunk(s) didn't match 2 times.
Starting to rip track 2, trial 3#
Error(s) succesfully corrected, 2 matches found for each chunk 
MD5 sum: a9dd4847b867efd054a1ae5e119ddfda

Starting to rip track 3, trial 1#
Starting to rip track 3, trial 2#
Analyzing files for mismatching chunks
7 chunk(s) didn't match 2 times.
Starting to rip track 3, trial 3#
Error(s) succesfully corrected, 2 matches found for each chunk 
MD5 sum: ba05889045f78b0232dbff0a217d72d3

Starting to rip track 4, trial 1#
Starting to rip track 4, trial 2#
Analyzing files for mismatching chunks
3 chunk(s) didn't match 2 times.
Starting to rip track 4, trial 3#
Error(s) succesfully corrected, 2 matches found for each chunk 
MD5 sum: bdbda9b7a6e45bffed2fe91f67c6912d

Starting to rip track 5, trial 1#
Starting to rip track 5, trial 2#
Analyzing files for mismatching chunks
Every chunk matched 2 times 
MD5 sum: a9406134fd16d61ce85a303fc684df78

Starting to rip track 6, trial 1#
Starting to rip track 6, trial 2#
Analyzing files for mismatching chunks
19 chunk(s) didn't match 2 times.
Starting to rip track 6, trial 3#
2 chunk(s) didn't match 2 times.
Starting to rip track 6, trial 4#
Error(s) succesfully corrected, 2 matches found for each chunk 
MD5 sum: 370468354d49539600d845611a338455

Starting to rip track 7, trial 1#
Starting to rip track 7, trial 2#
Analyzing files for mismatching chunks
257 chunk(s) didn't match 2 times.
Starting to rip track 7, trial 3#
78 chunk(s) didn't match 2 times.
Starting to rip track 7, trial 4#
24 chunk(s) didn't match 2 times.
Starting to rip track 7, trial 5#
8 chunk(s) didn't match 2 times.
Starting to rip track 7, trial 6#
3 chunk(s) didn't match 2 times.
Starting to rip track 7, trial 7#
1 chunk(s) didn't match 2 times.
Starting to rip track 7, trial 8#
Error(s) succesfully corrected, 2 matches found for each chunk 
MD5 sum: 82b32311b4a5ea48811a6eef3f8bcaf3

Starting to rip track 8, trial 1#
Starting to rip track 8, trial 2#
Analyzing files for mismatching chunks
8 chunk(s) didn't match 2 times.
Starting to rip track 8, trial 3#
Error(s) succesfully corrected, 2 matches found for each chunk 
MD5 sum: 836cad3023792450039baa742f99082c

Starting to rip track 9, trial 1#
Starting to rip track 9, trial 2#
Analyzing files for mismatching chunks
Every chunk matched 2 times 
MD5 sum: 1ab7f432e25814f2b607665311eec7d7

Starting to rip track 10, trial 1#
Starting to rip track 10, trial 2#
Analyzing files for mismatching chunks
11 chunk(s) didn't match 2 times.
Starting to rip track 10, trial 3#
4 chunk(s) didn't match 2 times.
Starting to rip track 10, trial 4#
2 chunk(s) didn't match 2 times.
Starting to rip track 10, trial 5#
2 chunk(s) didn't match 2 times.
Starting to rip track 10, trial 6#
Error(s) succesfully corrected, 2 matches found for each chunk 
MD5 sum: f45f5c1df35e24ede5dc40d3070cc52d

Starting to rip track 11, trial 1#
Starting to rip track 11, trial 2#
Analyzing files for mismatching chunks
33 chunk(s) didn't match 2 times.
Starting to rip track 11, trial 3#
3 chunk(s) didn't match 2 times.
Starting to rip track 11, trial 4#
1 chunk(s) didn't match 2 times.
Starting to rip track 11, trial 5#
Error(s) succesfully corrected, 2 matches found for each chunk 
MD5 sum: fb170b33846c00fc31cd1cfa03d15458


RIPPING SUMMARY

All chunks were tried to match at least 2  times.
Some track(s) needed correction,but could
be corrected within the maximum amount of trials

SUSPICION POSITION ANALYSIS

Since there are more than 150 chunks per second, after making the notion of the
suspicion position, the amount of initially mismatched chunks for that position is shown.

TRACK 1
    Suspicion position : 00:50 (1x) (CORRECTED at trial 3
TRACK 2
    Suspicion position : 01:18 (2x) (CORRECTED at trial 3
    Suspicion position : 01:26 (1x) (CORRECTED at trial 3
TRACK 3
    Suspicion position : 00:01 (1x) (CORRECTED at trial 3
    Suspicion position : 00:02 (3x) (CORRECTED at trial 3
    Suspicion position : 00:15 (2x) (CORRECTED at trial 3
    Suspicion position : 02:45 (1x) (CORRECTED at trial 3
TRACK 4
    Suspicion position : 00:02 (1x) (CORRECTED at trial 3
    Suspicion position : 00:04 (2x) (CORRECTED at trial 3
TRACK 6
    Suspicion position : 03:42 (1x) (CORRECTED at trial 3
    Suspicion position : 03:43 (1x) (CORRECTED at trial 3
    Suspicion position : 04:24 (2x) (CORRECTED at trial 4
    Suspicion position : 04:25 (1x) (CORRECTED at trial 3
    Suspicion position : 04:38 (1x) (CORRECTED at trial 3
    Suspicion position : 04:41 (1x) (CORRECTED at trial 3
    Suspicion position : 04:42 (2x) (CORRECTED at trial 3
    Suspicion position : 04:43 (3x) (CORRECTED at trial 3
    Suspicion position : 04:44 (1x) (CORRECTED at trial 3
    Suspicion position : 04:45 (2x) (CORRECTED at trial 3
    Suspicion position : 04:46 (4x) (CORRECTED at trial 3
TRACK 7
    Suspicion position : 00:02 (3x) (CORRECTED at trial 3
    Suspicion position : 00:03 (1x) (CORRECTED at trial 3
    Suspicion position : 00:04 (2x) (CORRECTED at trial 3
    Suspicion position : 00:05 (3x) (CORRECTED at trial 5
    Suspicion position : 00:06 (1x) (CORRECTED at trial 3
    Suspicion position : 00:07 (5x) (CORRECTED at trial 3
    Suspicion position : 00:08 (2x) (CORRECTED at trial 4
    Suspicion position : 00:09 (2x) (CORRECTED at trial 3
    Suspicion position : 00:10 (1x) (CORRECTED at trial 4
    Suspicion position : 00:15 (2x) (CORRECTED at trial 3
    Suspicion position : 00:16 (3x) (CORRECTED at trial 5
    Suspicion position : 00:17 (5x) (CORRECTED at trial 5
    Suspicion position : 00:18 (1x) (CORRECTED at trial 5
    Suspicion position : 00:20 (1x) (CORRECTED at trial 3
    Suspicion position : 00:21 (1x) (CORRECTED at trial 3
    Suspicion position : 00:22 (3x) (CORRECTED at trial 3
    Suspicion position : 00:23 (4x) (CORRECTED at trial 3
    Suspicion position : 00:24 (1x) (CORRECTED at trial 3
    Suspicion position : 00:25 (2x) (CORRECTED at trial 3
    Suspicion position : 00:26 (1x) (CORRECTED at trial 3
    Suspicion position : 00:27 (3x) (CORRECTED at trial 7
    Suspicion position : 00:29 (2x) (CORRECTED at trial 3
    Suspicion position : 00:30 (2x) (CORRECTED at trial 3
    Suspicion position : 00:31 (2x) (CORRECTED at trial 3
    Suspicion position : 00:32 (1x) (CORRECTED at trial 3
    Suspicion position : 00:33 (1x) (CORRECTED at trial 3
    Suspicion position : 00:34 (5x) (CORRECTED at trial 5
    Suspicion position : 00:35 (2x) (CORRECTED at trial 3
    Suspicion position : 00:36 (3x) (CORRECTED at trial 4
    Suspicion position : 00:37 (3x) (CORRECTED at trial 4
    Suspicion position : 00:38 (3x) (CORRECTED at trial 8
    Suspicion position : 00:39 (4x) (CORRECTED at trial 4
    Suspicion position : 00:40 (2x) (CORRECTED at trial 3
    Suspicion position : 00:41 (1x) (CORRECTED at trial 3
    Suspicion position : 00:42 (4x) (CORRECTED at trial 3
    Suspicion position : 00:43 (5x) (CORRECTED at trial 4
    Suspicion position : 00:44 (6x) (CORRECTED at trial 4
    Suspicion position : 00:45 (5x) (CORRECTED at trial 4
    Suspicion position : 00:46 (2x) (CORRECTED at trial 3
    Suspicion position : 00:47 (5x) (CORRECTED at trial 4
    Suspicion position : 00:48 (4x) (CORRECTED at trial 4
    Suspicion position : 00:49 (3x) (CORRECTED at trial 4
    Suspicion position : 00:50 (3x) (CORRECTED at trial 4
    Suspicion position : 00:51 (3x) (CORRECTED at trial 3
    Suspicion position : 00:52 (3x) (CORRECTED at trial 3
    Suspicion position : 00:53 (4x) (CORRECTED at trial 4
    Suspicion position : 00:54 (2x) (CORRECTED at trial 4
    Suspicion position : 00:55 (1x) (CORRECTED at trial 3
    Suspicion position : 00:56 (3x) (CORRECTED at trial 4
    Suspicion position : 00:57 (5x) (CORRECTED at trial 3
    Suspicion position : 00:58 (1x) (CORRECTED at trial 3
    Suspicion position : 00:59 (2x) (CORRECTED at trial 3
    Suspicion position : 01:01 (4x) (CORRECTED at trial 4
    Suspicion position : 01:02 (4x) (CORRECTED at trial 3
    Suspicion position : 01:03 (4x) (CORRECTED at trial 5
    Suspicion position : 01:04 (1x) (CORRECTED at trial 3
    Suspicion position : 01:05 (6x) (CORRECTED at trial 4
    Suspicion position : 01:06 (5x) (CORRECTED at trial 4
    Suspicion position : 01:07 (4x) (CORRECTED at trial 3
    Suspicion position : 01:08 (2x) (CORRECTED at trial 3
    Suspicion position : 01:09 (2x) (CORRECTED at trial 4
    Suspicion position : 01:10 (6x) (CORRECTED at trial 3
    Suspicion position : 01:11 (3x) (CORRECTED at trial 4
    Suspicion position : 01:12 (1x) (CORRECTED at trial 3
    Suspicion position : 01:13 (3x) (CORRECTED at trial 3
    Suspicion position : 01:14 (3x) (CORRECTED at trial 3
    Suspicion position : 01:15 (2x) (CORRECTED at trial 3
    Suspicion position : 01:16 (3x) (CORRECTED at trial 4
    Suspicion position : 01:17 (4x) (CORRECTED at trial 4
    Suspicion position : 01:18 (6x) (CORRECTED at trial 6
    Suspicion position : 01:19 (4x) (CORRECTED at trial 6
    Suspicion position : 01:20 (3x) (CORRECTED at trial 5
    Suspicion position : 01:21 (4x) (CORRECTED at trial 5
    Suspicion position : 01:22 (3x) (CORRECTED at trial 5
    Suspicion position : 01:23 (5x) (CORRECTED at trial 5
    Suspicion position : 01:24 (3x) (CORRECTED at trial 5
    Suspicion position : 01:25 (2x) (CORRECTED at trial 5
    Suspicion position : 01:26 (7x) (CORRECTED at trial 7
    Suspicion position : 01:27 (2x) (CORRECTED at trial 6
    Suspicion position : 01:28 (3x) (CORRECTED at trial 5
    Suspicion position : 01:29 (1x) (CORRECTED at trial 3
    Suspicion position : 01:30 (3x) (CORRECTED at trial 4
    Suspicion position : 01:31 (3x) (CORRECTED at trial 3
    Suspicion position : 01:33 (2x) (CORRECTED at trial 3
    Suspicion position : 01:34 (2x) (CORRECTED at trial 3
    Suspicion position : 01:35 (2x) (CORRECTED at trial 4
    Suspicion position : 01:36 (3x) (CORRECTED at trial 3
    Suspicion position : 01:38 (1x) (CORRECTED at trial 3
    Suspicion position : 01:39 (1x) (CORRECTED at trial 3
    Suspicion position : 01:40 (1x) (CORRECTED at trial 3
TRACK 8
    Suspicion position : 01:05 (1x) (CORRECTED at trial 3
    Suspicion position : 01:13 (2x) (CORRECTED at trial 3
    Suspicion position : 02:28 (1x) (CORRECTED at trial 3
    Suspicion position : 02:29 (1x) (CORRECTED at trial 3
    Suspicion position : 02:30 (1x) (CORRECTED at trial 3
    Suspicion position : 02:31 (2x) (CORRECTED at trial 3
TRACK 10
    Suspicion position : 02:00 (1x) (CORRECTED at trial 3
    Suspicion position : 02:37 (3x) (CORRECTED at trial 4
    Suspicion position : 02:39 (2x) (CORRECTED at trial 6
    Suspicion position : 02:44 (1x) (CORRECTED at trial 3
    Suspicion position : 02:46 (2x) (CORRECTED at trial 3
    Suspicion position : 03:21 (1x) (CORRECTED at trial 3
    Suspicion position : 03:25 (1x) (CORRECTED at trial 3
TRACK 11
    Suspicion position : 04:33 (2x) (CORRECTED at trial 3
    Suspicion position : 04:40 (1x) (CORRECTED at trial 3
    Suspicion position : 04:41 (3x) (CORRECTED at trial 3
    Suspicion position : 04:44 (2x) (CORRECTED at trial 3
    Suspicion position : 04:45 (1x) (CORRECTED at trial 3
    Suspicion position : 04:47 (1x) (CORRECTED at trial 3
    Suspicion position : 04:56 (4x) (CORRECTED at trial 5
    Suspicion position : 05:01 (3x) (CORRECTED at trial 3
    Suspicion position : 05:02 (2x) (CORRECTED at trial 3
    Suspicion position : 05:03 (1x) (CORRECTED at trial 3
    Suspicion position : 05:04 (2x) (CORRECTED at trial 3
    Suspicion position : 05:05 (2x) (CORRECTED at trial 3
    Suspicion position : 05:07 (2x) (CORRECTED at trial 3
    Suspicion position : 05:09 (1x) (CORRECTED at trial 3
    Suspicion position : 05:10 (2x) (CORRECTED at trial 3
    Suspicion position : 05:11 (2x) (CORRECTED at trial 3
    Suspicion position : 05:25 (2x) (CORRECTED at trial 3
```

---

### Post by mekkah on 2008-01-19
> **vanadium said:**
> There are two issues

1) How do you know if there has been an error in ripping a track? There is no logging facility.
2) Apparently no-one is able to create variable bitrate lames with soudjuicer. This is due to gstreamer. Ogg in fact is a better format, but fact is that any digital music player and most current DVD players play mp3, not ogg.

An additional problem is that cdparanoia is not anymore state-of-the-art, not anymore maintained and not adequate for drives that cache audio data (and most drives do nowadays)

I also would like to move away from any Windows application although wine works great.

1. Like u said: you can't, since there's no logging. CDParanoia is the best solution for ripping under Linux so far. Take it or leave it. I also miss the LOG feature of EAC. But until there's a stable version of RubyRipper. This is what i'm gonna use. Besides, i haven't encountered a single bad rip yet. I just wanted to show that you don't have to use GRIP (which is actually older than CDP) to make quality rips.

2. Rip the CD into WAV or FLAC and then use SoundConverter to encode it into MP3's.

Linux lacks good audio tools. But that's because most people dealing with Linux put their effort into other things. I used to be an straight-edge-audiophile, but since i moved to Ubuntu, i learned that i have to compromise a bit in order to get along with the system. Ripping without EAC is one thing you have to live without. People *** fast to complain, but no one wants to put the effort & time into developing those missing apps....

---

### Post by disturbed1 on 2008-01-19
> **mekkah said:**
> 

2. Rip the CD into WAV or FLAC and then use SoundConverter to encode it into MP3's.


You do know SoundConverter is a GStreamer app? It too suffers from the same 160kb limit Lame VBR bug as all GStreamer apps do.


For the most part SoundJuicer does the job, except when a secure rip is needed. You can also edit the GStreamer profiles and change the oggenc level to something higher or lower. To get the commands run  gst-inspect-0.10 *codec*

---

### Post by OoooMatron on 2008-01-20
Any new rips by me are all converted to Ogg level 7 and playback using Rockbox on my audio player.

I also agree that audio apps across the board are very weak compared to Windows and there isn't a single application to either rip or playback audio that works 100% without any kind of problem. The closest I seem to have come to decent audio playback is with Totem, VLC and Audacious but even those have their misgivings or lack of features.

VLC and Audacious run in multiple instances which is quite annoying and neither app seem to cache the id information in the playlist for streamed audio. Audacious also moves onto the next track while playing back streamed music. VLC cannot be made to play in the same instance anymore (if it ever could).

Amarok is ok but it's KDE and is prone to crashing and since using Gnump server I don't really feel the need for an application that contains a library but it is the closest yet to a decent music suite.

XMMS looks totally rubbish in this day and age and applications like Rhythm Box either are too basic or don't do streaming properly.

Ripping and burning is also poor because they are based on are extremely dated applications. EAC works faster (for my dvd drive) by 2-3 times under Wine than the Linux counterparts.

At least Nero Linux has come and made a decent attempt at some burning software. Nero also burns much faster than any of the linux software for my dvd drive.

I do realise that some people rip and burn equally fast in Linux/Windows but it is still a problem that many drives fail to burn faster than 4x.

Hopefully, in the future some new programs will come into the fray and set these issues behind us once and for all but these programs will need new libraries, not just better guis for the old ones.

---

### Post by vanadium on 2008-01-20
> Ripping without EAC is one thing you have to live without.
It runs perfectly on Wine for me, at least as well as under venerable Windows.

> CDParanoia is the best solution for ripping under Linux so far. Take it or leave it. 
Not correct in my opinion. Rubyripper, although relying  on cdparanoia to extract the audio, takes it one step further to make audio extraction more secure.

---

