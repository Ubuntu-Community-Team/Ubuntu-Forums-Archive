---
title: "Video playback in tv-out is blue"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by hackbarth on 2007-01-11
Ubuntu 6.06 in ECS A530 notebook. Tv-out works, but any media file being displayed in the notebook screen is blue in the TV.

I installed Dapper in my old  [ECS A530]("http://http://www.pcchipsusa.com/prod-a530.asp") notebook, to run Gnome well, I installed more 512MB of RAM.

TV-out works out of the box, mirroring the LCD screen, with one exception, whenever I play a media file, may it be .ogg or .avi, the media is displayed flawlessly in the LCD screen, but the portion of the TV screen which corrensponds to the media is blue. 

If the media file is subtitled, the subtitles appears in the TV screen, on top of the blue background that stands for the video. On the LCD it all appears normal.

If the media is put in fullscreen, the same aplies, the TV shows a blue screen, with subtitles.

I don't know where to begin. Everything else works allright. 
(well, the wireless card doesn't, but that is on another Thread...)

---

### Post by hackbarth on 2007-01-22
If anyone ever encounter the same problem and find my post, here's the solution: change the video-out driver:

To see possible values to vo drivers:

mplayer -vo help

The one wich worked to me:

mplayer -vo x11 <mediafile.ogg>

Or you can change this line in the .mplayer/gui.conf file:

vo_driver = "xv"

to

vo_driver = "x11"

---

