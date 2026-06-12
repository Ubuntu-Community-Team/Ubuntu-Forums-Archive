---
title: "need help converting avi files"
date: 2008-05-04
forum: Multimedia Software
---

### Post by TJ-Tigger on 2008-05-04
I have a video that I am trying to play on my xBox from my ubuntu box running TwonkyMedia.  Works quite well for the most part but I have an old video file that does not want to play.  I assume that it is due to the codec that was used to encode it.  I have not done much with video encoding/transcoding in a long time and never on linux. 

So to get to my point how can I convert this file to a format that will be supported on my xBox.  Here is the file output on the file

[email]t@t-desktop:/videos/vid1.avi[/email] vid1.avi: RIFF (little-endian) data, AVI, 320 x 236, 15.00 fps, video: DivX 3 Low-Motion, audio: MPEG-1 Layer 3 (stereo, 22050 Hz)

and here is an example of a file that plays well.

[email]t@tdesktop:/videos/vid2.avi[/email] vid2.avi: RIFF (little-endian) data, AVI, 640 x 480, 23.98 fps, video: XviD, audio: MPEG-1 Layer 3 (stereo, 48000 Hz)

The second video works just fine and I assume that is because it is using XVID and the first is using DIVX 3.  Is there a good way to convert the first video to a format that I will be able to stream to my 360?  I am reading up on ffmpeg but am not certain how to choose the correct codec for the avi file.

Thanks any help would be appreciated.

Tigg

---

### Post by Farenheit on 2008-05-04
You could try to download WinFF ([www.winff.org](www.winff.org)).  It's a front-end for ffmpeg and will allow you to open the original file, choose a new format, and convert.  

You'll need ffmpeg and the appropriate codecs installed for it to work.

---

### Post by TJ-Tigger on 2008-05-04
Thanks I will take a look at that.  I did find a way to get it to convert and work on my xBox

mencoder <filename.avi> -ovc xvid -oac mp3lame -o <output.avi>

---

