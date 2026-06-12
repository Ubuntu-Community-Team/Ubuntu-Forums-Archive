---
title: "Weird problem using cat *.mp3 command"
date: 2009-08-15
forum: Multimedia Software
---

### Post by Bartender on 2009-08-15
Here I was, feeling all cocky about using the command line for once...
Just ripped a 14 CD audiobook to mp3 using Sound Juicer.  Made new folders for the output of each CD, then cd'ed to each folder and used the cat command picked up on the forums
```
cat *.mp3 > *filename*.mp3
```
to merge all .mp3's into a new file inside the original folder.

I did this with all 14 folders.

Thought I'd listen to the first rip for a few minutes.  There was no introduction.  Took me a few minutes to figure out that the merged file started at track #10.  In all 14 folders, the cat command ignored tracks 1 thru 9.

Has anyone ever seen this before?  I just ripped CD #1 and tried again - same results.

EDIT:  Just went back and checked a few dozen rips from other audiobooks - all of them were OK.  The merged file included all tracks.

---

### Post by mc4man on 2009-08-15
Are your 1-9  mp3's zero padded, in other words, 01, 02, 03, ect.? If not do so

---

### Post by Bartender on 2009-08-16
No, they weren't.  SoundJuicer labeled them as Track 1.mp3, etc.

I figured that the numbering, and perhaps that space between Track and #, might have something to do with the way the .mp3's were recognized.

So I ripped the first of the 14 CD's using RipperX.  RX labeled them as -track1.mp3, etc.  I thought, "OK, no spaces, now we're cookin' with gas".  Ran the "cat *.mp3 > *newfilename*.mp3" command, and was surprised to find the exact same results - track1 thru track9 were skipped over.

It seems to me this is chasing down the wrong path, because Sound Juicer and the cat *.mp3 command worked fine in the half dozen previous audiobook rips.  Sound Juicer had labeled all of those as "Track 1" etc. with the spaces.

In other words, I can't see any obvious difference between the half dozen audiobooks that I ripped with Sound Juicer and concatenated successfully, and this latest audiobook that did not concatenate successfully.

I can still toss the folders onto my wife's Fuze with the six thousand separate tracks, and that will work well enough, but I'd like to understand why the first nine tracks were skipped.

I'll try what you suggest and report back.

---

### Post by mc4man on 2009-08-16
I use rubyripper which with the default naming uses 01 - trackname.mp3 ect (also has an option to rip to a single mp3

Would seem odd if the files are being skipped rather than placed in wrong 'order' ( does the size reflect they're actually being skipped?

In ripperx you could just use %# in the naming (config -> files

That would result in 01.mp3, 02.mp3 ect.

---

### Post by kaibob on 2009-08-16
Bash does not always sort files in the order you would expect, and, like mc4man, I wonder if the tracks are out of order rather than missing.

For example, I created 30 mp3 files named 1.mp3 to 30.mp3 and then ran the ls -l command in a terminal window. The first displayed files were 10.mp3 to 19.mp3 followed by 1.mp3 followed by 20.mp3 to 29.mp3 and so on. This would vary depending on the locale setting. Also, padding the numbers with a zero would also change this. 

I don't understand why things worked for you before, and, if the tracks are actually missing, why that would be the case, so perhaps something else is going on.

---

### Post by Bartender on 2009-08-16
> **kaibob said:**
> I don't understand why things worked for you before, and, if the tracks are actually missing, why that would be the case, so perhaps something else is going on.

Right, that's the weird part.  You both have a point that I did not consider.  Tracks 1 thru 9 may just be out of sequence.

But why were the first half dozen audiobooks concatenated in the proper sequence?  

I downloaded rubyripper a few days ago but have not tried to figure it out yet.  Ruby can be instructed to rip to a single .mp3?  That would be great!  Is that point-and-click, or do you change one of those strings of commands?  I don't understand those strings yet :confused:

---

### Post by Bartender on 2009-08-27
Rubyripper by default numbers the first tracks 01 - 09, and the cat command worked.
In Sound Juicer, if I manually changed 1 - 9 to 01 - 09 the cat command worked.

I screwed around with the Sound Juicer Preferences, changing the titling options from original.  If I knew what the original settings were I'd go back and try those.

Rubyripper is much slower than Sound Juicer, but I kind of like the way it samples at least twice.  Trying to rip some scratchy audiobook CD's, Rubyripper re-sampled several tracks until it was happy.  In one case, it resampled until it gave up and moved on, but the track sounds OK to me.

My wife is going to try out some Rubyripper outputs without concatenating the .mp3's.  The pause between tracks is only a second or so, which she doesn't find annoying.  We're both thinking that leaving the individual tracks intact might make it easier for her to keep track of where she was if she pushes the wrong button and loses her place.  

Because of the way Ruby numbers the tracks by default, the Fuze plays them in the right order.  Sometimes when I brought an audiobook CD over to the Fuze without concatenating, the Fuze dropped 1 - 9 to the bottom of the list and started playing from track 10.

---

