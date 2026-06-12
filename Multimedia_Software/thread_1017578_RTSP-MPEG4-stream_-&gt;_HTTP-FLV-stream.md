---
title: "RTSP-MPEG4-stream -&gt; HTTP-FLV-stream"
date: 2008-12-21
forum: Multimedia Software
---

### Post by utyf on 2008-12-21
Good morning!

That's what is needed:
    Reencode rtsp-stream from an ip-camera (Vivotek IP7138&#1073; video and audio) to flv-stream and serve out (http) to glad users :) 


That's what I have:
    Ubuntu 8.10 without X, remote machine, access with ssh.
    Ubuntu 8.10 at home to test flv-stream.

At the moment I've tried:
    ffmpeg + ffserver (ffmpeg does not send responses to RTMP server (camera) and therefore camera closes connection after 20 seconds, when I stream from local file(flv, avi, mpeg, whatever you want), works good)

    openRTSP+ffmpeg+ffserver ( openRTSP writes mov-files good, but can send into pipe only 1 elementary stream(video or audio), and there are some other problems)

    vlc - gives me a lot of 'vbv buffer overflow' messages, local files streaming works fine. ( And eats more CPU  )

    mencoder+ffmpeg+ffserver ( mencoder writes good flv files, but when I send output into a pipe ffmpeg doesn't want to read it).
   

Ask for help and good discussion about it, if somebody had this experience (successfull or not).

During last days, I've seen megabytes of logs from these programs, so I'll post some of them here only if our discussion will start ;)

---

### Post by yetihehe on 2009-12-11
I have about the same problem, but wanted to approach it more from red5 side. If you could go commercial, wowza is the answer. Development version is free and almost the same, but is limited to only 10 streams. With red5 you could try xuggler, openrtsp, ffmpeg, vpipe, steamStreamer, LiveRTMPClient...
Someone had some success with openrtsp: [http://www.zoneminder.com/forums/viewtopic.php?t=11475](http://www.zoneminder.com/forums/viewtopic.php?t=11475)

---

