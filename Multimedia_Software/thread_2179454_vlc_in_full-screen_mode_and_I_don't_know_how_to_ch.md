---
title: "vlc in full-screen mode and I don't know how to change this."
date: 2013-10-08
forum: Multimedia Software
---

### Post by t0p on 2013-10-08
Yesterday I was "exploring" the functionality of vlc.  Now, when I open vlc, it's in full-screen mode and I can't figure out how to change this.  Pressing "f", Ctrl-C, Esc, and all the other things I can think of don't help.  I just got the "playlist" screen, in full screen.

A right-click lets me play a video in full-screen mode, but no controls to make it smaller.  The "corner" buttons - close, maximise, minimise - are not available.  So I can watch a video, in full-screen, and can't leave the vlc process except by using CLI,

```
pkill vlc
```

which is a tad inconvenient.  I tried removing vlc, ie

```
sudo apt-get remove --purge vlc
```
then reinstalling it... to no available.  the nigh-impossible fullscreen "playlist" screen pops up, and nothing has changed for the better.  I like vlc, but I don't like this inescapable full-screen business.  I ran an update earlier with Update Manager a short while ago, but that doesn't make any difference...
  I'm using Ubuntu 12.04, fully updated as of yesterday, if that's of any help.  I'm using a Packard Bell EasyNote TS with Intel B815,dual-core, using Ubuntu 12.04, fully updated as of yesterday if that's any help. 

Any ideas? Cheers!

---

### Post by ibjsb4 on 2013-10-08
Maybe you can blame your theme for this behavior.

Also you know you have two threads going on?

[http://ubuntuforums.org/showthread.php?t=2179452](http://ubuntuforums.org/showthread.php?t=2179452)

---

### Post by johanzebin on 2013-10-08
You may try if **vlc --ignore-config** or **deleting $HOME/.config/vlc/** helps at all...?

(I am assuming that VLC was working properly before you "explored" its functions, and therefore ignoring or deleting your settings should help.)

---

### Post by t0p on 2013-10-08
Thanks johanzebin.  **vlc --ignore-config** didn't help, but deleting **$HOME/.config/vlc/**  seems to have done the job.  As for the duplicate thread, ibjsb4,  I dunno how I did that.  But I shall mark both threads [SOLVED].

---

