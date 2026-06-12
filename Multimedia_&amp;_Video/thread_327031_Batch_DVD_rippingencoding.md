---
title: "Batch DVD ripping/encoding"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by eldepeche on 2006-12-28
I'd like to rip my DVDs to OGG Theora format. I don't need any menus, subtitles, other languages or anything, just the main video and audio. (But, if there's a way to rip subtitles as well, that would be nice, as I have some foreign films. Not necessary though, since I've seen them and I can pretend to know what they're saying.) I want all of the files to be small enough to burn onto a single CD-R. 

I've been using Thoggen, since it's really easy and does what I want. But, it takes from four to twelve (!) hours to rip/encode a DVD. 

I'm going to be out of town for about a week, and it would be marvelous if I could rip a pile of DVD images now, then come back and have a large number of OGG files sitting there. Is there a way to automate this process? dvd::rip doesn't seem to have Theora as an output option, nor does Acidrip. I discovered OGMRip, but I can't get it to build, so that's out too. Are there command line utilities that can do this? Or some other way entirely?

---

### Post by billl on 2007-01-02
There are instructions on the homepage on how to install OGMRip on Ubuntu Dapper (they should also work for Ubuntu Edgy). Just check here: [http://ogmrip.sourceforge.net/index.html#download]("http://ogmrip.sourceforge.net/index.html#download")

You'll also find on the homepage a software called shRip that uses OGMRip's backend but has a command-line interface instead of a GUI.

Cheers,

Olivier

---

### Post by penvzila on 2007-01-14
OGMrip and Acidrip are both execellent.  In my opinion, you aren't going to get very much better if you tune the command line switches yourself, so why bother.  There is a repository to build OGMrip from, search for it here.

---

### Post by edward4130 on 2007-01-18
As far as ripping DVD's, I have two commands/scripts that may help.  Both are
based upon mencoder, which comes as part of Mplayer.  I am not doing the OGG since i have a stand alone Divx-dvd player and want to keep that format around.  This may not be what you are looking for but I am posting it to help anyone else.  Much of this I got from my Bro in law Geoff that helps me get though this stuff I can't find in the forums.

The Mplayer guys are the Hungarian prodigies that bring all media to Unix.
And have available for download all of the Windows and Real player and Apple
codecs.    They have some wonderful documentation  that you could spend 2007
reading.

Put a DVD in, and try playing it from the command line with

mplayer dvd://1

And be sure that the "1" title is the one that you want.  Sometimes it is not.
Might be dvd://2, or dvd:3.   but usually it is 1.

Once you are sure it is 1, or whatever, run this in a directory with lots of
room:

mplayer -vo xv dvd://1 -dumpstream -dumpfile outfile.mpg


That command makes a large file called "outfile.mpg".   It basically just
plays the DVD, and dumps the mpg data that it reads,  The resulting file is
called "outfile.mpg", though you could call it whatever you want, or rename
it.  It will have video and audio.

If you want to compress it, there are loits of ways, I picked this script up
in the Knoppmyth forums.  Just paste into a file, and save as "rip.sh" or
something, and chmod +x.  Note, because it is in e-mail, you may have some
trouble with the whitespace on these and may need to do some testing on the
command line to get it right before pasting into a script.

From [http://mysettopbox.tv/phpBB2/viewtopic.php?t=12899](http://mysettopbox.tv/phpBB2/viewtopic.php?t=12899)

#!/bin/bash
THEFILE=$1
NEWFILE=`echo $THEFILE|sed 's/mpg/avi/'`
unlink frameno.avi 2> /dev/null
nice -n 19 mencoder $THEFILE -oac mp3lame -lameopts abr:br=128  -ovc
lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=920:vpass=1 -ofps
25 -vf pp=de,scale=720:405 -o "/dev/null"
nice -n 19 mencoder $THEFILE -oac mp3lame -lameopts abr:br=128  -ovc
lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=920:vpass=2 -ofps
25 -vf pp=de,scale=720:405 -o $NEWFILE unlink divx2pass.log  2> /dev/null

Actually, on the Mplayer documentation pages, I picked up an example that
works faster for me:

#!/bin/bash
mencoder dvd://1 -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -oac
mp3lame -lameopts vbr=3 -o /dev/null
mencoder dvd://1 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell:vpass=2 -oac
mp3lame -lameopts vbr=3 -o output.avi

rm -f divx2pass.log

These do take a long time, longer than the movie took, but they are also
encoding it.  The quality is coming out great for me, better than cable tv
quality, not as good as DVD or HD of course.  The straight rip command takes
about half as long as the play time, I think, not sure.

Here is the documentation page:
[http://www.mplayerhq.hu/DOCS/HTML/en/index.html](http://www.mplayerhq.hu/DOCS/HTML/en/index.html)

---

