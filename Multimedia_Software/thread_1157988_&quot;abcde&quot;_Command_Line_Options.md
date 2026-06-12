---
title: "&quot;abcde&quot; Command Line Options"
date: 2009-05-13
forum: Multimedia Software
---

### Post by TunaCanTommy on 2009-05-13
I primarily rip audiobooks from CDs I take out from the library - to either MP3 or Ogg, haven't decided yet. I have different .conf files for each.
I put the files on a SanDisk Sansa 4GB Clip . .  it handles MP3, Ogg, and FLAC.  Also has a very nice bookmark feature for files tagged GENRE=Audiobook.
I like to put an entire CD, about 30-tracks, into one file. I use the "-1" option to do that - no problem.
What I'm fooling around with now is how to put a title on the command line as an option.
If I set the following options on the abcde command line - "-1nNW1" I get:
-1 - rip to one file
n -  no CDDB query (usually audiobooks aren't out there,)
N - no user intervention ( gives me Unknow Artist / Unknow Album )
W1 - use disc notation as "Disc01" and include the disc info in the track number; ie: 101, 102, 103 . . .
W2 - I get 201, 202, 203

But when I use W2 for the second disc, the first disk gets over-written because both are "Unknown Artist / Unknown Album/Unknown Title"  . . .  the same title!

The "W2" option doesn't do anything for the title, just the tags.

What I've been doing is not using the "-N" option and I edit the CDDB information for Artist, Album and Title. 

After all the CDs are ripped I "batch-edit" the ID3v2 tags for the book to tidy up all the files.  I use "Audio Tag Tool" making sure they're right for use in my Sansa CLIP.

If I could put ID3v2 tag information in the command line for DTITLE, ie; DTITLE=Disc02, I could use the "-N" option all I'd have to do is, use the right .conf file and make a small change on the command line for each disc I rip, take the "Unknow Artist / Unknow Album" and make the changes when I edit the ID3v2 tags. I'd like a way to make a "unique" title, at the command line, for each CD as it is ripped - preferably without editing the CDDB info each time.

I know I could just rename each file after it is ripped/tagged while the next CD is being ripped . . . plenty of time for that when a CD is ripped as one-file and before the tagging process begins.

Any ideas for me ? ?

---

### Post by andrew.46 on 2009-05-14
Hi TunaCanTommy,

The more I think about this the more I suspect that abcde is perhaps not the right tool for this job. Have you considered writing your own simple script to accomplish this? 

It is a great pity that abcde is no longer being developed so advice cannot be sought from a developer, or modifications introduced into the script itself to make this task a little easier.

All the best,

Andrew

---

### Post by TunaCanTommy on 2009-05-14
Andrew:

I expect you're right . . . it was just a little puzzle to ponder.

Tom

---

### Post by paxmark1 on 2009-05-19
Maybe elsewehere would be better.  But this one is recent.  I am really liking abcde a lot.  I used to use ripit.  

However, when there are "multiple exact entires"  (of genre), it prints the various listings, as 1   2     3    and then there is a highlighted "end"  I input various permutations to try to get it to accept anyone of the options and it returns to the highlighted "end"   Read man, googled,  any ideas

---

### Post by andrew.46 on 2009-05-19
Hi paxmark1,

> **paxmark1 said:**
> [...] when there are "multiple exact entires"  (of genre), it prints the various listings, as 1   2     3    and then there is a highlighted "end"  I input various permutations to try to get it to accept anyone of the options and it returns to the highlighted "end"   Read man, googled,  any ideas

When you have scrolled down the entries and reached 'end' simply press the key 'q' and you will return to the main screen to make our choice:

```

andrew@skamandros~$ abcde
Executing customizable pre-read function... done.
Getting CD track info... Querying the CD for audio tracks...
Grabbing entire CD - tracks: 01 02 03 04 05 06 07 08 09
Checking CDDB server status...
Querying the CDDB server...
Obtaining CDDB results...
Retrieving multiple matches... done.
**[COLOR="Red"]Which entry would you like abcde to use (0 for none)? [0-6]: [/COLOR]**

```

Select the number that you want and of you go :-).

Andrew

---

