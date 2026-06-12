---
title: "No sound in embedded videos"
date: 2009-04-24
forum: Multimedia Software
---

### Post by lolwhites on 2009-04-24
Since upgrading to 9.04, I have no sound when playing flash videos from sites like YouTube and Vimeo. I've tried in both Firefox and Opera with the same issue. Sound is fine in other applications, however (Amarok, VLC etc).

---

### Post by dilandog on 2009-04-24
Clean install with restricted extras, same problem. No sound with embedded content.

---

### Post by michaeldt on 2009-04-24
The problem appears to be due to swfdec, which is now the default flash player in Firefox. However, there also seems to be a problem getting Adobe's flash player working. Quick workaround which worked for me in Firefox was suggested in the bug thread:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326609/comments/23](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326609/comments/23)

Download flash from Adobe's website and extract the .so file to /usr/lib/firefox-3.0.9/plugins/


Once I  did this I simply restarted Firefox, went to a page with flash and in the bottom right of the screen, clicked the blue icon and changed the flash player to Adobe's. Everything works fine now including sound.

---

### Post by lolwhites on 2009-04-24
Thanks, that worked for me!

---

### Post by dilandog on 2009-04-24
Thank you. Everything works fine.

---

### Post by lolwhites on 2009-04-25
Spoke too soon. Every time I restart, the problem returns even though the .so file is in the right place. I don't see any blue icon in the bottom right of the screen.

---

