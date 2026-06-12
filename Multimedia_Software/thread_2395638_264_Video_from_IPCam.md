---
title: "264 Video from IPCam"
date: 2018-07-04
forum: Multimedia Software
---

### Post by BobvanderPoel on 2018-07-04
I've got a cheapo ip security cam. Seems to work okay as far as saving files up to my ftp site, etc. But, the video it saves is in some kind of .264 format which nothing I've tried on linux seems to be able to view. The manufacturer says to use Windows IE to view the files ... I suspect it's using some active-x stuff to do this. I even booted up a version of IE in a virtualbox windows10, but that didn't work either.

I'd like to just convert the files into mp4 or something and view them. Any hope or suggestions?

---

### Post by TheFu on 2018-07-04
.264 is probably h.264, which vlc should easily play. There are freely available, legal, h.264 decoders.   But there are many different sub-types of h.264, so it is impossible for  every program to support every possible variant.   You can transcode using a tool like handbrake to well-supported variants.

BTW, mp4 is just a container, it doesn't describe a video+audio codec.

Try handbrake and you probably want to use an mkv container which is extremely flexible.

---

### Post by BobvanderPoel on 2018-07-04
> **TheFu said:**
> .264 is probably h.264, which vlc should easily play. There are freely available, legal, h.264 decoders.   But there are many different sub-types of h.264, so it is impossible for  every program to support every possible variant.   You can transcode using a tool like handbrake to well-supported variants.

BTW, mp4 is just a container, it doesn't describe a video+audio codec.

Try handbrake and you probably want to use an mkv container which is extremely flexible.

Thanks, but I've been there :) VLC doesn't play these files and handbrake doesn't recognize them. From sniffing around the web, it appears that they are "standard" .264 files with some "fluff" added. I did find one reference to a program which was supposed to "fix" them, but it was a dead link.

---

### Post by TheFu on 2018-07-04
Uh ... gotta ask, have you tried just taking the raw 264 file and putting it into a container?

```
$ mkvmerge -o  output.mkv file.264
```

It should be as fast as a copy command.

[https://superuser.com/questions/1289973/how-to-convert-raw-264-file-to-mp4-provided-by-luowice-ip-camera](https://superuser.com/questions/1289973/how-to-convert-raw-264-file-to-mp4-provided-by-luowice-ip-camera) says about the same, I just prefer mkv containers for all the added flexibility.

If that doesn't work, 
* look for mpeg2ts output options for the camera. You can transcode that on-the-fly using ffmpeg.
* And I'd return/resell the IP camera ASAP to get one which supports standards.  

If you stick with standards for everything, then the OS usually doesn't matter.

---

### Post by BobvanderPoel on 2018-07-04
I'm pretty sure it's the same problem. Using mkvmerge I get:
mkvmerge -o  output.mkv foo.H264
mkvmerge v24.0.0 ('Beyond The Pale') 64-bit
'foo.H264': Using the demultiplexer for the format 'AVC/h.264'.
'foo.H264' track 0: Using the output module for the format 'AVC/h.264 (unframed)'.
The file 'output.mkv' has been opened for writing.
Warning: 'foo.H264' track 0: This AVC/h.264 track's timing information indicates that it uses a variable frame rate. However, no default duration nor an external timestamp file has been provided for it, nor does the source container provide timestamps. The resulting timestamps may not be useful.
Error: 'foo.H264' track 0: mkvmerge encountered broken or unparsable data in this AVC/h.264 video track. Either your file is damaged (which mkvmerge cannot cope with yet) or this is a bug in mkvmerge itself. The error message was:
Success

I read the link at superuser.com a day or so ago, but the links to [https://www.spitzner.org/kkmoon.html](https://www.spitzner.org/kkmoon.html) no longer work. 

I will give the node.js file a go, but I'm not very adept at that language. 

Seems we have the same camera :)

---

### Post by BobvanderPoel on 2018-07-04
I think it is working! I grabbed the converter code and ran it on some files. Perfect. 

I says in the docs for this that further conversion may be needed, but the files I tested worked fine in vlc. 

To install:

    sudo  npm install -g chipcaco

It's that easy :)

---

### Post by TheFu on 2018-07-05
npm stuff scares me as much as javascript does, but happy you found a solution.

---

