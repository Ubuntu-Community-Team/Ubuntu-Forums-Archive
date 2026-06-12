---
title: "Change dvb-t card encoding options"
date: 2010-05-24
forum: Mythbuntu
---

### Post by reformy on 2010-05-24
Hi all
I've noticed that all the recordings I do with my dvb-t card (aver-media) are encoded in a way that prevents me from opening those files in Avidemux. Previously I had a PVR-150 card and the recording it did were easily editable using Avidemux.
How can I change the card encoding options?

Thanks,
Yair

---

### Post by ian dobson on 2010-05-24
Hi,

The signal your dvb-t receives from the antenna is already encoded as a digital stream (mpeg2/h264). Your old pvr-150 received an analog TV signal that it encoded with an encoder chip on the card which MythTV then read.

Maybe you need to transcode the recording before Avidemux can process it.

What error are youseeing when you try and process a recording with Avidemux?

Regards
Ian Dobson

---

### Post by reformy on 2010-05-25
Thanks for your answer.

Well, it's not really an error. It opens the file, but it plays it slow, and you can't jump to key frames or even back and forward with the arrows. If u try that - it simply jump back to the beginning of the file.

I have a user-job that moves the recording and then delete the recording. Maybe I need to add a transcoding to that script (using ffmpeg or something).

---

### Post by ian dobson on 2010-05-25
Hi,

Maybe just try a lossless transcode, it could be that the stream your getting from your DVB-T source isn't 100% standards conform and thats causing Avidemux problems.

If you have a windows box, have a look at GSpot it's a great freeware tool to analyse video files.

Regards
Ian Dobson

---

### Post by reformy on 2010-05-26
gspot says:
File Type: MPEG-2 Transport Stream
Mime Type: video/mp2t

and no video data.

---

