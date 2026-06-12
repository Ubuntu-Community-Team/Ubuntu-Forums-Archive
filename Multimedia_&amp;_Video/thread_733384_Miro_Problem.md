---
title: "Miro Problem"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by Delber on 2008-03-23
I just installed Miro on Gutsy Gibbon. I have a problem opening the application. The windows pops up and as the Miro is loading the Miro Guide, it just closes abruptly and this happens every time. Any help is appreciated. :)

---

### Post by rmtatum on 2008-03-23
Open a terminal window and type 

```
miro 2> error.log
```

Post the contents of errror.log here.

---

### Post by Delber on 2008-03-23
INFO     Starting up Miro
INFO     Version:  1.2
INFO     Revision: [https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.2/tv/resources](https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.2/tv/resources) - 6613
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/herbert/.miro/sqlitedb
TIMING   Database load slow: 1.114
INFO     Recomputing filters...
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     *** Launching Downloader Daemon ****
WARNING  Menu item action "CheckVersion" not implemented
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
alsa
oss
pulseaudio
none
file
INFO     loaded renderer 'xinerenderer'
TIMING   Icon clear: 0.010
INFO     Finished startup sequence
TIMING   idle (Finishing startup) too slow (3.054 secs)
INFO     got file:///tmp/tmpXMnoaZ.html
INFO     got file:///tmp/tmpDmmP5M.html
INFO     *** Daemon ready ***
INFO     got [https://www.miroguide.com/](https://www.miroguide.com/)
TIMING   feed update for: [http://revision3.com/diggnation/feed/quicktime-large/](http://revision3.com/diggnation/feed/quicktime-large/) too slow (0.136 secs)
TIMING   feed update for: [http://jetset.blip.tv/?skin=rss](http://jetset.blip.tv/?skin=rss) too slow (0.171 secs)
TIMING   feed update for: [http://www.kqed.org/.pod/questvideo](http://www.kqed.org/.pod/questvideo) too slow (0.133 secs)
herbert@herbert-desktop:~$ WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...

---

### Post by rmtatum on 2008-03-29
Try this thread:

[http://ubuntuforums.org/showthread.php?t=588617&page=2](http://ubuntuforums.org/showthread.php?t=588617&page=2)

---

### Post by james_xxx on 2008-03-31
I have the same problem, and have had for a long time.

Switching to IcedTea does not help a bit. Oddly, Miro is working just fine on my laptop, and I have no idea what the difference is in how it is configured vs. this desktop.

---

