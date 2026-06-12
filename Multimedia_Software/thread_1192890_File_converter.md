---
title: "File converter"
date: 2009-06-20
forum: Multimedia Software
---

### Post by ellalan on 2009-06-20
Hi,
I need to convert a Youtube video file(.mp4) to Audio file to record on a CD(.mp3) before Sunday night, could some one please give me a hand.
I am running Jaunty,I know I could go on and look for it but I left it too late and I am stuck for time.

---

### Post by ad_267 on 2009-06-20
Avidemux should be fine for this.

Edit: Actually the option to save audio doesn't seem to work like I thought it did. Sound converter can extract the sound from videos though, so that's probably a better program to use.

---

### Post by SuperSonic4 on 2009-06-20
go to whichever directory the file resides in and issue the following command

```
ffmpeg -i input.mp4 -vn -acodec libmp3lame -ac 2 -ab [COLOR="Red"]128k[/COLOR] output.mp3
```

Change 128k to whichever quality you desire.

edit: if you have pacpl installed that works too

---

### Post by ellalan on 2009-06-20
I'm struggling to get Avidemux going, I am doing something wrong here, I have installed the program from the repo but I find it difficult to use it.
Could some one walk me through. Thanks for the help.

---

### Post by ad_267 on 2009-06-20
I thought you could go to Audio then Save to save the audio, but that doesn't use the audio format selected. You can use sound converter instead. Just drag and drop the video file onto sound converter, then change your preferences to set the output format and convert it.

---

### Post by SuperSonic4 on 2009-06-20
You can also use an ffmpeg or mencoder script from the command line :]

---

### Post by ellalan on 2009-06-20
Thanx guys for all your help, all done [http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)
ad_267's method did it for me. It was simple and easy.

---

