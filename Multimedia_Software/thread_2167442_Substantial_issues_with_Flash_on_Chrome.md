---
title: "Substantial issues with Flash on Chrome"
date: 2013-08-13
forum: Multimedia Software
---

### Post by Hakura on 2013-08-13
Hi.

I've installed Ubuntu 12.04 LTS on my machine a couple of weeks ago after a long time without using Linux. I'm still a beginner and I'm pretty clueless about most things, but I certainly have the last version available of Adobe Flash:

> flashplugin-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  ttf-dejavu-extra libunistring0:i386 java-common libgomp1:i386 libcroco3:i386
  tzdata-java libgettextpo0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.


I was having this issue with Chrome's built-in Flash plug-in when I tried to watch YouTube videos on full screen. It would work normally and I was able to watch the whole video on full screen, but when I tried to quit it and get back to my browsing, the screen would turn white and nothing I tried to do made the system work again. Sometimes I'd try to quit the full screen mode while the video was playing and the sound kept working, so I think the system didn't actually stop, it's only Flash that messed with my graphics. So I went looking and found out about Chrome's integrated plug-in. I disabled it and left the system plug-in enabled.

For some reason, with this config, YouTube videos are behaving in an odd way. Sometimes I can actually get the full screen to work, and sometimes it just freezes and *compiz* crashes. I came here because lately every time I try to play something on full screen I get a compiz crash and the video stops working.

I really prefer using Chrome on Linux, Firefox bothers me a lot and I don't want to switch just because of this.

Am I doing something wrong? Why is the latest Flash plug-in doing this? Am I the only one?

Any help would be really appreciated.

PS: Sorry, I forgot to add a prefix.

---

### Post by tgalati4 on 2013-08-13
Are you sure it is a flash problem?  Many videos are encoded to stream using HTML5 under Chrome.  It's possible that your computer's graphic chip has a hard time rendering full-screen, and thus causes other desktop/graphic issues.  If you really had a flash issue, you would get an error to that effect.

Try running the error console in Chrome and see if there are any obvious error messages.

---

