---
title: "MP3 Trouble on Sansa e260 when ripped in Ububtu"
date: 2010-08-24
forum: Multimedia Software
---

### Post by John Peschken on 2010-08-24
I have a Sansa e260 (4GB).  It's a few years old.  I believe it's an early version.  According to the manual, it understands only WMA and MP3 files.  It has the latest firmware available for it.

When I rip MP3's for it on my Windows Machine, everything works fine.  When I rip them on my Ubuntu machine, the Sansa can't figure out what the artist, album, or even the song title are.  It knows only the file name.  Everything just shows up in the song list as "1. Song Title.mp3"  etc.  Album, Artist, and Genre are "Unknown".

I have tried ripping with both Banshee and Sound Juicer.  Sound Juicer offers only one mp3 option.  with the following gstreamer line. 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

I know enough about gstreamer to know this is doing a variable bit rate mp3, but that's about all.  Banshee offers more understandable (for me) choices, but I don't see where I can get a look at the gstreamer parameters (I imagine it's also using gstreamer).  Banshee offers "Preset", "Average", "Constant", and "Variable"  for "VBR" modes and a sliding bitrate scale.  I have tried all of these except "Preset", all set at 128 Kbps. 

I gather from other things I have read in these forums that there are different versions of headers (or whatever the place where album, artist, and such info is stored is called) in MP3 files.  I wonder if my old Sansa might not understand the newer headers?  I really have no idea.  I'm counting on the experts here.  

It apparently makes no difference how I put the music on the Sansa.  I can rip to MP3s and sync it  via Banshee or just copy the files to the "music" folder on the Sansa.   I can rip to a FLAC, and let Banshee convert to MP3 and sync.  It seems to make no difference how the file gets on the Sansa.  For what it's worth, I can make a disk with these MP3's and my 2008 Honda's CD player understands them just fine.  It knows who the album,  artist,  etc. are.  

So, it's fairly clear it is the Sansa that is not understanding the header information in the MP3 files coming off the Ubuntu machine.  It understands the MP3's created by Windows Media Player just fine, but I _really_ want to move away from Windows.

Ideas Please?

Additional Note: 8/25/20 - I went ahead and bought Nero for Linux.  That creates MP3's the Sansa can relate to.  That seems to again point to a flaw in the MP3 files generated via gstreamer.  So, I have a work-around, but it would be more convenient to use Banshee or Sound Juicer to make MP3's.  Nero is awkward to use, so I would still like to find an answer in the free software if that's possible.

---

### Post by John Peschken on 2010-08-30
I have been searching around the various forums and the intenet in general. 
I gather that my problem is probably the id3 parameter, but honestly, there's a lot I am reading that is way over my head.  I am already using the id3v2mux parameter.  I tried substituting an id3v1mux thinking maybe I needed the older version, but that does not seem to have made a difference.  Oh, the fun of a new OS!

---

### Post by gordintoronto on 2010-08-31
I found a parameter "prefer-v1" but I couldn't figure out where it should go! (Murky docs!)  I'm pretty sure it's what you need.

---

### Post by John Peschken on 2010-08-31
I'll put that idea off to the side for now.  My frustration level with Ubuntu has hit 11 onthe 1-10 tear-your-hair-out o-meter.  That machine is in the drawer for now.  I resisted the urge to reinstall WinXP for now, but I had to walk away.  MP3's are my only beef with Ubuntu.  I know it's not the developers fault that MP3's are patented, but that doesn't make it any easier to deal with them.
 
I had not come across your parameter.  It seems like it has promise.  I'll try that the next time I decide to pickit up.

---

### Post by tommcd on 2010-08-31
John,
Your thread is now marked "Solved". I am curious to know how you solved it. Could you post the solution here please?
Your solution may help others with similar problems.

---

### Post by Chronon on 2010-09-01
I am able to tag all of my media using EasyTAG and Picard.  

Also, you could avoid these tagging problems by using Rockbox, which allows you to browse music with a file browser rather than a database of metadata tags like the original firmware.  (It also has many other benefits.)

---

### Post by John Peschken on 2010-09-01
Sorry to say I "solved" it by putting my Ubuntu laptop in the closet.   I also find leaving threads open after a couple people have offered a solution I start to get complaints from people who think the thread should be closed, so I closed it.
 
I think probably the suggestion from "gordintoronto" above is what I was looking for.  That does not solve the problem where exactly to _put_ that parameter, but thought I could figure that out by trial and error and research.  More hassles.
 
The truth is, I am just worn down by all the MP3 ripping difficulties in Ubuntu, and by waiting for the incredibly slow ripping compared to what I am used to in Windows.  I considered buying a new player that could deal with OGG files, but suddenly my free OS was going to cost me $70 - 100.   And with about 100 CD's to slowly rip, I just gave in at about 20.  So, for now I have retreated to the relatively uncomplicated world of Windows.
 
I will get back to it one day, I hope.

---

### Post by John Peschken on 2010-09-01
> **Chronon said:**
> I am able to tag all of my media using EasyTAG and Picard. 
 
Also, you could avoid these tagging problems by using Rockbox, which allows you to browse music with a file browser rather than a database of metadata tags like the original firmware. (It also has many other benefits.)
No thanks! Putting a new OS on my media player is not what I need while I'm tearing my hair out over Ubuntu. Maybe some day. 
 
As for re-tagging everythiing with Picard or Easytag or such like, I imagine that is a file-at-a time proposition. Is that correct? I do not want to do that with about 100 CD's X about 13 tracks each = 1300 files. Not my idea of fun.

---

### Post by Zimmer on 2010-09-01
GRIP was the one I used most before the advent of Banshee. 
In fact, I do not think I have tried a Banshee ripped mp3 on my player .. will have to investigate now I have read this thread.

---

### Post by John Peschken on 2010-09-01
GRIP seems to have some promise.  I'll have to try that when I get back to my Linux box.  If I understand correclty it uses something called CD paranoia to do the work rather than gstreamer.  I also found documentation I think I understand at nostatic.org.  Everything I could find on gstreamer was either vague or way over my head on the topic of the various options.  When I tried to mess with the gstreamer options things always went downhiill fast.

---

### Post by John Peschken on 2010-09-01
I'm beginning to think about this from a different angle.  It occurs to me that the root of my troubles is that my Sansa e260 apparently does not get along with the MP3's gstreamer puts out.  
 
However, I see that Rockbox can be installed with the help of a nice installer.  That is much more promising than the somehwat arcane directions I had seen earlier.  Rockbox allows the Sansa to play Vorbis/OGG files, which I hear are superior to MP3 anyway.  What could go wrong?  <grin>.   
 
My hope and prayer is that the OGG format files ripped in Ubuntu will work correctly on the Sansa.  I would love dearly to kick MP3 to the curb.  Is anyone here ripping OGG files in Ubuntu and running them on Rockbox?  Does it all work correctly?  My fear is I'll have two devices where I'm trying to sort out the OS instead of just one.

---

### Post by tommcd on 2010-09-01
> **John Peschken said:**
> 
The truth is, I am just worn down by all the MP3 ripping difficulties in Ubuntu, and by waiting for the incredibly slow ripping compared to what I am used to in Windows.
I use the **asunder** program to rip CDs to my computer. It is fast and light and rips the CDs fast enough for me. I have not ripped a CD on Windows in a very long time, so I can not offer a comparison to Windows.
> **John Peschken said:**
> 
  I considered buying a new player that could deal with OGG files, but suddenly my free OS was going to cost me $70 - 100.   And with about 100 CD's to slowly rip, I just gave in at about 20.  So, for now I have retreated to the relatively uncomplicated world of Windows.
 
I assume you have installed the restricted formats packages and medibuntu codecs:
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
You are able to play mp3 music files on Ubuntu; is that correct?

If you do decide to buy new mp3 player, I recommend the Sandisk Sansa Fuse:
[http://www.sandisk.com/products/sansa-music-and-video-players/sandisk-sansa-fuze](http://www.sandisk.com/products/sansa-music-and-video-players/sandisk-sansa-fuze)
They even state that they support linux (way down at the bottom of the page). I have a 4GB Fuse and it works just fine in Ubuntu, Slackware, and Salix.

EDIT: I posted this before I saw your last post John.
Anyway, that Rockbox does look interesting.

---

### Post by tommcd on 2010-09-01
Stupid double post somehow ... sorry!

---

### Post by John Peschken on 2010-09-01
Well, it's a backwards solution, but it IS a solution!

I installed Rockbox on my Sansa.  It went without a hitch.  It is more complicated than the stock firmware, but it is capable of much more, so that's to be expected.  There will be learning curve, but it looks reasonable so far.  Time to read the manual.

This will allow me to load the thing with Vorbis OGG or FLAC files, and avoid the entire MP3 problem.  In the meantime, the Ubuntu generated MP3's that the Sansa could not understand work correctly with Rockbox installed.  

Hooray!

---

### Post by Zimmer on 2010-09-02
GRIP options... I found this in my 'helpfiles' folder..

rip file format
~/mp3/%A/%d/%n.wav
endcode command line
-h -b %b %w %m
endcode file format
~/mp3/%A/%d/%n.%x


for ogg
rip format
~/ogg/%A/%d/%n.wav

might be of use to you..

Please note that I am led to believe GRIP is no longer being developed..

---

### Post by Chronon on 2010-09-09
> **John Peschken said:**
>  
As for re-tagging everythiing with Picard or Easytag or such like, I imagine that is a file-at-a time proposition. Is that correct? I do not want to do that with about 100 CD's X about 13 tracks each = 1300 files. Not my idea of fun.

No.  Both will do your entire library at one go.

---

### Post by Chronon on 2010-09-09
> **John Peschken said:**
> Is anyone here ripping OGG files in Ubuntu and running them on Rockbox?  Does it all work correctly?  My fear is I'll have two devices where I'm trying to sort out the OS instead of just one.

Yes, I do this frequently with no problems (with FLAC too).

---

### Post by John Peschken on 2010-09-09
I do have the restricted formats installed.  The trouble was that the Sansa e260 did not seem to understand the headers being generated.  Since my car and the Sansa with Rockbox installed both understood the headers just fine, I hang the problem on the stock Sansa firmware.  Not saying it's "bad", just incompatible with the Ubuntu MP3's for some reason I never did pin down.
 
The Sansa Fuse you suggest was what I was considering going to, but now that I have Rockbox on the e260 and it play's OGG's I don't need to get a new player.  Maybe a bigger SD for the e260 is in order, but the e260 does everything I need now.

---

### Post by Chronon on 2010-09-09
By the way, with Rockbox the e260 can use microSDHC cards (up to 32GB, currently).

---

