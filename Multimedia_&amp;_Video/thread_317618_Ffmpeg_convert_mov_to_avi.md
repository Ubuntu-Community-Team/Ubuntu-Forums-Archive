---
title: "Ffmpeg: convert mov to avi"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by KenSentMe on 2006-12-12
I have a quicktime mov file that i want to convert to a file that can be used by Windows Media Converter. It's for uploading a video to a website. I tried using ffmpeg for this, and used this command:

ffmpeg -i movies.mov -sameq -vcodec wmv3 -acodec wmav2 -f avi movies_final.avi

But then i get this error:

Unsupported codec for output stream #0.0

What am i doing wrong and am i using the right options/codecs that Windows Media Encoder will probably like best (i know it's pretty picky about codecs).

Regards,

KenSentMe

---

### Post by brent_watson on 2006-12-20
I tried to convert mov files on my Debian sarge system for quite some time.  The furthest I got was to install VLC and use the File-->Wizard... option.  I could get videos to convert from MOV to AVI's, but I would always lose the sound.  Maybe you'd have better luck on Ubuntu...

If all else fails, you can go down the same road I did, and use an on-line converter.  eg: [http://media-convert.com/](http://media-convert.com/)

---

### Post by Dekunuts on 2006-12-20
I had the same problem some time ago and I don't exactly remember what I did, but I think you have to give resolution and audio sample rate and such in your command line, but I can't remember the correct values. Hope that helps a bit

---

