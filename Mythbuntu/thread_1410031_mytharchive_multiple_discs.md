---
title: "mytharchive multiple discs"
date: 2010-02-18
forum: Mythbuntu
---

### Post by zapstrap on 2010-02-18
I have a recorded programme too big to fit on a single dvd.  If I use the archiver in mythtv, it attempts to clean up the recording, process out commercials, etc, but then announces that it's failed, and gives up.  Is there a way to archive a recording such that it spans multiple dvds?

---

### Post by klc5555 on 2010-02-18
Usually mytharchive will try to drop frames until the video will fit onto a disc. So the mytharchive failure may be something else. Can't tell without looking at the end of the "mythburn" log. 

But if the problem really is that the video is too big for the disc and you really want to avoid a) 3rd party software or b) using the quality settings in mytharchive or using the nuvexport script to transcode the thing down to where it will fit on a single disc, then there is at least one more barbaric way to get the job done in mytharchive.

If the video needs to fit on 2 discs, you cutlist it twice. The first time marks the commercials in the first half and marks the entire second half as cut. Do it at some conveniently placed commercial break. Archive the (half) show in mytharchive onto a disc.

Recutlist the show. This time commercials in the second half are marked, and the entire first half of the show is marked as cut. Archive the (now second half) show in mytharchive onto a second disc. You can also edit the metadata for the show in the frontend to add something like "Part Two" to the title, prior to archiving the thing this second time, if you wish. And there it is. Told you it was barbaric.

If a show had to span 3 discs, then the process would be done 3 times, at roughly thirds of the way through the program.

---

### Post by zapstrap on 2010-02-20
OK, I spent some time looking for how to cutlist an archive, and if it's  in the archive system for Myth, it so far has eluded me.  This is  becoming yet another time vortex.  Can  I use Myth to create a 15GB ISO  on the hard drive and use something else to split it across several  discs so it can be played back in an old-school DVD player?  If so, what  application will allow me to do this?

---

### Post by zapstrap on 2010-02-22
The errors I get from the log viewer are as follows:

Running mythtranscode --mpeg2 to fix any errors
Failed while running mythtranscode to cut commercials and/or clean up an mpeg2 file.
Result: 1, Command was mythtranscode --mpeg2 -c 2009 -s 2010-02-12T16:00:00 -o /media/archive/mytharchivetemp/work/1/newfile.mpg
Failed to run mythtranscode to fix any errors
******************************************************
ERROR: Failed while running mytharchivehelper to get stream information from "/media/archive/rfecordings/2009_20100212160000.mpg"
******************************************************

Terminated

This is a 7 or 8 hour recording, so it's quite big.  The newfile.mpg file is ~15GB.

I have checked the file permissions to newfile.mpg, and the whole path is open for writing.

---

### Post by SiHa on 2010-02-22
The only way I know of to create a cutlist(which may not be exclusive!) is to play the file, then from the on-screen menu, select 'Edit'.

'z' (I think) will import any cutlist already created by mythcommflag.
Left / Right = Move along timeline
Up / Down = Increase / Decrease jump amount on timeline 

Enter to add a cutpoint, and select whether to delete to the left or right of this point.

When you've finished, just back out to the menu.

---

### Post by klc5555 on 2010-02-22
The mythtv wiki is very good at documenting common procedures like this. cf. [http://www.mythtv.org/wiki/Creating_a_cutlist](http://www.mythtv.org/wiki/Creating_a_cutlist)

or for the complete discussion with screenshots: [http://www.mythtv.org/wiki/Removing_Commercials](http://www.mythtv.org/wiki/Removing_Commercials)

---

### Post by zapstrap on 2010-02-26
I ran the transcoder to eliminate all commercials, then cut the program to about a 3 hour section to see if I could fit that on to one DVD.  I get a warning and the same error reported above after running ffmpeg:

2010-02-25 22:41:35 WARNING: frames ragtets do not match
2010-02-25 22:51:35 The frame rate for ntsc should be 29.97 but the stream info file report a fps of 30
2010-02-25 22:51:35 Waiting for mythtranscode to create the fifos
2010-02-25 22:51:36 Running ffmpeg
2010-02-26 00:56:42 ******************************************************
2010-02-26 00:56:42 ERROR: Failed while running mytharchivehelper to get stream information from "/media/archive/mytharchivetemp/work/1/newfile2.mpg"
2010-02-26 00:56:42  ******************************************************

I have checked the directories, as before, and they all exist and have write permission set.  I didn't see anything on this error in the Wiki pages.  Any ideas?

---

### Post by klc5555 on 2010-02-26
Can't imagine what the ffmpeg problem is, or the mytharchivehelper problem. Maybe by transcoding the commercials out by hand you've ended up with a frame index/seek table that no longer matches the video, and needs rebuilding. Also mytharchive tends to experience fewer odd problems when its working directory is under the main user/owner of the frontend rather than elsewhere. It could also be that the mpeg recording itself has a flaw that ffmpeg can't handle. Maybe other folks will have some other and better ideas. Using mytharchive has frequently not been a very enjoyable experience since about Mythtv 0.20.2. 

At any rate, when once in a while I end up with a mpeg that for whatever reason ffmpeg or mytharchive chokes on, I tend to use "nuvexport --transcode"  or "nuvexport --mencoder" at the highest possible quality settings to export the mpeg to a high-quality .avi file (nuvexport can honor a cutlist), and then use a 3rd-party program like Devede to put the .avi file onto a regular DVD. If your original show file has already had the commercial sections transcoded out, as you say, the file might be processed directly onto a double-density DVD by a program like Devede, or could have sections exported into separate .avi files using something like "nuvexport --transcode" and these sections archived onto separate DVDs with a program like Devede.

---

### Post by zapstrap on 2010-02-28
I changed all of the file permissions I could find, and I got past the error I was having.  In a sad case of snatching defeat from the jaws of victory, I advanced to the next problem instead of the objective.  Here's the tail end of the mythburn.log file now:

INFO: Video pts = 0.133 .. 1241.907
INFO: Audio[0] pts = 0.133 .. 1241.925
STAT: VOBU 3112 at 554MB, 1 PGCS

INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 16:9
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

ERR:  Cannot jump to chapter 4 of title 1, only 3 exist
ERR:  in VTSM pgc 0, button 3
************************************************************
ERROR: Failed while running dvdauthor. Result: 1
************************************************************

chmod: changing permissions of `/media/archive/mytharchivetemp/': Operation not permitted
chmod: changing permissions of `/media/archive/mytharchivetemp/work': Operation not permitted
chmod: changing permissions of `/media/archive/mytharchivetemp/logs': Operation not permitted
chmod: changing permissions of `/media/archive/mytharchivetemp/logs/mythburn.log': Operation not permitted
chmod: changing permissions of `/media/archive/mytharchivetemp/config': Operation not permitted
chmod: changing permissions of `/media/archive/mytharchivetemp/config/mydata.xml': Operation not permitted
Terminated

Looking at this site:
[http://svn.mythtv.org/trac/ticket/7884](http://svn.mythtv.org/trac/ticket/7884)
hints that this is a bug in myth.  So, after all the effort and time, it looks like I can't get there from here.  Does anybody know a work-around for this problem?

---

