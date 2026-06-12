---
title: "SMPlayer 0.6.0rc4 released"
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by rvm4000 on 2008-04-15
SMPlayer is a MPlayer frontend, developed using Qt (the current version requires at least Qt 4.2). More info [in the website](http://smplayer.sourceforge.net).

Most important changes since version 0.6.0rc3:
> 
* (Bugfix) Now DVDs start to play at chapter #1, instead of chapter #2, if using mplayer 1.0rc2 or older.
* (Fix) A delay could happen on startup if there were non local files in the recent's menu.
* (Bugfix) When using the command line options -send-action or -actions, some actions like aspect_4:3 didn't work.
* Initial support for edl files. If a file with the same name of the file to play but with extension .edl (or .EDL) exists, then smplayer will load it automatically. An edl file allows to skip or mute parts of the video.
* Possibility to automatically get info (length and name) about the files added to the playlist. This option is enabled by defaul on linux and disabled on windows (it's slow in this OS).
* Added in Preferences->General->Video an option to select the default deinterlacer.
* Added support for the mouse's buttons XButton1 and XButton2.
* Some new options have been added to the list of available actions for mouse buttons.
* Possibility to merge the 6 seeking buttons in the GUI into only two. It would only show the "rewind 10 secs" and "forward 10 secs" buttons. Keeping them pressed for a moment would popup menu with the rest of the buttons. This option is DISABLED by default and currently it can only be enabled at compile time changing the MINI_ARROW_BUTTONS define in src/guiconfig.h before compiling.


 * [smplayer_0.6.0rc4_i386.deb](http://prdownload.berlios.de/smplayer/smplayer_0.6.0rc4_i386.deb) (compiled on kubuntu 7.04)

This time there's also available a package for AMD64:

 * [smplayer_0.6.0rc4_amd64.deb](http://prdownload.berlios.de/smplayer/smplayer_0.6.0rc4_amd64.deb) (compiled on kubuntu 7.10)

---

