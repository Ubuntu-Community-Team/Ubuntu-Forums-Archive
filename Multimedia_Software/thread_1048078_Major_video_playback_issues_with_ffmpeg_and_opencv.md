---
title: "Major video playback issues with ffmpeg and opencv"
date: 2009-01-23
forum: Multimedia Software
---

### Post by Rae III on 2009-01-23
I have just recently finished installing OpenCV. After spending about 5 (aggravating) hours I managed to install the ffmpeg libraries for OpenCV so I could work with video. Finally the OpenCV output stopped giving me 'could not find codec' errors and instead gave me this:

OpenCV ERROR: Bad flag (parameter or structure field) (Unrecognized or unsupported array type)	in function cvGetMat, cxcore/cxarray.cpp(2882)

So I managed to trace the error and it turns out that the function cvQueryFrame() is not properly returning a frame from the desired video. So to test whether this was an OpenCV library issue or something to do with the codecs, I attempted to play some standard .avi's in various media players. Totem and VLC both tell me that I don't have the required video codecs (audio to the .avi's still plays). MPlayer though still plays videos, but I believe that is because it uses the gstreamer codecs whereas the other two do not. I've tried uninstalling the ubuntu restricted extras package and the gstreamer packages multiple times to no avail. I know there are ways specific to each media player to fix this, but that doesn't really fix my overall problem. I need to fix the codecs at the system level, which I believe would stop causing errors in OpenCV. I've spent many hours smashing my head against the wall looking for a solution, but there seems to be none. Does anyone know of anyway to roll back codecs? Or any other solution to my problem?

---

