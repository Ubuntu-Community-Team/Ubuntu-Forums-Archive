---
title: "MKV support"
date: 2015-03-24
forum: Multimedia Software
---

### Post by fisheye11 on 2015-03-24
I'm a newbie, and recently swtiched to Ubuntu 14.04 and am recovering from Windows 8. Though I have prior experience, its too minor to consider current.  I want to play MKV files in VLC, but am having no luck.  I know its a container filetype, and have tried other players.  I've installed the restricted extras, but nothing has changed.  What should I do?

---

### Post by SeijiSensei on 2015-03-24
"Having no luck" doesn't give us much to go on.

Try installing **smplayer** and see if that works any better for you.

---

### Post by Keith_Helms on 2015-03-25
Vlc works fine with mkv files.  Maybe you're missing a codec somewhere.  Try running it from the command line (vlc mkvfilename) and share what messages you get back.

---

### Post by fisheye11 on 2015-03-25
Sorry Sensei!  SMPlayer just plays the audio, and ignores the video.

---

### Post by fisheye11 on 2015-03-25
"[COLOR=#ff0000]No suitable decoder module:[/COLOR] [COLOR=#000000]VLC does not support the audio or video format "hevc". Unfortunately there is no way for you to fix this."[/COLOR]

---

### Post by fisheye11 on 2015-03-25
Nevermind.  I grabbed some bad files.  I downloaded a different file without the HEVC format, and it runs great.  Thanks again!

---

### Post by mc4man on 2015-03-25
There is no way to decode hevc in 14.04 with any of the Ubuntu repo  players as libav in 14.04 doesn't support hevc. So you need to either build a player like vlc or make use of a ppa, there are several that will give you that support. They'd range from just a lib & vlc plugin to get hevc support in your current vlc to much more extensive ppa(s).

So what would you like to do?

Edit: - I see you dumped using hevc so in this regard moot point...

---

