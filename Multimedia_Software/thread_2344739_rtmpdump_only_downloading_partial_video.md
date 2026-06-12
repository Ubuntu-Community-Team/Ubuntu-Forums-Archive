---
title: "rtmpdump only downloading partial video"
date: 2016-11-28
forum: Multimedia Software
---

### Post by pow14 on 2016-11-28
[COLOR=#000000][FONT=verdana]Hey guys![/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I am trying to download these videos for my exams from a site, but I keep getting the first few seconds of the video then I get empty buffer, something of that sort.

[/FONT][/COLOR]```
rtmpdump -r "rtmps://53c7c8e287199.streamlock.net/vods3/" -W "http://d2190hpfa85jkd.cloudfront.net/v11/student/swf/flowplayer-3.2.18.swf" -y "mp4:amazons3/coursekart/videos/1521/topics/ER Diagrams - Part 1 of 1_qtp.mp4" -o Vid1.flv[COLOR=#000000][FONT=verdana]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=verdana]

This is the command I am running..

here is the page source code:

[/FONT][/COLOR][http://pastebin.com/raw/iJpRfJh6](http://pastebin.com/raw/iJpRfJh6)


[COLOR=#000000][FONT=verdana]Can someone please tell me what I am doing wrong ? and how I can download the entire video? [/FONT][/COLOR][IMG]http://stream-recorder.com/forum/images/smilies/frown.gif[/IMG]



[COLOR=#000000][FONT=verdana]EDIT:

Just had to increase the buffer size! :D 

[/FONT][/COLOR]```
-R --buffer 2000
```[COLOR=#000000][FONT=verdana]

[/FONT][/COLOR]

---

