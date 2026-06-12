---
title: "nautilus thumbnails - no preview for .flv files"
date: 2009-05-24
forum: Multimedia Software
---

### Post by fermulator on 2009-05-24
Would anyone be able to assist me in troubleshooting this?  I'm fluent with Linux, however I'm just not sure how to troubleshoot this problem.

I've got some files in my video collection saved from youtube as *.flv (flash video) files.  When you view the Videos directory in ubuntu, the nautilus thumbnailer conveniently creates a thumbnail for all the video files.

The thumbnails show up for all all (.avi .mpeg .wmv, etc.) except *.flv.

Any idea(s) why?

---

### Post by fermulator on 2009-06-12
Any tips for enabling video preview for *.flv files?  Still haven't figured it out.

---

### Post by malleeblue on 2009-07-07
I'm having the same issue with the only difference being that I don't have thumbnails displaying for mpg files either. I'd be keen to know if there's a fix for this.

I've got:
» Jaunty Jackalope
» Gnome 2.26.1
» Kernel 2.6.28-13-generic

with these GStreamer plugins installed:
» gstreamer0.10-plugins-bad
» gstreamer0.10-plugins-bad-multiverse
» gstreamer0.10-plugins-base
» gstreamer0.10-plugins-base-apps
» gstreamer0.10-plugins-good
» gstreamer0.10-plugins-ugly-multiverse

---

### Post by fermulator on 2009-07-25
bump (sorry!)

---

### Post by xc3RnbFO8P on 2009-07-25
> gconf-editor

Desktop> Gnome> Video@ x-flv, Enable check box

---

### Post by fermulator on 2009-07-25
It is checked.

Desktop> Gnome> Thumbnailers > Video@ x-flv
> command: /desktop/gnome/thumbnailers/video@flv/command
enable: true

stumped.

---

### Post by lbharti on 2009-08-16
Find the solution at [http://fixed-it.blogspot.com/2009/08/nautilus-ubuntu-missing-thumbnails.html](http://fixed-it.blogspot.com/2009/08/nautilus-ubuntu-missing-thumbnails.html)

---

