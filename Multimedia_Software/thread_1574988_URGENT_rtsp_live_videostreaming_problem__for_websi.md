---
title: "URGENT rtsp live videostreaming problem  for websites"
date: 2010-09-15
forum: Multimedia Software
---

### Post by kdojgd on 2010-09-15
**Hello people,**

I'm really frustrated at the moment, messing around with a damned streaming problem.
Now I'm getting more and more tired of reading user posts with solutions what don't work or answers like "unfortunately is not possible". I've been working now for week, night and day, on the same problem, so please help me if possible ...

**The source-device**
I've simple wireless IP-cameras with webserver, streaming mjpeg over http and mpeg-4 over rtsp  The cams mjpeg stream does not offer audio support, so there is no other way, I must use RTSP.
[B]
The problem[/B] ...
... is, I must display the video/audio-stream (RTSP) in all common webbrowsers, but the user should not be disturbed by active-x warnings or exotic plugins like java applets. So the most common way would be a flash plugin, because the native video support of html 5 is not standardized enough.

Now the **** begins, adobe developed (POV: extra to make money) an own streaming protocol called RTMP, what is not compatible with RTSP, only with there own FMS...
[B]
Nogo solutions, already tested[/B]...
...yes there'r some solutions what would work, but they are unacceptable, because they would be to expensive for me as student, this solutions are: Flash Media Server, Wowza or a Streaminghost with transcoding... (Yes, FMS and WOWZA have free accounts, but restricted in time or number of simultaneous connection to 10, so not usable in my project)  
[B]
The bug-monsters[/B]
A free alternative streamingserver is RED5, but it's a mess, configuration is not really easy, current trunk builds dont even work on my ubuntu versions, a rstp to rtmp solution exists, but not for current dependency and the server itself does not work very stable... An other possibility in some blogs was openRTSP over pipe to ffmpeg to ffserver, but I didn't get this to work as well as all other blog-writers, except some Turkish guy, what is the reference for all other blogs...

And so on and so on

[B]
My request for help![/B]
I need a solution to display this audio/video stream, from my ip-camera, in a website, compatible to all current browsers, without installing some active-x components or something like that, to a couple of users 100 < ...

If someone could offer me a cheap solution in linux, if  restreaming by server or transcoding or a solution, to get a flashplayer that displays a RTSP stream, I take anything, if it's reliable and secure...

Please help me, I 'm thankful for everything pushing my project forward ...

Yours 

kdojgd

---

