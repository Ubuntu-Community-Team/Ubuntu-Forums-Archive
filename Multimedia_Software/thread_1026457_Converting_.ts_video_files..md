---
title: "Converting .ts video files."
date: 2008-12-31
forum: Multimedia Software
---

### Post by gender on 2008-12-31
Hello,
I'm fairly new to Ubuntu, but know my way around stuff good enough. I do a lot of video converting to suit the requirements of my standalone DVD player and I've run into some problems when using avidemux.

First and foremost, the program crashes [as in, closes immediately] each and every time I try to convert a .ts file to an .avi one. Maybe 512MB of RAM isn't enough? But, yeah, no matter whether I'm converting to XViD or x264, if the container is .avi, it crashes.

I can, on the other hand, convert an .mpg file to an .avi one nice and smooth. But when converting my .ts file to an .mp(e)g one, it converts with a very slow FPS rate which is slowly going down to 0. Maybe that's how it's supposed to be?

I've also tried VirtualDub, which didn't accept the .ts file and VirtualDubMod, which had an .exe installation file that Wine wouldn't even start up.

So, yeah, maybe I'm being an idiot and missing some settings or something, so any help would be really appreciated!

[ PS: I've read tons of guides that I've Googled, but I'm still asking for help. D: ]

---

### Post by xc3RnbFO8P on 2008-12-31
Use Devede in Add/Remove (all available application)
You can coose to make ISO or MPEG file.

---

### Post by gender on 2009-01-01
Thanks! This program seems to work nicely and it keeps the video and sound in sync, unlike avidemux.

---

### Post by gender on 2009-01-03
Seems like I spoke to soon. It did convert one .ts file and converts .mpgs, but I'm trying with some other .ts files and they all come up with the error "Conversion failed. It seems a bug of mencoder." or something like that. :(
If anyone has some ideas, I'm willing to listen.

---

### Post by jocheem67 on 2009-01-03
I like handbrake a lot

[http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

It lets you convert video.ts folders to mp4 or avi without too much hazzle.
Give it a try.

I did a mp4 conversion lately and it worked flawlessly. However avidemux should in fact work too....

Only downfall is that it can only hardcode subs...if that's a problem then dvd::rip might be your thing. It is somewhat older, but quality has never been bad, and it's very versatile.

---

### Post by gender on 2009-01-03
Thank you for your suggestions. Unfortunately, Handbrake doesn't start up at all when I click it in the Sound & Video menu and dvd::rip expects me to encode a video from a DVD, while my videos are on my hard disk.

---

### Post by jocheem67 on 2009-01-04
Well, that'spretty strange. I can't help you with the reason handbrake doesn't even start up, though just maybe you need more ram ?!


You could consider using transcode or ffmpeg from the cli to do your conversions, but that's pretty difficult.

An other option is to use k9copy, but I haven't too much experience with that program. It's easy to use though.

Have you thought about using dvdfab hd decrypter and dvdshrink with wine. They work great on my rig. Ofcourse this is just plain old copying.

---

### Post by Cresho on 2009-02-03
i use all kinds of video editing software in linux.  virtualdub, mp4cam2avi, avidemux, blender, winff, vegas video, mainactor, etc.  I spent a good month configuring everything with all softwares, all codecs, all scripts.  It is possible and my results are way better than commercial products. I mentioned vegas but I really dont use it unless i think it can handle it.

It is very easy getting windows applications to run in ubuntu.
here is one example.

[http://ubuntuforums.org/showthread.php?p=6668670#post6668670](http://ubuntuforums.org/showthread.php?p=6668670#post6668670)

---

