---
title: "VLC Interface not normal"
date: 2009-09-13
forum: Multimedia Software
---

### Post by gobberpooper on 2009-09-13
What's up with the Ubuntu interface of VLC? It's really starting to bother me now. First off, the video output and interface are different windows which really annoys me. In fullscreen I would be able to see the controls when I move my mouse. But because the controls are in a separate window, the video output covers it up in fullscreen.

In the options I have integrate video in interface checked. idk why it doesn't work.

The first picture is mine in windows mode, the second is the one my dad has on his laptop(vista). The third is mine in fullscreen, the fourth is an image from google images in fullscreen.

---

### Post by scragar on 2009-09-13
This was caused by an error in VLC on linux which caused it to crash if the video output was launched in the same window as the menu's. It has been fixed upstream at the moment, but the ubuntu repos are slightly behind.

Essentially you can either wait for ubuntu to update and impliment these changes, or you can update it yourself(which could be rather complicated).

---

### Post by binbash on 2009-09-13
Read this post : [http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

---

### Post by gobberpooper on 2009-09-13
> **scragar said:**
> This was caused by an error in VLC on linux which caused it to crash if the video output was launched in the same window as the menu's. It has been fixed upstream at the moment, but the ubuntu repos are slightly behind.

Essentially you can either wait for ubuntu to update and impliment these changes, or you can update it yourself(which could be rather complicated).

Awesome awesome awesome. works wonderfully now. For those of you who would like to know how to update VLC to get fullscreen controls and integrated video output, add 
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main 

[FONT=Verdana]to you repositories(or hardy or intrepid depending on your version). Then go to synpatic,
search for "vlc", and upgrade vlc which will also upgrade several other libraries and
packages. Wait for it to download and then install and enjoy a less annoying version!
[/FONT]

---

