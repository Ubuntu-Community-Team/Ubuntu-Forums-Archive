---
title: "recordmydesktop output video file codec problem?"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by audax321 on 2007-05-04
Hello,

I installed recordmydesktop from the repos to record my desktop :)  The program itself does what it is intended to do and outputs the video file. The problem is that my laptop (Feisty with all codecs installed) can't play the output file whether it is ogg, avi, or mpg (other files with these extensions play fine). I've tried totem-xine, totem-gstreamer, mplayer, and vlc. They all just open and immediately crash.

For a while I thought it was something wrong with the encoding, but then I copied the video to my desktop computer (Dapper) and the video played fine. I even sent the file to my brother who is using Windows and the video played for him as well.

Anyway, I'm just wondering if anyone else is experiencing this problem on Feisty or if anyone knows of a way to fix it.

I installed all my codecs on Feisty using Automatix... I installed them on Dapper manually, but I double-checked on Feisty and everything seems to be installed.

Also I've attached a quick video file made using recordmydesktop if it helps.

EDIT: I thought I should also mention that Feisty can display the video thumbnail, so obviously it can read something, but can't play it without crashing.

Thanks for your help.

---

### Post by audax321 on 2007-05-04
Okay, I've found these workarounds:

mplayer -vo x11 file.ogg   (works, but gives an error about not being able to open some codec)
vlc (works with no error and again the video plug-in needs to be set to x11)

So, now I'm using vlc to playback the videos.

---

### Post by audax321 on 2007-05-05
Okay I completely fixed the problem with totem (xine version, might work with the gstreamer version too ...also took care of graphical issues with Beryl and playing videos for me) :)

1. Open /home/username/.gnome2/totem_config

2. Find the following section:

```

# video driver to use
# string, default: auto
#video.driver:auto

```

3. Change that section to:

```

# video driver to use
# string, default: auto
#video.driver:auto
video.driver:xshm

```

Hope that helps someone.

---

### Post by sk8dork on 2007-05-15
i was having this same issue on one of my machines. the example .ogg video that comes with ubuntu would play but not the one encoded from record-my-desktop would not. changing totem_config as described in post 3 fixed the problem.

---

### Post by philidox on 2007-07-13
thank you so much!  I was just about to post a new thread complaining about the same issue but that change fix it right up, your the best

here is the url to see how it is done [http://www.youtube.com/watch?v=7130JPIzCK8](http://www.youtube.com/watch?v=7130JPIzCK8)

---

