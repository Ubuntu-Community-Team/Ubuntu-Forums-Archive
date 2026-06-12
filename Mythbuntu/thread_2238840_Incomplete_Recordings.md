---
title: "Incomplete Recordings"
date: 2014-08-10
forum: Mythbuntu
---

### Post by hydrotom2 on 2014-08-10
I have recently updated my Mythbuntu installation doing a clean install of Mythbuntu 14.04.1 and mythtv 0.27. I then used a copy of my old database to import all the recordings etc. This went well.  I have succesfully recorded programmes since then. However in the past few days recordings have either not been recorded or have been only partialy recorded. When I use mythweb from another computer or tablet to look at the recorded programmes they either show a total size that is not equal to the recored file (it is greater) or they show a B in the file size column, which means there is no recording.
As a check I have used the frontend to watch a tv channel in real time. A similar thing occurs, the channel cuts off after about 20 mins or so. 
There is plenty of room on the discs in the system and the file permissions are ok. I can see that when a recording is truncated some files are still written to the disc but they are written as a series of image files. In a similar manner  to frames from old cine film.
Since I have limited knowledge the log files have not helped me apart from indicating a possible mythpreviewgen related issue.

eg in the syslog
mythpreviewgen: message repeated 500 times: [ mythpreviewgen[10561]: E Decoder avformatdecoder.cpp:4903 (GetFrame) decoding error#012#011#011#011eno: Unknown error 541478725 (541478725)]
 
in the frontend log lots of lines similar to what is below.
mythfrontend.real: mythfrontend[3602]: E PreviewGeneratorQueue previewgeneratorqueue.cpp:389 (GeneratePreviewImage) PreviewQueue: Attempted to generate preview for '7302_20140808203000.mpg_0x0_-1s' 5930 times; >= max(50)


I am using 2 satellite tuner cards in a dedicated HTPC under the TV.  I wonder if it is related to the tuner cards or LNB? Both lock on to the TV channel.  I dont know how to check this further..

Can anyone give me a pointer to resolve this or do I have to do another clean install to see itf the problem persists.

---

