---
title: "DVDs won't play"
date: 2009-05-06
forum: Multimedia Software
---

### Post by Jeconti on 2009-05-06
I'm still trying to resolve whether or not this is a hardware or a software issue.

When I run it through the MythTV frontend, I select the option to play a DVD, the screen goes black for a second, then it just goes back to the frontend GUI.

I tried playing it outside of the frontend with xine and got the following error:

There is no input plugin available to handle dvd:/ Maybe MRL syntax is wrong or file/stream source doesn't exist.

Is this some xfce thing that I just don't know about? I never had a problem playing DVDs when I was running just Ubuntu.

---

### Post by khelben1979 on 2009-05-06
Look in this thread: [How can I get my videos to play]("https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html")?

Other than that, [libdvdcss]("http://en.wikipedia.org/wiki/Libdvdcss") is a library which you need to have installed in order to play DVD:s.

---

### Post by acimmarusti on 2009-05-06
Open up a terminal and do the following:

```

sudo apt-get install ubuntu-restricted-extras totem-xine
sudo /usr/share/doc/libdvdread3/install-css.sh

```

You can get any other media player (as long as it uses xine). This should work.

---

