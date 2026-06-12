---
title: "mythtranscode failing during archive videos"
date: 2008-05-30
forum: Mythbuntu
---

### Post by jakev383 on 2008-05-30
I'm trying to make a DVD of some of my recorded shows, and it never cuts the commercials out.
Looking at the logs that are displayed during the process, I see:
```

2008-05-30 07:26:03           Modern Marvels
2008-05-30 07:26:03 Video resolution is 480 by 480
2008-05-30 07:26:03 *************************************************************
2008-05-30 07:26:03 Processing file 1053_20080415130000.mpg of type recording
2008-05-30 07:26:03 *************************************************************
2008-05-30 07:26:03 File type is 'mpeg'
2008-05-30 07:26:03 Video codec is 'mpeg2video'
2008-05-30 07:26:03 File has a cut list - running mythtrancode to remove unwanted segments
2008-05-30 07:27:49 Failed while running mythtranscode to cut commercials and/or clean up an mpeg2 file.
Result: 256, Command was mythtranscode --mpeg2 --honorcutlist -c 1053 -s 2008-04-15T13:00:00 -o /var/lib/mythtemp/work/1/tmp
2008-05-30 07:27:49 Failed to run mythtranscode to remove unwanted segments
2008-05-30 07:27:49 File will be re-encoded using profile EP
2008-05-30 07:27:50 streaminfo.xml :-
<?xml version="1.0" ?><!DOCTYPE FILEINFO><file duration="3596" filename="/var/lib/mythtv/recordings/1053_20080415130000.mpg" type="mpeg">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="6000000" codec="mpeg2video" ffmpegindex="0" fps="29.97" height="480" id="480" start_time="0.36036" streamindex="0" width="480"/>        
                <audio bitrate="384000" channels="2" codec="mp2" ffmpegindex="1" id="448" language="N/A" samplerate="48000" start_time="0.17034" streamindex="1"/>        
        </streams>    
</file>

```

Does anyone know why it's failing? I had a lot of issues after installation of the backend (I moved from Mythdora to Mythbuntu) and had to create the /var/lib/mythtemp dir and set the permissions for it (currently /var/lib/mythtemp is 777 owned by mythtv:mythtv and config/ logs/ and work/ under it have the same permissions).
Any help is appreciated!

---

### Post by jakev383 on 2008-05-30
Looks like I solved it - instead of having the dir owned by mythtv:mythtv I had to own it by my user (jake:jake).  It's happily cutting commercials right now!

---

### Post by jakev383 on 2008-07-01
Spoke too soon.  It's still failing with the same code and the dirs are all owned by my user, not mythtv.
Anyone have any idea why it may be failing?
Thanks.

---

### Post by jakev383 on 2008-07-01
Guess I really should work on things a little more before posting from the hip; a solution that seems to be working (for now) was found here:
[http://ubuntuforums.org/showthread.php?t=610856&highlight=mythtranscode+256&page=2](http://ubuntuforums.org/showthread.php?t=610856&highlight=mythtranscode+256&page=2)
I DID add the line to my startup script as well, so hopefully this shouldn't rear up again.

---

