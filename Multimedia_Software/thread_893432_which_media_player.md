---
title: "which media player?"
date: 2008-08-18
forum: Multimedia Software
---

### Post by pko66 on 2008-08-18
Hello!

I am new to ubuntu; have some experience with fedora but only as a server. I am really pleased with ubuntu as a desktop o.s. and, since windows XP is getting old and I do not like Vista and all that stupid DRM, I'm planning the switch. Most of the things I need are covered with openoffice, pidgin and Firefox, but I still haven't found a media player to mi liking.

I want to play video files (not DVDs... since it seems they do not want us to watch they disks, I obligingly do not buy them. In fact, I do not even have a DVD player in the computer, I disconnected it after installing ubuntu). Basic playback works OK with totem and gstreamer (with xine it works OK also), but I really find the interface lacking features I'm used to.

In windows, I use MPC (media player classic), but there are also a number of other players in windows that, more or less, cover my requirements: bsplayer, viplay, kmplayer... but haven't found any "perfect" one in linux. The problem is in the interface, the files themselves are being reproduced OK, more or less.

I've tried totem, vlc and gmplayer so far...

What I am looking for is:

1- automatic loading of subtitles (for "movie.avi" it should load "movie.srt", "movie.eng.srt", "movie.english.srt" etc). this is a MUST
2- easy changing full screen to/from windowed with just the mouse. The preferred mode would be double clicking on the movie.
3- mouse controls for playback (an interactive progress bar, volume, start/stop/pause...) in full screen; they should automatically appear/disappear with a mouse gesture or click or something like that
4- corrections in aspect ratio; MPC has some very sensible presets and also you can fine tune the AR with the keypad

totem does 1 (I think) and 2, but lacks 3 and 4. Also, it worked with some bugs in the interface

VLC, as in windows, is great at playing really weird files but the interface is simply awful. Does 2 and probably 4 but not 3. Supposedly it does 1 also (in windows it works flawlessly) but somehow does not work in my linux installation; haven't studied it at length, since I do not like the interface in windows, I do not also like it in linux. A pity, such a wonderful player, to have such a limited UI.

gmplayer lacks 1, is inconvenient at 2, does OK 3. Since it lacks proper subtitle support, that is a showstopper to me and didn't investigate the aspect ratio options. Also it looked somewhat buggy, it crashed twice in my tests.

Any suggestion? what other players should I try?

I am using Hardy Heron (gnome), Athlon X2 4800, 2GB RAM, nVidia graphics with native nvidia drivers (installed with envyng)

Thank you!

---

### Post by billgoldberg on 2008-08-18
> **pko66 said:**
> Hello!

I am new to ubuntu; have some experience with fedora but only as a server. I am really pleased with ubuntu as a desktop o.s. and, since windows XP is getting old and I do not like Vista and all that stupid DRM, I'm planning the switch. Most of the things I need are covered with openoffice, pidgin and Firefox, but I still haven't found a media player to mi liking.

I want to play video files (not DVDs... since it seems they do not want us to watch they disks, I obligingly do not buy them. In fact, I do not even have a DVD player in the computer, I disconnected it after installing ubuntu). Basic playback works OK with totem and gstreamer (with xine it works OK also), but I really find the interface lacking features I'm used to.

In windows, I use MPC (media player classic), but there are also a number of other players in windows that, more or less, cover my requirements: bsplayer, viplay, kmplayer... but haven't found any "perfect" one in linux. The problem is in the interface, the files themselves are being reproduced OK, more or less.

I've tried totem, vlc and gmplayer so far...

What I am looking for is:

1- automatic loading of subtitles (for "movie.avi" it should load "movie.srt", "movie.eng.srt", "movie.english.srt" etc). this is a MUST
2- easy changing full screen to/from windowed with just the mouse. The preferred mode would be double clicking on the movie.
3- mouse controls for playback (an interactive progress bar, volume, start/stop/pause...) in full screen; they should automatically appear/disappear with a mouse gesture or click or something like that
4- corrections in aspect ratio; MPC has some very sensible presets and also you can fine tune the AR with the keypad

totem does 1 (I think) and 2, but lacks 3 and 4. Also, it worked with some bugs in the interface

VLC, as in windows, is great at playing really weird files but the interface is simply awful. Does 2 and probably 4 but not 3. Supposedly it does 1 also (in windows it works flawlessly) but somehow does not work in my linux installation; haven't studied it at length, since I do not like the interface in windows, I do not also like it in linux. A pity, such a wonderful player, to have such a limited UI.

gmplayer lacks 1, is inconvenient at 2, does OK 3. Since it lacks proper subtitle support, that is a showstopper to me and didn't investigate the aspect ratio options. Also it looked somewhat buggy, it crashed twice in my tests.

Any suggestion? what other players should I try?

I am using Hardy Heron (gnome), Athlon X2 4800, 2GB RAM, nVidia graphics with native nvidia drivers (installed with envyng)

Thank you!

Totem does do point 3, I'm not sure about 4.

After you installed all codecs (see link in signature) it's a great video player.

---

### Post by Vivaldi Gloria on 2008-08-18
> **pko66 said:**
> VLC, ... Supposedly it does 1 also (in windows it works flawlessly) but somehow does not work in my linux installation;

To fix the vlc subtitle issue press ALT+F2 and start

```
gksudo gedit /usr/share/applications/vlc.desktop
```

and change 

```
Exec=vlc %U 
```

to 

```
Exec=vlc %m
```

See

[http://ubuntuforums.org/showthread.php?t=775337](http://ubuntuforums.org/showthread.php?t=775337)

---

