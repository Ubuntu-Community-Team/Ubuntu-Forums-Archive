---
title: "Fixing Joined Mp3s"
date: 2009-10-28
forum: Multimedia Software
---

### Post by themindfantastic on 2009-10-28
I read an older thread from over a year ago about joining MP3s and it put out an easy way to do it, which I have been using.  ```
Cat 01.mp3 02.mp3 > New.mp3 
``` But the problem is the resulting file sometimes is messed up.  For example lets say 01.mp3 is 5 mins and 02.mp3 is 3 mins, the resulting combined file should be 8 mins.  Sometimes it will say its only 5 mins long, what the first file was originally, though it has 8 mins of mp3 data in the file, and this means some players will actually stop playing the file after 5 mins.  When you have joined an audiobook with 3 min tracks into one long mega file that should be 5 hours long to find your can only listen to the first 3 mins of it, can be pretty annoying.

I have taken to moving them into Audacity and literally just resaving the file, but this requires a good 15 mins to load some of these long mega mp3 files, when really its not the data so much but something in the header which could be rewritten.  Again there is nothing wrong with the MP3 data itself, just the fact the basic information the Mp3 seems to have about itself is sometimes fixed and needs to be adjusted so it can recognize the the new data that is there.

Is there an easier way?  If there is an MP3 fix utility or something or even just a program that can join MP3s and rewrite the headers, anything to get something that works all the time.

---

### Post by vinutux on 2009-10-28
install ogmtools 

```
sudo apt-get install ogmtools
```

and paly with omgmerge ```
ogmmerge [global options] -o out [options] <file1> [[options] <file2> ...]  
```

Here is help : **[http://manpages.ubuntu.com/manpages/intrepid/man1/ogmmerge.1.html]("http://manpages.ubuntu.com/manpages/intrepid/man1/ogmmerge.1.html")**

---

### Post by Jose Catre-Vandis on 2009-10-28
Using cat to join mp3s means that the resultant file uses the first files ID3 tag.

There doesn't seem to be any easy way of doing this, short of decoding to pcm/wav and then re-encoding (e.g. using Audacity)

---

### Post by themindfantastic on 2009-10-30
I've played around with ogmmerge, and I've tried it or 'joining' which I believe the resulting file actually just was a merged overlapping crapfest which various players ran into the corner and cried to their mommy from just looking at it.  I then figured well if I could just get it to fix the resulting 'cat' file, and that too seemed to not do anything that resulted in a file that played anything.  Granted I am just not applying the right switches or something for it, but the man page pushes the fact its for merging audio and video together not so much rewriting audio headers.  But if I figure it out it might work.

I know that Cat tends to keep the ID3 tag of the first and I had originally hoped (prior to writing the message above and looking for anything that might fix things) simply rewriting the ID3 tag might fix the issue, but it didn't seem to.  So I might be stuck trying to do it the hard way.  Im thinking I might get away with 'sound converter' simply converting it to the same settings it already has, doing a great deal of CPU chunking for a short analysis and writing a simple header.  Too bad I know little about programming because I think if anything a small program that would address fixing MP3 headers to match how many frames it really has would be a useful albeit very niche sort of utility.

---

### Post by Jose Catre-Vandis on 2009-11-03
Found a partial solution (if you are preapred to use wine, but at least it is freeware and gpl.

mp3packer

This will take your concatenated files and rewrite frame by frame. It retains the header of the first file but sorts out the bitrate and time.

Download here:
```
http://omion.dyndns.org/mp3packer/mp3packer-1.20.rar
```

Unrar the archive and then in a terminal run:
```
wine mp3packer input.mp3 output.mp3
```

Full instructions in the help html in the archive. Note I already had wine and perl installed.

---

### Post by themindfantastic on 2009-11-03
Now THIS is almost exactly what I was looking for actually.  Yes it has to be routed through Wine, but hey better than nothing (being GPLd I might figure out how to compile it natively, bot that I have much experience in such things) Thank you for the find.

---

