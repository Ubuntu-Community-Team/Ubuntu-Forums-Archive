---
title: "Program closes after opening a video file"
date: 2009-01-21
forum: Multimedia Software
---

### Post by tbrminsanity on 2009-01-21
I first noticed this problem with Miro, every time I try to open a video file it closes the program trying to run the video.  I've had this happen with every video program on my system.  

I have an ATI Raidon X1600 Graphics card, Ubuntu 64-bit, Core 2 Duo, and 2GB RAM if that helps.

---

### Post by hal8000 on 2009-01-21
Start miro or your other apps from the terminal, when the program exits, some useful info may be displayed

---

### Post by siefer132 on 2009-01-21
i seem to have the same problem. Movie Player crashes whenever i try to play a video. how would I launch Movie Player from the terminal?

---

### Post by siefer132 on 2009-01-21
bump

---

### Post by 2hot6ft2 on 2009-01-21
Do you have all the needed codecs to be able to play sound and videos?
You can install most of them by doing the following.

Put this in a terminal and hit Enter
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

Then your password and Enter (your password will not be displayed)

It will fix that as well as other missing multimedia you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.

---

### Post by 2hot6ft2 on 2009-01-21
> **siefer132 said:**
> i seem to have the same problem. Movie Player crashes whenever i try to play a video. how would I launch Movie Player from the terminal?
You would open a terminal
Applications>Accessories>Terminal
and put in ```
mplay
``` and hit Enter

I like vlc player better it can be installed using
```
sudo apt-get install vlc
```

---

### Post by tbrminsanity on 2009-01-21
Here is the terminal output from vlc when it crashes:

QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

(process:7314): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(process:7314): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(process:7314): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(process:7314): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


I have the restricted extras loaded already.

---

### Post by siefer132 on 2009-01-21
Hey,

I have VLC installed, it crashes too, and i have the restircted things installed too. when i type in ```
mplay
``` in terminal then hit enter it says```
bash: mplay: command not found
```

ok this is what i get when i open vlc with terminal and then open a video file ```
mdb:13, lastbuf:0 skipping granule 0
QPainter::begin: Paint device returned engine == 0, type: 1
mdb:26, lastbuf:13 skipping granule 0
mdb:39, lastbuf:26 skipping granule 0
mdb:52, lastbuf:39 skipping granule 0
mdb:65, lastbuf:52 skipping granule 0
mdb:78, lastbuf:65 skipping granule 0
mdb:91, lastbuf:78 skipping granule 0
mdb:104, lastbuf:91 skipping granule 0
mdb:117, lastbuf:104 skipping granule 0
mdb:130, lastbuf:117 skipping granule 0
mdb:143, lastbuf:130 skipping granule 0
mdb:156, lastbuf:143 skipping granule 0
mdb:169, lastbuf:156 skipping granule 0
mdb:182, lastbuf:169 skipping granule 0
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

```

EDIT: Its a video driver issue. k so now its flashing.

Edit 2: mmkmay so i just switched back to metacity and it stopped flashing. try installing your restricted video driver, go to System -> Administration -> Hardware Drivers.

---

### Post by tbrminsanity on 2009-01-22
I loaded the propriatary drivers for my graphics card and the problem has disapeared.  Thank you everyone.

---

### Post by tbrminsanity on 2009-01-22
Now I'm having the problem that my video is flashy.  Any suggestions?

---

