---
title: "Youtube videos have blue faces and such"
date: 2014-02-19
forum: Multimedia Software
---

### Post by merlinus on 2014-02-19
All youtube videos now have blue faces and such.  I am using 12.04 and this happens with both Firefox and Opera.

---

### Post by howefield on 2014-02-19
Try this thread for various solutions.

[http://ubuntuforums.org/showthread.php?t=2043694](http://ubuntuforums.org/showthread.php?t=2043694)

---

### Post by papibe on 2014-02-19
Hi merlinus.

Are you using the Nvidia proprietary driver by any chance? If so, there's a chance you are experiencing a known bug. Disable Flash hardware acceleration, and you'll be OK (check this [thread]("http://ubuntuforums.org/showthread.php?t=1949137&highlight=youtube")).

Also, I would recommend joining the [youtube HTML5]("http://www.youtube.com/html5/") player trial, to use the browser's embedded player instead of Flash (when available).

Regards.

---

### Post by monkeybrain20122 on 2014-02-19
This only affects Youtube, so just don't use flash on Youtube.
[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)
Works much better than flash anyway if you have a Nvidia card and use gecko-mediaplayer as the backend, configure gnome-mplayer to output as vdpau, you get full hardware acceleration.

Updating Nvidia driver may also help, since I think it has been fixed by Nvidia. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by merlinus on 2014-02-19
This worked for me, and I did not have to disable acceleration:

cd /usr/lib/flashplugin-installer || cd /usr/lib/adobe-flashplugin/
sudo perl -pi.bak -e 's/libvdpau/lixvdpau/g' libflashplayer.so

Thanks very much to everyone!

---

### Post by monkeybrain20122 on 2014-02-20
BTW, you can watch all Youtube videos in html5 now
[https://addons.mozilla.org/en-US/firefox/addon/youtube-flash-to-HTML5/](https://addons.mozilla.org/en-US/firefox/addon/youtube-flash-to-HTML5/)

---

