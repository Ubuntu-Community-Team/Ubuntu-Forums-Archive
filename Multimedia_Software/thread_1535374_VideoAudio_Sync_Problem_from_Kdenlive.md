---
title: "Video/Audio Sync Problem from Kdenlive"
date: 2010-07-20
forum: Multimedia Software
---

### Post by zosowolfpacker on 2010-07-20
Hi all,
I am having a unusual problem...or unusual to me...with the audio/video synchronizing in my first video created from "kdenlive".  
The weird part is both sync within kdenlive, both sync when I view the video on my laptop but the audio gets a little bit faster than the video once the video is rendered and uploaded to YouTube.  It's only in YT, that this happens.
I render the video as an MP4 using the "Web" YouTube rendering format preset in kdenlive.  I believe I'm going with the HD format.

Posted a question about this over at the kdenlive forum but still no help as of yet.

I would greatly appreciate any insight or solutions to check out.  

Thanks much everyone!

---

### Post by zosowolfpacker on 2010-07-20
Just an update on this issue.  I went back and did an upload to YouTube using the 640 X 480 format.  And that time everything worked great in YouTube.

However, I am not sure why the audio/video gets out of sync when rendering as 1280 X 720?  
So I still have the problem in that arena and woulo  like the format to be of such quality.

Thanks guys,

---

### Post by Maximus_ARNP on 2011-01-05
I had the same problem on computer as well as on Youtube uploads.

This is how I have been able to solve the problem:

Extract Audio from Video and convert it to MP3 or WAV. (Use AUDACITY for conversion for audio format).
Import Audio first as WAV (if that does not work you may try MP3 later).

Set PROJECT SETTINGS: HD 1080p 30 FPS

On TIMELINE, Audio and Video have correct length of 10 minutes. But, in "PROJECT MONITOR" as I play, the length of the project reads longer than 10 minutes. [No worry].

RENDER to a file (.m2t) using 1080p 30 FPS. 

Confirm that Audio is in sync with Video. At this time, if Audio is not in Sync, used MP3 audio and remove WAV audio. Make sure you save and close the project and REOPEN Project and IMPORT MP3 audio. You will notice that in the property of the outputed video file, the estimated duration is longer than actual length of original audio.

When you upload video to Youtube, Youtube will render CORRECT length as original recording.

Enjoy.

---

