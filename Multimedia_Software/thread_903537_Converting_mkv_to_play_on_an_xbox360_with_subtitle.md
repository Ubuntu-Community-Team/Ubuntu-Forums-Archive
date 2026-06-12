---
title: "Converting mkv to play on an xbox360 with subtitles and another question."
date: 2008-08-28
forum: Multimedia Software
---

### Post by wunder on 2008-08-28
Hello everyone.  First post and brand new into Ubuntu (go easy on me, heh).  I've been figuring things out greatly with the help of this forum (thank god for you all), but I have a question regarding streaming media to my xbox360.

Currently my ushare is working alright.  I mean, given the fact that when I start it it says my interface eth0 is down, but it still works.

Anyways, the original question.. I have some .mkv videos that require subtitles due to the japanese audio that I prefer.  Is it possible to convert these and still retain the subtitles?

Thanks so much for any advice you all can give.  I tried searching but couldn't really find anything that applied to my questions.  Hope I wasn't rambling too much. :)

---

### Post by wunder on 2008-09-09
bump.. any thoughts?  I still can't find anything, unless I'm overlooking something.

---

### Post by aeiah on 2008-09-09
matroska is just a container. you should be able to strip out the useful bits from the container and package them into something more useful to you without converting anything (in theory, although it depends what codec is used. i dont know what the xbox 360 can play but i guess you do). you should be able to rip out the subs and put them in a .srt or .idx + .sub, if xbox 360 can handle these. its probably worth testing with normal xvid / x264 and avi / mp4 files to make sure that part is set up, and test it with subtitle files before messing around.

if this all works then just rip out the parts you need and put them in a container that the xbox likes. look at the app mkvextract. the manual is here: [http://linux.die.net/man/1/mkvextract](http://linux.die.net/man/1/mkvextract)

and from a quick google there's a python script that will split things up for you here: [http://www.larsen-b.com/Article/261.html](http://www.larsen-b.com/Article/261.html)

bare in mind that this script tends to assume that your audio is in .ogg format but since it is doing no conversion it doesnt matter. even if its an mp3 audio and you've called it .ogg its irrelevant. what the script does is take the video, audio and subtitle out the mkv, save the subtitle as .srt then combine the video and audio and save that as a .avi. if you have multiple subtitles and audio streams the script may break or it may spit multiple files out, i dunno.

---

### Post by aeiah on 2008-09-09
it seems you may have problems with that script and might be best writing your own or finding another one. all its really doing is sending a series of commands to mkvextract and to ffmpeg

---

### Post by aeiah on 2008-09-09
also, have you looked here? 

[http://ubuntuforums.org/showthread.php?t=811826](http://ubuntuforums.org/showthread.php?t=811826)

its for ps3, but the general info is the same

---

