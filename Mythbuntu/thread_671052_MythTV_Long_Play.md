---
title: "MythTV Long Play?"
date: 2008-01-18
forum: Mythbuntu
---

### Post by browndog289 on 2008-01-18
Hello

Does anyone know how I can change the default recording profile to long play so I can fit more on my hard disk drive?

The only option I can find is Recording Type - which gives me Normal / Audio Only etc but I want to edit the compression settings for my DVB card.

Help please!

---

### Post by racmar on 2008-01-18
The option you need to change is called bitrate.  You can change the slider, lower values give a worse recording, but make smaller files.  Also, you should look at the capture screen size.  You can set it lower than 720x720 for smaller files.

reference for bitrate: [http://www.mediachance.com/dvdlab/tutorial/bitrate.html](http://www.mediachance.com/dvdlab/tutorial/bitrate.html)


Another option is to transcode your videos.  This will basically create smaller files by changing mpeg2 into another ( better compressed ) format like mpeg4.  Transcoding is done after the recording has been made, I think you can set it to run in the middle of the night when there is little load on the backend.

---

### Post by browndog289 on 2008-01-18
Ok thanks, but is that will still leave the original MPEG2 file for myth to play - is there any way I can convert the recording (or better still have the original recording) to MPEG4 (Divx) so that I can still play it from my recordings list in Myth but save the space of having to have an MPEG2 and an MPEG4?

If I transcode it the new file will not play through Myth or will it?

---

### Post by racmar on 2008-01-18
I'm not quite sure I understand what you are asking, but I'll try to explain better. 

First, myth makes a recording ( usually ) in mpeg2.  

If you transcode, myth will create a new and smaller mpeg4 file based off the original mpeg2.  After the conversion process, myth will delete the original mpeg2 file.

Thus you are left with a smaller version of the same tv show.  The new file will play just a well as the original, it's just smaller.  Think of it like turning a bitmap file ( *.bmp ) into a jpeg ( *.jpg ).

---

### Post by browndog289 on 2008-01-21
Thanks, I've changed the settings for Medium Quality in recording profiles to transcode to MPEG4 with MP3 as audio, however this keeps failing with "Transcode Failed with status: 247".

When I check mythbackend.log it says unknown codec. I have installed w32codec as well as ubuntu-restricted-extras.

Any idea why it is failing, or how I can get the correct codec?

---

### Post by racmar on 2008-01-21
I did a quick google search and found this:

[http://forums.gentoo.org/viewtopic.php?t=510526](http://forums.gentoo.org/viewtopic.php?t=510526)
[http://mythtv.org/docs/mythtv-HOWTO-23.html#ss23.14](http://mythtv.org/docs/mythtv-HOWTO-23.html#ss23.14)

Basically, they say to change your transcode from RTJpeg to mpeg4 or vice versa.

---

### Post by ubnewbie2 on 2008-01-21
> **racmar said:**
> The option you need to change is called bitrate.  You can change the slider, lower values give a worse recording, but make smaller files.  Also, you should look at the capture screen size.  You can set it lower than 720x720 for smaller files.


I read with interest, your suggestion on changing the bitrate and screen size.  Unfortunately, I went and read the wiki, and it says you can't do this for a DVB card.
```
Recording profiles are not so useful - no longer able to change bitrate or framesize
```

Of course the wiki may be wrong.  :(

---

### Post by racmar on 2008-01-21
What model capture card do you have?  I have two pvr-500's and a HDhomerun, and they all capture in mpeg2.  I've not had any experience with DVB cards.  I've never tried to change the bitrate on my HD stuff, but don't feel bad, because it records at 7GB / hour.  A football game is upwards of 20GB.

Anyway, you *should* be able to use transcoding after you've recorded to shrink the filesize.

---

### Post by ubnewbie2 on 2008-01-22
> **racmar said:**
> What model capture card do you have?  I have two pvr-500's and a HDhomerun, and they all capture in mpeg2.  I've not had any experience with DVB cards.  I've never tried to change the bitrate on my HD stuff, but don't feel bad, because it records at 7GB / hour.  A football game is upwards of 20GB.

Anyway, you *should* be able to use transcoding after you've recorded to shrink the filesize.

I am using a pair of Leadtek DTV1000-T cards - cheap and reliable.

Here's the thing, a DVB card does not really "capture" in the normal sense.  It receives the digital stream from the TV station, and places it in a file. The TV station is what determines the format and bitrate, and, yes, they transmit mpeg2. This is why, I believe, you cannot change the bitrate, other than by running a transcode process, after it has been recorded.

I know what you mean about the large file sizes.  HD makes huge files - I had one nearly 30GB long the other day.

---

### Post by browndog289 on 2008-01-22
I managed to get it to transcode - don't ask me what I did though! :)
I just changed it back from MPEG4 to RTJPEG and saved the settings, then I went back in and changed it back and its working fine now - some shows are 1/4 of the MPEG2 size!

Thanks for your help

browndog

---

