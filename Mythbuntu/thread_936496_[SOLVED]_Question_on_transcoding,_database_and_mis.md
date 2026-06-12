---
title: "[SOLVED] Question on transcoding, database and missing files"
date: 2008-10-02
forum: Mythbuntu
---

### Post by zalnn on 2008-10-02
I am pretty new to MythTV and I have to say, is PRETTY AWESOME! 

I am now almost looking for an excuse to record programs.  I am beginning to amass a large quantity of recordings and running out of space.

So I have been looking into transcoding the programs I want to keep into Xvid / DivX. I think have figured out how to do this using nuvexport or Mythnuv2mkv, although I haven't tried it yet.

**1.** The question is, once I transcode and delete the original mpg, how does the missing file affect the database?

**2.** How will the database know to not record that episode again in the future as I have the backend recording a particular tv show on any channel at anytime, with it filtering for duplicates on Tile and Description.

**3.** In your opinion, which is a better format, DivX or Xvid?

Thanks in advance

---

### Post by ian dobson on 2008-10-02
Hi,

Why not just use the transcoder. On my system a 2 GB/1Hour SD video transcodes to about 1Gb and I don't even see a difference in quality.

To answer your questions
1) You should delete the recording through MythTV so that the database is updated

2) MythTV has a database Table "oldrecordings" which I think contains a list of recorded programs.

3)The transcoder creates DivX and I'm very happy with the quality. At high quality it seems to use a bitrate of about 1600Kibit/sec.

Regards
Ian Dobson

---

### Post by zalnn on 2008-10-03
> **ian dobson said:**
> Hi,

Why not just use the transcoder. On my system a 2 GB/1Hour SD video transcodes to about 1Gb and I don't even see a difference in quality.

To answer your questions
1) You should delete the recording through MythTV so that the database is updated

2) MythTV has a database Table "oldrecordings" which I think contains a list of recorded programs.

3)The transcoder creates DivX and I'm very happy with the quality. At high quality it seems to use a bitrate of about 1600Kibit/sec.

Regards
Ian Dobson


True, but I would really like to transcode the recordings to DivX or XviD for portability.

Also a recording compressed by about 1/5 (bitrate reduced from ~5000kbps to ~1000kbps) using XviD is better than DivX which in turn is better than MPEG-4 (or whatever it is that mythtranscode outputs).

What does / can mythtranscode transcode into?

---

### Post by ian dobson on 2008-10-03
Hi,

On my box with the standard settingd mythtranscode converts from MPEG2 to DivX when I select automatic translate.

Regards
Ian Dobson

---

### Post by zalnn on 2008-10-04
> **ian dobson said:**
> Hi,

On my box with the standard settingd mythtranscode converts from MPEG2 to DivX when I select automatic translate.

Regards
Ian Dobson

Can you expand on this a little more?  How did you set it up?  What menues? FE or BE?

Another question is, mythcommflag automatically flags all the commercials, but it doesn't generate a cut list. 

Also when I run mythtranscode with the --mpeg2 option (to generate a smaller original file w/o commercials) the .tmp file is created fine, but is not renamed and the original remains :(

My permissions are all setup to be owned by mythtv and have rwxrwxrwx (777) permissions. 

Yes, I run the job as 'mythtv' user.

So close to getting this, I can almost taste it!!! Please help!!!

---

### Post by ian dobson on 2008-10-04
Hi,

I didn't really setup anything. I just go to mythweb, select the show I want to convert and click on the convert button selecting the automatic quality detection.

The file is transcoded to a NUV container containing a DivX video which I can play back on my PC (After intalling the dsmyth video codec package).

Regards
Ian Dobson

---

### Post by zalnn on 2008-10-04
> **ian dobson said:**
> Hi,
I didn't really setup anything. I just go to mythweb, select the show I want to convert and click on the convert button selecting the automatic quality detection.


Did you mean transcode button?  I don't see a Convert button

---

### Post by ian dobson on 2008-10-04
Hi,

Transcode I guess, in German it's "Umwandeln" which translates to convert/change.

Regards
Ian Dobson

---

### Post by zalnn on 2008-10-07
OK, figured out how to get things working how I want.

For those who come looking for an answer look at the post bellow
[http://ubuntuforums.org/showpost.php?p=5539926&postcount=4](http://ubuntuforums.org/showpost.php?p=5539926&postcount=4)

Also read this thread and follow the link to the thread on "gossamer-threads"
[http://ubuntuforums.org/showthread.php?t=881946](http://ubuntuforums.org/showthread.php?t=881946)

---

