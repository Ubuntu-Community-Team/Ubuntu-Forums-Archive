---
title: "Certain files play in VNC but not in MythTV"
date: 2010-09-18
forum: Mythbuntu
---

### Post by jquintana on 2010-09-18
I have 2 files (.mpg and .mkv) that play fine in VLC but when I try to open them up in MythTV nothing happens. What I mean by nothing happens is the following:

1. Open MythTV Frontend
2. Click Media Library
3. Click Watch Videos
4. Click the movie I want to watch
5. Click Play on preview screen

At this point I get a screen that says Please Wait... and then it returns to the preview screen (where I originally clicked Play).

I have other files which play fine in MythTV just these two are causing problems.

Any help is greatly appreciated.

---

### Post by pu15e on 2010-09-18
I realise this is really no help at all, but we have one file in our library (an xvid of Coraline) which used to work, but has for the last couple of weeks simply caused the front end to drop out.

  Running .23.1-fixes, btw...

Cheers,
 Mattt.

---

### Post by goffa72 on 2010-09-19
Just a guess, but maybe the files do not have the correct permissions or ownership for mythtv.

---

### Post by nickrout on 2010-09-19
> **jquintana said:**
> I have 2 files (.mpg and .mkv) that play fine in VLC but when I try to open them up in MythTV nothing happens. What I mean by nothing happens is the following:

1. Open MythTV Frontend
2. Click Media Library
3. Click Watch Videos
4. Click the movie I want to watch
5. Click Play on preview screen

At this point I get a screen that says Please Wait... and then it returns to the preview screen (where I originally clicked Play).

I have other files which play fine in MythTV just these two are causing problems.

Any help is greatly appreciated.


for help you would need to show us your mythfrontend logs at the point where it fails to play.

---

### Post by azmyth on 2010-09-21
You can always adjust the file type to play with a different player. I have some files that use mplayer instead like mkv files. If you have your lircrc file setup properly you can use your remote with mplayer. Anyhow, look at your log files and it'll tell you exactly what's wrong.

---

