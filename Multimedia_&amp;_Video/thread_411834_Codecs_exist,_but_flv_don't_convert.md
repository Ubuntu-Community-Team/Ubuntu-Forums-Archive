---
title: "Codecs exist, but flv don't convert"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by Zalbor on 2007-04-17
I'm using edgy. I've checked many threads here about how to convert an .flv file to .mpg or .wmv, and none of them work. mencoder and ffmpeg both say that they can't recognise the format of the source file. I've installed w32codecs and all other codecs I know of that could help.

Is there a solution?

EDIT: It seems some get converted, but only the sound (no picture). And also the VLC player can't play some of them.

---

### Post by snoop on 2007-04-17
What commands are you using for ffmpeg? I only ask because I once got that error and it turned out that I had placed -i twice. This is the command I use to successfully convert videos  ffmpeg -i input.flv output.mpg

You can also try using vlc itself to convert the video (this might be using mencoder of ffmpeg itself, but not sure).

Also, is this a flash file that you got off a website (ie, do you know that the file actually works and is not corrupt itself).

---

### Post by Zalbor on 2007-04-18
I removed the files I'd written the commands in... but I found them somewhere on these forum, and they were working for others.
The files were new and from youtube. Also, the flv player in windows plays them fine, so they shouldn't be corrupt.
I'll try converting with VLC, I didn't know it could do that, thanks. But what about the ones it doesn't even play?

---

### Post by snoop on 2007-04-18
This is a strange problem, because vlc, ffmpeg are both cross platform.

Did you try using mplayer? Sorry i cant be of more help.

---

### Post by Zalbor on 2007-04-19
Yeah, mplayer plays less than vlc, and sometimes it crashes...

Thanks for helping as much as you could anyway :)

---

