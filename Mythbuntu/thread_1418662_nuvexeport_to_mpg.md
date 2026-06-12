---
title: "nuvexeport to mpg"
date: 2010-02-28
forum: Mythbuntu
---

### Post by linuxhippy on 2010-02-28
I found that using nuvexport that I can convert huge nuv files to little tiny mpg files by choosing convert to DVD.  This just produces a data file anywhere you want.  My cable is analog-perhaps this is why the files are relatively small.  A 1 hour show is 3.5 GB and converts to a 124 MB mpg file.  The picture looks the same as when I watched it in mythtv and the aspect ratio can be changed in VLC to full screen 16:9.

So, can I enhance the clarity of the picture any and if so how?

---

### Post by klc5555 on 2010-02-28
The place to start is [http://www.mythtv.org/wiki/Nuvexport](http://www.mythtv.org/wiki/Nuvexport)  You'll want to note section 20 on the VBR Quality Option.

---

### Post by linuxhippy on 2010-03-01
That's interesting!  So I can enhance video quality.  I'm also glad that you told me what section it was in...I have trouble reading to the end of something that long :)

I'm being truthful about that too-it's like ADD after 5 minutes.

---

### Post by nickrout on 2010-03-02
> **linuxhippy said:**
>   A 1 hour show is 3.5 GB and converts to a 124 MB mpg file.  The picture looks the same as when I watched it in mythtv 

not with any quality you cannot. It's just not possible, you are missing something. Either the quality is severely retarded or you only have the first few minutes of the file.

Really, believe me, even with the best codecs available, a one hour show at 124MB is nonsense.

---

### Post by linuxhippy on 2010-03-02
just found out that 124 MB was only 5 minutes.  I don't know why it didn't do the entire recording.  I encoded 12 files and 1 was totally done without commercials.  That was 1.1 GB.

Any ideas why it made mistakes most of the time?

I did this in the directory where I wanted the archives:

nuvexport
picked output quality as DVD
selected recordings (I did 4-8 nuvs at a time and separated each with a space) and accepted all defaults (VBR was 5 and the recording was 45 minutes without commercials)

---

### Post by klc5555 on 2010-03-02
> **linuxhippy said:**
> just found out that 124 MB was only 5 minutes.  I don't know why it didn't do the entire recording.  I encoded 12 files and 1 was totally done without commercials.  That was 1.1 GB.

Any ideas why it made mistakes most of the time?

I did this in the directory where I wanted the archives:

nuvexport
picked output quality as DVD
selected recordings (I did 4-8 nuvs at a time and separated each with a space) and accepted all defaults (VBR was 5 and the recording was 45 minutes without commercials)

Could be that ffmpeg is bombing out for some reason. You could try with the "transcode" or "mencoder" switch instead ("nuvexport  --transcode"). Both are slower than the default with ffmpeg, but higher quality than ffmpeg when they work.

Also, when encoding an entire long set of episodes, if the database changes while the set is encoding (say a movie recorded in the meantime, so your TV series is now number "36" in the index instead of number "35" as it was when nuvexport was started), then nuvexport will finish encoding the episode it's working on, but will fail to find any of the subsequent episodes when setting up the fifos and will exit. You'll need to run nuvexport again to pick up the remaining episodes that it didn't get to the first time.

---

### Post by nickrout on 2010-03-02
what errors are shown in the logs?

---

### Post by azmyth on 2010-03-02
Not sure if you did this but you need to give it a new filename. I tried using the same file name before and it would work for a short while then stop.

---

### Post by linuxhippy on 2010-03-02
> **azmyth said:**
> Not sure if you did this but you need to give it a new filename. I tried using the same file name before and it would work for a short while then stop.

Maybe this is it.  I will also check my log files to see if there is a clue there.  I removed everything in this archive directory and just chose 1 show (maybe my computer cannot handle multiple transcodings) that should've been 45 minutes.  I also messed around with the VBR values thinking 6000 may have been too high and tried 2000.  Same result-the transcoding lasted 4 1/2 minutes this time but I only got 11 minutes of my show.

---

### Post by nickrout on 2010-03-02
say again: what are the error messages???

---

### Post by linuxhippy on 2010-03-02
no messages...I need to check the log files.

---

### Post by linuxhippy on 2010-03-04
I found something puzzling.  nuvexport can transcode to an mpg DVD file that's 1 hour long if it includes all the commercials...even when I indicate that it should include the cutlist.  However, on the recordings where I edited them by pressing M in the watch screen and then select edit and CTRL-Z the transcoding kept stopping at the first cut point 11 minutes into the show,

Any ideas why?

---

### Post by klc5555 on 2010-03-04
> **linuxhippy said:**
> I found something puzzling.  nuvexport can transcode to an mpg DVD file that's 1 hour long if it includes all the commercials...even when I indicate that it should include the cutlist.  However, on the recordings where I edited them by pressing M in the watch screen and then select edit and CTRL-Z the transcoding kept stopping at the first cut point 11 minutes into the show,

Any ideas why?

There could be a flaw in the original recording that does not affect its being played or cutlisted, but causes the transcode to bomb out.

You could prove or disprove this by attempting to produce a file without the commercials from your cutlisted show by running from a prompt "mythtranscode --mpeg2 --showprogress --honorcutlist -c [4-digit mythtv channel code] -s [complete start time]" 

The mythtranscode utility will give you a percentage complete update every 5 seconds until it either bombs with a (sometimes) usable error message or produces a *.tmp file that will actually be a copy of your show minus the cutlisted parts. Either way you'll be further along than you are now.

---

