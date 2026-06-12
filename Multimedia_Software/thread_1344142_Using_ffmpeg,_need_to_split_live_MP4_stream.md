---
title: "Using ffmpeg, need to split live MP4 stream"
date: 2009-12-02
forum: Multimedia Software
---

### Post by jstefan on 2009-12-02
I am quite new as my avatar shows. I am new to Linux, Ubuntu and multimedia. I have been reading the ffmpeg documentation and plenty of web pages but have not seen a solution to my problem.

I am using ffmpeg to convert frames grabbed by a video4linux2 board connected to a movie camera into MP4 format. 

I need to split the MP4 output data stream into multiple files while decoding is still in progress without loss or duplication of the frames. Splitting the files will minimize data loss if the system crashes and also allows the previous data to be transmitted or burned to a DVD. 

A number of web pages tell how to manually splt a static file with one or more commands, but I need a way to split the continuous data stream on a periodic basis. 

I could send the mp4 data to sysout and pipe to another process to split, but I doubt the process would be able to detect and split on a frame boundary and for all I know the MP4 format needs a special starting and ending file sequence.  
 
Any ideas would be appreciated.

TIA,
Jan

---

### Post by FakeOutdoorsman on 2009-12-02
I recommend asking this question on the [ffmpeg-users](http://ffmpeg.org/contact.html) mailing list.  Make sure to read the "rules" (the first paragraph in the above link) before posting your question, otherwise you may be ignored.

If you get an answer that works please post it here too.

---

### Post by jstefan on 2009-12-03
will do.
Thanx

---

