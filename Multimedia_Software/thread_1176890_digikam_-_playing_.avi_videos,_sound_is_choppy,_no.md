---
title: "digikam - playing .avi videos, sound is choppy, no video"
date: 2009-06-02
forum: Multimedia Software
---

### Post by timcredible on 2009-06-02
ok, so i have thumbnails of .avi videos (i installed mplayerthumbs), but when i try to play the video, the audio plays but is choppy and there's no video.  anyone know what package i'm missing?  i have mplayer, kmplayer, kmplayer-konq-plugins all installed.  thanks.

---

### Post by gedakc on 2010-12-16
I had a similar problem on Ubuntu 10.04 LTS Lucid Lynx Netbook edition.

Because f-spot does not import or handle avi video files, I had installed digikam with the following command:

     ```
sudo aptitude install digikam
```

This installed a lot of other packages related to KDE.

When I started digikam it would generate thumbnails for all of my jpg pictures but there was none for my avi video files.  To fix this problem I installed mplayerthumbs with the following command:

     ```
sudo aptitude install mplayerthumbs
```

This fixed the thumbnail problem with thumbnails not displaying.


At this point I could view pictures with digikam, but when I tried to play avi video files I could hear sound, but there was no video so I installed some missing xine packages with the following command:

     ```
sudo aptitude install phonon-backend-xine libxine1-plugins libxine1-ffmpeg
```

This fixed the problem.  :-)

Now I can see the avi file thumbnails, and when I click on the avi files in digikam, the avi files play showing both video and sound.

PS:  In the above commands, you can also substitute "apt-get" for "aptitude" if you do not have aptitude installed.

---

