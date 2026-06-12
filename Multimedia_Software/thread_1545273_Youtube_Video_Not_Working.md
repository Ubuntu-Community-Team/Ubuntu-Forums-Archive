---
title: "Youtube Video Not Working"
date: 2010-08-03
forum: Multimedia Software
---

### Post by lege101 on 2010-08-03
Lately when I try to watch a video on Youtube.com it won't play the video correctly. It would speed through the video and no sound would come out. I tried using headphones to see if the sound would come out then but it didn't. But when I listen to music on like a profile or listen to music from my computer it works. It seems that Youtube is thee only thing not working. Any suggestions would be greatly appreciated.

I have tried: sudo apt-get install flashplugin-installer 
and: sudo apt-get install ubuntu-restricted-extras
but the videos still do not work.

---

### Post by Cavsfan on 2010-08-03
Try this FF addon created by **lovinglinux**
While I find the workaround which you may need to.

_[ https://addons.mozilla.org/en-US/firefox/addon/161939/]("https://addons.mozilla.org/en-US/firefox/addon/161939/")_

---

### Post by Cavsfan on 2010-08-03
**gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer**

Then add: **"export GDK_NATIVE_WINDOWS=1**" before the last line of text
(without the quotes).

Save it and restart browser.

---

### Post by lege101 on 2010-08-03
okay thank you

---

