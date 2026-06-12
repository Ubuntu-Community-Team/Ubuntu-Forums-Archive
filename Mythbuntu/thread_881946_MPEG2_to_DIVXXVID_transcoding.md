---
title: "MPEG2 to DIVX/XVID transcoding"
date: 2008-08-06
forum: Mythbuntu
---

### Post by ian dobson on 2008-08-06
Hi All,

I have 3 tuner cards in my backend server (1xPVR-500 and 2xDVB-c) both of which produce MPEG2 output.

I'm starting to get abit worried about the diskspace on my server (I still have about 800Gb free so I've got time before it gets critical).

The question I have is "Is there a way that I can automatically transcode the recorded video to XVID/x264 but still keep the information in the mythTV SQL database?"

I can export videos using mencoder to XVID which I can play on my frontend but I can't workout to "reimport" the video back into MythTV and update the skip list. I've tried just overwriting the MPEG2 file with the XVID file, then with mythcommflag but mythcommflag died with an error that it "waited too long when trying to read the ringbuffer".

Regards
Ian Dobson

---

### Post by nickrout on 2008-08-07
yes [http://www.gossamer-threads.com/lists/mythtv/users/344684#344684](http://www.gossamer-threads.com/lists/mythtv/users/344684#344684)

---

### Post by ian dobson on 2008-08-07
Hi,

1) I've managed to export a small video using mencoder
2) Using mythrebuilddatabase I can add a recording back to the SQL database but it doesn't appear to create a cut/skip list.

It shouldn't be too hard to write a small perl script that dumps the program data from the DB, transcodes the video, "deletes" the old one then reimports the video using the data from (1), once I workout why mythrebuilddatabase doesn't recreate the skiplist.

Regards
Ian Dobson

---

### Post by Lindsay.Mathieson on 2008-08-07
> **nickrout said:**
> yes [http://www.gossamer-threads.com/lists/mythtv/users/344684#344684](http://www.gossamer-threads.com/lists/mythtv/users/344684#344684)

Being the original supplicant on that thread I can vouch for the advice :)

[LIST=1]
[*]Edit the Transcoding MPEG2 Profile. This has to be done via mtyhfrontend.
[*]Set the Dest Codec to MPEG4 (Xvid)
[*]I set the bitrate to 1200, gave me good results
[*]Via Mythweb start a Transcoding job for a existing recording
[*]This transcodes the recoding in place and updates the myttv db appropriately. Does take a while to run though :) You can monitor the progress via the mythweb status page.
[/LIST]

My 1 Hour SD recordings (2.4GB) shrunk to 630MB on average. Quality was not noticeably effected.

Automatic transcoding can be specified in the recording rule. Again I use mythweb to do this. Actually I use mythweb for everything except watching the videos :)

---

### Post by ian dobson on 2008-08-07
Hi Lindsay.Mathieson,

OK I think I've setup the transcode filter correctly but when I transcode a film I get a nuv file thats about 50% the size of the original file.

Using GSPOT to examine the video file it appears to be a MPEG1 file.

When I get back home at the weekend I'll have another look at it.


Regards
Ian Dobson

---

### Post by Lindsay.Mathieson on 2008-08-07
This is the built in transcoder? not nuvexport?

The builtin transcoder will still produce nuv files - nuv is just a wrapping format, the codec will be mpreg4.

---

### Post by ian dobson on 2008-08-08
Hi,

I'm using the built in transcoder. After playing about abit I've found the nuv is a MPEG1 container, and I'm actually getting MPEG4 videos. So the problem is solved.

I'm just supprised how quickly my backend (Q6600) can transcode from MPEG2 to MPEG4. It seems to transcode at about 60-90fps.

Regards
Ian Dobson

---

