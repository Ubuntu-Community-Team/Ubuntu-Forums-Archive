---
title: "MythArchive fails on runing dvdauthor"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by releep on 2007-07-22
When I try to generate a iso image to transfer to my other system to burn with I get a message.](*,)
ERROR: Failed while running dvdauthor. Result: 1

I'm still new to this any help would be great.

I can email the logs if needed they are too big to upload to this site.
here is the end part of them.

Progress.log
2007-07-21 23:16:49 Video length is 3598 seconds. Each chapter will be 449 seconds
2007-07-21 23:16:49 Total size of video files, before multiplexing, is 1981 Mbytes, audio is 82 MBytes, menus are 3 MBytes.
2007-07-21 23:16:49 Video will fit onto DVD. 2316.95 MBytes of space remaining on recordable DVD.
2007-07-21 23:16:49 Multiplexing MPEG stream to /vid2/temp/work/1/final.mpg
2007-07-21 23:16:49 Available streams - video and one audio stream
2007-07-21 23:16:49 Multiplex started PID=9708
2007-07-21 23:16:49 Starting dvdauthor
2007-07-21 23:21:39 ************************************************************
2007-07-21 23:21:39 ERROR: Failed while running dvdauthor. Result: 1
2007-07-21 23:21:39 ************************************************************
2007-07-21 23:21:39 
2007-07-21 23:21:39 Terminated


mythburn.log
**ERROR: [mplex] MUX STATUS: Frame data under-runs detected!
WARN: Video PTS does not line up on a multiple of a field.

INFO: Video pts = 0.178 .. 1799.446
INFO: Audio[0] pts = 0.178 .. 3598.354
STAT: VOBU 9334 at 2115MB, 1 PGCS
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: pal
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x576
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

ERR:  Cannot jump to chapter 7 of title 1, only 6 exist
ERR:  in VTSM pgc 0, button 6
************************************************************
ERROR: Failed while running dvdauthor. Result: 1
************************************************************

chmod: changing permissions of `/vid2/temp': Operation not permitted
Terminated

---

