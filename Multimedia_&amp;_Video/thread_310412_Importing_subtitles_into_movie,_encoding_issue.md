---
title: "Importing subtitles into movie, encoding issue"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by babis85 on 2006-12-01
Hello there, there have been days i have been trying to come over a problem of importing subtitles into an .avi (the extension doesn't matter). Specifically, i have managed to import them, but not in the right encoding. This is, the characters are seemed to be like russian or japanese or everything different from greek characters. The subtitles are coded in ISO-8859-7. 
I have used many programs such as mencoder (commandline), avidemux, mandvd. For the first even if i specify the preferable encoding the subtitles aren't displayed right. In avidemux, there is no option for ISO-8859-7 encoding and so in mandvd.

As for mencoder, i run it from console with the following command:
> 
mencoder -vop pp=de,scale=548:222 -oac copy -ovc lavc -lavcopts keyint=25:vcodec=mpeg4:vbitrate=679:vpass=1 -subcp ISO-8859-7 -sub "Underground a.srt" -o "UndergroundA_subbed.avi" "Underground a.avi"


Please, tell me a solution for that problem. I have dug my heels in finding one and i am not to quit soon.

---

### Post by simosx on 2006-12-19
> **babis85 said:**
> Hello there, there have been days i have been trying to come over a problem of importing subtitles into an .avi (the extension doesn't matter). Specifically, i have managed to import them, but not in the right encoding. This is, the characters are seemed to be like russian or japanese or everything different from greek characters. The subtitles are coded in ISO-8859-7. 
I have used many programs such as mencoder (commandline), avidemux, mandvd. For the first even if i specify the preferable encoding the subtitles aren't displayed right. In avidemux, there is no option for ISO-8859-7 encoding and so in mandvd.

As for mencoder, i run it from console with the following command:


Please, tell me a solution for that problem. I have dug my heels in finding one and i am not to quit soon.

The general idea is to switch to Unicode and UTF-8.
You can convert existing subtitle files with the command

iconv -f iso-8859-7 -t utf-8 < old-subtitles.sub > new-unicode-subtitles.sub

---

### Post by babis85 on 2006-12-20
Thanks for your reply. I have already tried out this way, but it doesn't work either.

---

