---
title: "Record &quot;quad&quot; format with ffmpeg?"
date: 2018-10-13
forum: Multimedia Software
---

### Post by SimonHGR on 2018-10-13
Hi all, I have a four channel USB input device. I know it's working, because audacity records the four independent inputs perfectly well. But I would prefer to do my recording using ffmpeg. I've found in the ffmpeg docs that channel format may be specified using "quad" (and indeed, ffprobe tells me that the four-channel output file I get when I export from audacity is in "quad" format. But for the life of me, I can't work out how to actually use this specification on an ffmpeg command line. Try as I might, I either get an error because the command line is malformed, or I get a stereo file.

Can anyone tell me how to formulate an ffmpeg command such that it records all four channels, in "normal" quad channel layout, rather than simply producing stereo?

---

### Post by Autodave on 2018-10-13
I cannot help you with that: sorry.  But let me give you what I do have:  I record 18 channels via USB connection from a Allen & Heath mixer.  I have tried just about every program out there and Audacity is the only one that I have had any luck with.

---

### Post by SimonHGR on 2018-10-13
Interesting. Have you tried ffmpeg? Did you get two channels from it if you did? The docs for ffmpeg explain how to take five mono files and join them into a single 5.1 format surround-sound result, and how to split such a file out too, but nothing about simply reading a multi-channel input device and storing it. Hard to believe it's not capable, but I guess I have audacity as a fallback at least. Thanks!

---

### Post by Autodave on 2018-10-13
I briefly looked at ffmpeg, but that was about all.  There are a few times that I cannot run the recording (it is a church service) and someone else has to record it.  Remotely, I can then do the editing. But, I really needed something simple that didn't take a lot of teaching to someone. And, I *hated* trying to get *jack* to work: just wasn't worth all the hassle.

---

