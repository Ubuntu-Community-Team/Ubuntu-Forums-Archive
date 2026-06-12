---
title: "shnsplit, splitting FLAC"
date: 2011-12-18
forum: Multimedia Software
---

### Post by MoreOrLess on 2011-12-18
I feel like I'm missing something obvious here and I've been searching for hours trying to split a flac file into a few separate flac files. I use this command:
```
shnsplt <filename>
```
Then I enter the split points in m:ss format, but I don't know what to enter to indicate the final split point (which happens to be the end of the file in my case). The man page is not helpful.

---

### Post by satanselbow on 2011-12-18
What you need my friend is the most excellent "flacon"... which isn't in the repos for reasons known only to... dunno who...

[https://launchpad.net/~flacon/+archive/ppa](https://launchpad.net/~flacon/+archive/ppa)

Essential CUE/FLAC splitting software if ever there was some - enjoy :popcorn:

EDIT: Just re-read your original post... Have you got a cue file? If not it is simple to create your own using the info from [https://en.wikipedia.org/wiki/Cue_sheet_%28computing%29](https://en.wikipedia.org/wiki/Cue_sheet_%28computing%29)

---

### Post by MoreOrLess on 2011-12-18
I just put the times into a text file, one per line, and used the -f option. That worked, but I'm still wondering how to specify <eof> on the terminal (and it's not entering no input).

---

### Post by MoreOrLess on 2011-12-18
> **satanselbow said:**
> What you need my friend is the most excellent "flacon"... which isn't in the repos for reasons known only to... dunno who...

[https://launchpad.net/~flacon/+archive/ppa](https://launchpad.net/~flacon/+archive/ppa)

Essential CUE/FLAC splitting software if ever there was some - enjoy :popcorn:

EDIT: Just re-read your original post... Have you got a cue file? If not it is simple to create your own using the info from [https://en.wikipedia.org/wiki/Cue_sheet_%28computing%29](https://en.wikipedia.org/wiki/Cue_sheet_%28computing%29)
Thanks for the suggestion. I saw it when searching, but it seemed like massive overkill to split one flac file and I really want to know what I was doing wrong.

---

### Post by satanselbow on 2011-12-18
Every audio CD that comes into my house gets backed up as CUE/FLAC before the kids / dogs destroy them so it falls into the "essential software" category for me ;)

Cue + Flac is like Bread + butter so it seems logical to use the app designed for the job :popcorn:

---

### Post by MoreOrLess on 2011-12-18
The first thing I do with CD's is rip them into flac before they get scratched. The reason I don't create a cue file when ripping is because music players read them as playlists and create multiple entries when I add the CD directory.

Anyway, I was splitting a "hidden track" that's on the end of a CD after a long period of silence, so I don't think that would have shown in the cue.

Thanks for the tips, though.

---

### Post by shantiq on 2011-12-19
**Commandline with SoX**  if you have no cuefile

>     TRIM AND SPLIT AUDIO 


sox filename.flac 1.flac --show-progress trim 0 02:00 && sox  filename.flac  2.flac  --show-progress trim 02:00 01:13


on a file called filename lasting 3:13
if you wish to split in 2 files one 2 min and one 1:13



=========================================================================

yes [flacon]("http://ubuntuforums.org/showpost.php?p=10893306&postcount=12") is good too and cokeid split-lossless script [too]("http://ubuntuforums.org/showpost.php?p=11507101&postcount=13")   bOth of these require a cuefile.  **T**hey are for splitting single file lossless albums if that is what you are after   shnsplit is clumsier than those 2;   anyway i put the info for that too further down   ;  flacon is **really** good


**=================**




if one wants to use shnsplit and you have a cuefile [**answer to your original question**]

you need ```
sudo apt-get install cuetools

```





> 

Shnsplit requires a list of break-points with which to split an audio file. Conveniently, cuebreakpoints prints the break-points from a cue or toc file in a format that can be used by shnsplit. You can pipe the output of cuebreakpoints to shnsplit as follows:

**[COLOR="DarkRed"]```
cuebreakpoints sample.cue | shnsplit -o flac sample.flac
```[/COLOR]**

In this example, a flac file called &#8220;sample.flac&#8221; is split according to the break-points contained in &#8220;sample.cue&#8221; and the results are output in the flac format.

The output file format is specified via the &#8220;-o&#8221; option. If you don&#8217;t specify an output format your split files will be in shntool&#8217;s default format (i.e., wave files, &#8220;wav&#8221;).  **you can also use ** -o wv  -o shn  -o ape



here is [all the info]("http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/") you need

---

### Post by shantiq on 2011-12-19
> **MoreOrLess said:**
> 
Anyway, I was splitting a "hidden track" that's on the end of a CD after a long period of silence.


**Commandline with SoX if you have no cuefile**

TRIM AND SPLIT AUDIO 

> 
 sox filename.flac 1.flac --show-progress trim 0 02:00 && sox filename.flac 2.flac --show-progress trim 02:00 01:13 


 on a file called filename lasting 3:13
 if you wish to split in 2 files one 2 min and one 1:13

---

