---
title: "How to connect two or more wmv files to one large file?"
date: 2015-03-12
forum: Multimedia Software
---

### Post by bartek6 on 2015-03-12
Hi everybody,

How can I connect two or more wmv files to one large file in the simplest way? I only want to connect them without rendering or changing file format. I have Lubuntu 14.04 LTS.

---

### Post by andrew.46 on 2015-03-12
Have a read here:

[https://trac.ffmpeg.org/wiki/Concatenate](https://trac.ffmpeg.org/wiki/Concatenate)

some re-encoding might be required...

---

### Post by Bucky Ball on 2015-03-12
Audacity. It's in the repositories.

---

### Post by Rob Sayer on 2015-03-12
Are you sure you didn't mean Avidemux instead of Audacity?  The latter will indeed pull the audio stream from a video file but won't do much with wmv video.  You can append/join video files with avidemux, no problem.

ffmpeg would work too but I frankly had enough CLI usage back in the 80s.  I'm going to use a GUI app unless necessary and most users will too.

As mentioned, you can't necessarily join them without re encoding because they are both .wmv files.  Other parameters have to be the same like the resolution.

---

### Post by Bucky Ball on 2015-03-12
Ah, my mistake. ;)

---

### Post by bartek6 on 2015-03-16
I've downloaded Avidemux. I can easy join new wmv files, and save them, but I have problem with audio. The voice is disorted from point of concatenating new file.

---

### Post by bartek6 on 2015-07-07
After a few months I wanna back to this problem. Does anybody have new idea how to solve this problem?

---

### Post by Rob Sayer on 2015-07-07
Install mediainfo-gui, open both files.

They have to match in a number of parameters in both audio and video or you can't append them without re encoding.

THis is a good media forum:

[http://www.videohelp.com/](http://www.videohelp.com/)

---

### Post by FakeOutdoorsman on 2015-07-08
Did the concat demuxer as shown in the link Andrew provided not do the job?

---

