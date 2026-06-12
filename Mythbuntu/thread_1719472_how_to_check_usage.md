---
title: "how to check usage?"
date: 2011-04-01
forum: Mythbuntu
---

### Post by nhtrader on 2011-04-01
I'm interested in checking/tracking the usage of recordings and videos. 

Is there a log file for this purpose?

Is there a script that scans for usage?

Is there a log file that contains entries when a file is playing?

---

### Post by nickrout on 2011-04-01
/var/log/mythfrontend.log

---

### Post by nhtrader on 2011-04-02
> **nickrout said:**
> /var/log/mythfrontend.log


in version 0.24-235 it's now /var/log/mythtv/mythfrontend.log

I didn't find the entry naming the file being played...

2011-04-02 08:40:05.880 TV: Attempting to change from None to WatchingPreRecorded
2011-04-02 08:40:06.207 AFD: Opened codec 0xa43a71a0, id(MPEG2VIDEO) type(Video)
2011-04-02 08:40:06.207 AFD: codec AC3 has 2 channels
2011-04-02 08:40:06.208 AFD: Opened codec 0xa43a7760, id(AC3) type(Audio)
2011-04-02 08:40:06.208 AFD: codec AC3 has 1 channels
2011-04-02 08:40:06.209 AFD: Opened codec 0xa43a7e90, id(AC3) type(Audio)
2011-04-02 08:40:06.346 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2011-04-02 08:40:06.388 ALSA, Error: Setting hardware audio buffer size to 6016
2011-04-02 08:40:06.388 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-04-02 08:40:06.388 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-04-02 08:40:06.388 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2011-04-02 08:40:06.433 AudioPlayer: Enabling Audio
2011-04-02 08:40:06.614 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2011-04-02 08:40:06.649 OSD: Base theme size: 1280x720
2011-04-02 08:40:06.649 OSD: Scaling factors: 0.4125x0.666667
2011-04-02 08:40:06.675 OSD: Base theme size: 1280x720
2011-04-02 08:40:06.675 OSD: Scaling factors: 0.4125x0.666667
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 528 x 480
YadifDeint: Using existing thread.
2011-04-02 08:40:06.679 Player(1): Video timing method: USleep with busy wait
2011-04-02 08:40:06.679 TV: Changing from None to WatchingPreRecorded
2011-04-02 08:40:06.753 VideoOutput: Created YV12 OSD.
QPainter::begin: Paint device returned engine == 0, type: 3
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::setPen: Painter not active
QPainter::setBrush: Painter not active
QPainter::drawRects: Painter not active
QPainter::end: Painter not active, aborted
QPainter::begin: Paint device returned engine == 0, type: 3
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::setPen: Painter not active
QPainter::setBrush: Painter not active
QPainter::drawRects: Painter not active
QPainter::end: Painter not active, aborted
QPainter::begin: Paint device returned engine == 0, type: 3
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::setPen: Painter not active
QPainter::setBrush: Painter not active
QPainter::drawRects: Painter not active
QPainter::end: Painter not active, aborted

BTW, this Qpainter:: sequence repeats a few hundred times...


But no where can I find the filename being played. 

Where can I find the name of the file being played?

---

### Post by nickrout on 2011-04-02
yeah sorry about the wrong path to the log.

I was sure it gave a message about what file was being played, but I can't see it in my log file either.

---

### Post by chrisblue on 2011-04-13
I have recently been having a detailed look at the logs to try to track down a FE crash and I have found that my log file mostly tells me what has been played but it may not be so easy to cull just that info from everything else in the log........oh and sometimes it doesn't.

---

### Post by nickrout on 2011-04-13
you realise that the database has info on whether a recording has been played (but maybe not when).

---

