---
title: "KDENLIVE seg faulting after upgrade attempt"
date: 2009-08-05
forum: Multimedia Software
---

### Post by bobnutfield on 2009-08-05
Hello Everyone,

As far as movie editing goes, I have really buggered my system.  I was using Kdenlive 7.3, which was a little buggy but usable, on Ubuntu Gnome. It was working fine for the most part.  I followed a number posts on the Kdenlive forum on upgrading to the latest .7.5 version which supposedly fixed a number of bugs.  To do this, I had to enable a PPA repo from launchpad and then do the upgrade.  Well, it removed or destroyed VLC, and then immediately seg faulted when I tried to start it.

No big deal, I thought, I will just remove the repo, purge Kdenlive, and reinstall both VLC and Kdenlive .7.3 from the Jaunty repo.  VLC reinstalled and seems to work ok, but, now no matter what I try, Kdenlive will not run and continues to seg fault.  Because I am running Ubuntu and not Kubuntu, there is not much information on the crash:

```
kdenlive(4629) MainWindow::parseProfiles: RESULTING MLT PATH:  "/usr/share/mlt/profiles/"
mlt_repository_init: failed to dlopen /usr/lib/mlt/libmltavformat.so
  (libfaad.so.0: cannot open shared object file: No such file or directory)
kdenlive(4629) initEffects::parseEffectFiles: //  INIT EFFECT SEARCH
kdenlive(4629) Render::Render: //////////  USINGÂ*PROFILE:  hdv_1080_50i
kdenlive(4629) Monitor::Monitor: /////// BUILDING MONITOR, ID:  67109363
kdenlive(4629) Render::Render: //////////  USINGÂ*PROFILE:  hdv_1080_50i
kdenlive(4629) Monitor::Monitor: /////// BUILDING MONITOR, ID:  67109545
QPainter::fontMetrics: Painter not active
kdenlive(4629) RecMonitor::RecMonitor: /////// BUILDING MONITOR, ID:  67109588
kdenlive(4629) MainWindow::loadPlugins: // PARSING FIOLER:  "/usr/lib/kde4/"
kdenlive(4629) MainWindow::loadPlugins: // FOUND PLUGIN:  "libkdenlive_sampleplugin.so" =  "/usr/lib/kde4/libkdenlive_sampleplugin.so"
kdenlive(4629) MainWindow::addToMenu: // ADD to MENU ("Countdown", "Noise")
kdenlive(4629) KdenliveDoc::setProfilePath: KDEnnlive document, init timecode from path:  "hdv_1080_50i" ,   25
kdenlive(4629) KdenliveDoc::KdenliveDoc: KDEnlive document, init timecode:  25
kdenlive(4629) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  4 , DURATION:  0
kdenlive(4629) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  3 , DURATION:  0
kdenlive(4629) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  2 , DURATION:  0
kdenlive(4629) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  1 , DURATION:  0
kdenlive(4629) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  0 , DURATION:  0
kdenlive(4629) TrackView::parseDocument: ///////////  TOTAL PROJECT DURATION:  300
kdenlive(4629) Render::setSceneList: // NEW SCENE LIST DURATION SET TO:  0
KCrash: Application 'kdenlive' crashing...
sock_file=/home/bob/.kde/socket-bob-laptop/kdeinit4__0
**Warning: connect() failed: : No such file or directory**
KCrash cannot reach kdeinit, launching directly.
```

Used to run just fine in Gnome and I should have left it alone, but that is water under the bridge.  I have sought help on the Kdenlive forum, but it is not very active and I have gotten no help.  I assume the highlighted line in the crash is the problem, but have no idea what that is.

I have reinstalled, purged, and reinstalled a number of times, so it has to be something that was removed in the attempt to reinstall, but I cannot find it.  To be honest, I doubt if anyone is going to be able to help with this, short of a system reinstall, which I am not going to do.  If I can't sort this out, I will just use it on another distro from another computer which is not as powerful as this one, so that is not the best solution.

If anyone can help, I would appreciate it.

Bob


EDIT:  A number of other video related libraries must be upgraded as well.  Why they were not upgraded during the initial install/upgrade I do not know.  Once these files were upgraded, KDEnlive 0.7.5 launched fine.

---

