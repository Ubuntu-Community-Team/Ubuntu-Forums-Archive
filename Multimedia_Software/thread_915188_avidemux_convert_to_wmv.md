---
title: "avidemux convert to wmv"
date: 2008-09-09
forum: Multimedia Software
---

### Post by Blippo on 2008-09-09
Hi!

Sorry if this been answered before, but i have searched and didnt find any answer.

Im trying to find a way to convert to wmv in avidemux.
My porpuse for this is because i convert with subs to play it on my xbox360.

My xbox only accepts wmv format. And i have no posiblility to connect to xbox live and download a codec.
My solution to my problem for now is to first convert to avi with the subs then use ffmpeg to convert to wmv.
I find this pretty time consuming and needless to do if i could to it in just one converstion.
And i have found that sometimes when i do the last conversion to wmv the sound goes out of sync.

i use this command that i found somewhere..(mayby here on ubuntu forums, i dont remember..)

#ffmpeg -i "file.avi" -s 640x412 -b 1500k -vcodec wmv2 -ar 44100 -acodec wmav2 -ab 128k -ac 2 -y file.wmv

Can i use this codec "wmv2" and "wmav2" in avidemux?
Or does anyone have a better solution to my problem?

//Blippo

---

