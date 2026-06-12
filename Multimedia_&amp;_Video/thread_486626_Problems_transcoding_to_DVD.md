---
title: "Problems transcoding to DVD"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by yodermk on 2007-06-28
Hi,

I'm trying to get my wedding on a DVD.

Problem summary:  After the transcode command, it chops off the top and bottom of the video.

Steps taken so far:

* Video recorded in 16:9 mode on a Panasonic GS500 (true widescreen)
* Edited in Cinelerra to where I want it.  Cinelerra project specifies 16:9
* Rendered to an AVI file.  So far so good.
* Transcode step:

$ transcode -i wed1.avi -x mplayer,mplayer -y ffmpeg --export_prof dvd-ntsc --export_asr 3 -o wed -D0 -m wed.ac3 -J modfps=clonetype=3 --export_fps 29.97

So why is it chopping off part of the video, and how can I prevent it from doing that?  I am thinking I can pass an option to mplayer but am not really sure of the specifics.

Thanks for any suggestions!

---

### Post by kelvin spratt on 2007-06-28
I Do This Sort of thing all the time i use cinelerra as you do and save as Quicklime for Linux i use a higher bitrate  not Defaul  for rendering [then they play in windows media player if you use Nero mp4 codec,]  Then Use DeVeDe to write to DVD no transcoding DeVeDE gives me a choice of default or wide or full frame and a choice of frame rates and sound rates write as ISO and burn jobs done on my system, the latest version is you can get here [http://www.getdeb.net/](http://www.getdeb.net/) do a 10sec preview to check things are ok if you have a problem with sound go to the DeVeDe site bottom of page their is a patch for mencoder but preview first as i don't need the patch

---

### Post by timcredible on 2007-06-28
cli has it's place, but why not use qdvdauthor or devede or kdenlive to make it easier?  i used to like dvdstyler, but i'm moving to qdvdauthor instead because it does more.

---

### Post by yodermk on 2007-06-29
Tried QDVDAuthor and got confused.  Found a good tutorial for all the CLI stuff and figured I'd just follow that.

Will try devede and/or kdenlive.  Of course if anyone knows why the transcode is chopping off some of the picture I'd still love to know that.

Thanks!

---

### Post by yodermk on 2007-07-03
For the record, just tried it with --export_asr 2 (instead of 3), which specifies a 4:3 aspect ratio (3 specifies 16:9).  Now it doesn't chop any video off, but it does stretch it out a little top to bottom.

Still seems like it should have worked earlier since the video was already 16:9 ...

---

### Post by yodermk on 2007-07-03
Ok, I pumped out a pretty nice video using the Quicktime for Linux export, then by using DeVeDe.  I didn't see where it allows for creating DVD menus, but maybe I missed something.  It's a good start anyway, thanks Kevin!

---

### Post by ubunlilluz on 2007-07-03
i usually use tovid and in particular its gui tovidgui

---

### Post by lintoon on 2007-07-03
I usually use avidemux and use varsha to create the dvd structured iso.  K3b to burn the iso.  Varsha can burn it direct but I like to use k3b because I trust it. Always perfect.

---

