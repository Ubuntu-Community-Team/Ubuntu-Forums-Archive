---
title: "Remove duplicate songs from mp3 collection?"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by sshetye on 2007-06-07
HI folks,

I've noticed that I've got several duplicate songs in my collection. Could be because I was experimenting various players when I moved to Ubuntu from XP. Anyway, I was wondering if there is a known method of finding and deleting duplicates in Ubuntu (any app!).

I did search and found the following
1) [http://ubuntuforums.org/showthread.php?t=231158](http://ubuntuforums.org/showthread.php?t=231158)
This appears to detect "duplicates" based off file name. My file names are different (eg. "Artist **_[COLOR="Red"]-[/COLOR]_** song name.mp3"  vs "Artist**_ [COLOR="Red"]:[/COLOR]_** song name.mp3")

2) [http://ubuntuforums.org/showthread.php?t=435297](http://ubuntuforums.org/showthread.php?t=435297)
Talks of making a single large playlist of all songs. This doesn't work for me in Amarok 1.4.5

I'm not sure if any of those options detects duplicates based off ID3 tags. I know its possible since iTunes used to catch duplicates quite nicely. I ***think*** it checked
1) file name (similar file names in different folders)
2) song name from ID3 tag (ignoring whitespaces and special characters)

So, is there any Ubuntu (I'm on feisty) program to weed out duplicate songs?

---

### Post by dannystaple on 2007-06-08
I was once looking for something like this, to weed out likely duplicates of any file, including and not limited to MP3s. I found KleanSweep (which is in Universe I think), and FSLint.

Danny

---

### Post by n3twrkm4n on 2007-06-08
> **dannystaple said:**
> I was once looking for something like this, to weed out likely duplicates of any file, including and not limited to MP3s. I found KleanSweep (which is in Universe I think), and FSLint.

Danny

[FONT="Courier New"]fdupes -r ./stuff > dupes.txt[/FONT]

That will output to a file, or if you really WANT to delete them you can do:

[FONT="Courier New"]fdupes -r ./stuff | xargs rm -f[/FONT]

I would try that first on a sample file just to make sure before you go deleting. fdupes uses an md5 hash to match the files so it should be *pretty* accurate.

Home of fdupes:
[http://netdial.caribe.net/~adrian2/fdupes.html](http://netdial.caribe.net/~adrian2/fdupes.html)

---

### Post by sshetye on 2007-06-18
> **n3twrkm4n said:**
> [FONT="Courier New"]fdupes -r ./stuff > dupes.txt[/FONT]

That will output to a file, or if you really WANT to delete them you can do:

[FONT="Courier New"]fdupes -r ./stuff | xargs rm -f[/FONT]

I would try that first on a sample file just to make sure before you go deleting. fdupes uses an md5 hash to match the files so it should be *pretty* accurate.

Home of fdupes:
[http://netdial.caribe.net/~adrian2/fdupes.html](http://netdial.caribe.net/~adrian2/fdupes.html)

Let me try clarifying. iTunes can weed out 

filename.mp3 [ id3 title = "ONE"]
versus
FILEname123.mp [id3 title = "One"]

If fdupes uses MD5 for comparisons it will most likely always fail in the scenario above, where ID3 tags (embedded in file, affects MD5) could have "ONE" vs "One". 

Danny, kleensweep appears to not read inside ID3 tags. So there is no way it is "aware" that the ID3 tags hint that the songs could be similar.

So I'm guessing there is no application that can find duplicates in Ubuntu like iTunes detects on Windows???

When will computers get smart to "listen" to songs and flag duplicates even if filenames/ ID3 tags / volume level/ equalizer settings /mono/stereo settings are different. And then just delete the bot bitrate/poor quality one.

---

### Post by H.E. Pennypacker on 2007-06-18
Have you tried FSlint?  How about Duplicate Music Matcher?  

[http://gnomefiles.org/app.php/Duplicate_Music_Matcher](http://gnomefiles.org/app.php/Duplicate_Music_Matcher)

FSLint is available through Synaptic.

---

### Post by sshetye on 2007-06-20
> **H.E. Pennypacker said:**
> Have you tried FSlint? 
FSLint appears to check for duplicate file. Doesn't seem to have the smarts for recognizing close/identical MP3 files.

> **H.E. Pennypacker said:**
> 
 How about Duplicate Music Matcher?  

[http://gnomefiles.org/app.php/Duplicate_Music_Matcher](http://gnomefiles.org/app.php/Duplicate_Music_Matcher)


THIS my friend look promising. Documentation appears to make it appear even better than iTunes' detection. We'll find out. Running this on my collection right now. Thanks !

UPDATE: This appears to be the right concept, but is showing up TOO many false positives. In fact some songs are flagged as duplicates even when the ID3 tags are quite different!!?? A bug in this program? If this program is improved, I can see it being used more widely

---

