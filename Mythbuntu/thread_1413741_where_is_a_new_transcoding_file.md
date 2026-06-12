---
title: "where is a new transcoding file?"
date: 2010-02-22
forum: Mythbuntu
---

### Post by linuxhippy on 2010-02-22
I just edited a mythbuntu recording and re-transcoded using m then transcode while watching the video.  I selected High as the method.  Where is the new file created?

---

### Post by SiHa on 2010-02-23
The default transoders replace the original file, so it'll be in /var/lib/mythtv/recordings. Have you checked on the MythTV Status page, under the job list, that it ran successfully?

---

### Post by linuxhippy on 2010-02-23
I was thinking it may have replaced the file-but it didn't.  I checked the date on the file in a terminal and it didn't change.  The file is in /recordings/StarTrekTheNextGeneration (owner=mythtv, group=mythtv, chmod=775) and not /var/lib/mythtv/recordings.

Aha-there was an error transcoding, though.  I see that in the Status page...it doesn't say what was wrong.

---

### Post by SiHa on 2010-02-23
Sorry, I was assuming you stuck with the default Myth file locations.
> Aha-there was an error transcoding, though. I see that in the Status page...it doesn't say what was wrong.

Yeah, it's not very helpful when the transcode fails. The backend log should have the error messages.

It's been a while since I fiddled with this, but when you go to transcode, is there someting like 'Auto-detect (RTjpeg)'. I think I've seen written somewhere (and this is borne out by my own experience) that this has never worked, and you should select the other option.
This may be in transcoder options which (again, I think) are under recording options - dafault transcoders.

---

### Post by linuxhippy on 2010-02-23
You were right-the error message was in /var/log/mythbackend.log and showed this:

2010-02-23 06:04:07.213 No video information found!
2010-02-23 06:04:07.214 Please ensure that recording profiles for the transcoder are set
2010-02-23 06:04:07.217 Transcoding /recordings/StarTrekNextGeneration/1021_20100210020000.nuv failed

I'm thinking the error has to do with my recording profile (2nd line).  I never set this up and I think it's in Utilities/Setup>Setup>TV Settings>Recording Profiles>Transcoders.  

Can I just use the default transcoding profiles except for the Auto-detect (RTjpeg) setting?

---

### Post by SiHa on 2010-02-24
> Can I just use the default transcoding profiles except for the Auto-detect (RTjpeg) setting?

Should be able to, the default profiles are just that, you don't (well, shouldn't) need to set them up.
I used to use the 'High-Quality' for stuff I wanted to keep on the box, and Medium for stuff that I wanted to take to work on a key and watch at lunchtime.

---

### Post by linuxhippy on 2010-02-24
well, I used the default setting and got a smaller .tmp file in the same directory (I had previously specified somewhere to keep old files during transcoding...it said it would rename the old files with .old, though).  I want to keep this file for burning to DVD as divx file and it transcoded a 3.6 GB nuv file to a 545 MB nuv.tmp file.

So, does it sound like it tanscoded this 1 hour show right?  How do you go about editing a file so it doesn't have commercials on the file to be burned to a dvd?

---

### Post by SiHa on 2010-02-24
Before transcoding, you can create a cutlist. Transcode will honour this, and remove the commercials.

See here: [http://www.mythtv.org/wiki/Removing_Commercials](http://www.mythtv.org/wiki/Removing_Commercials) (Thanks to KLC5555 for the link).
Edit: This link also has information about the RTjpeg issue.

---

### Post by linuxhippy on 2010-02-24
I'll go through this again.  I started with this and got off on a rabbit trail of my own making after the first section.

---

