---
title: "Mythbrowser missing in 9.04"
date: 2009-05-06
forum: Mythbuntu
---

### Post by wizgnome on 2009-05-06
I installed 9.04 yesterday and had a couple of problems. 
The video manager had a IMDB search box on screen - which I managed to fix by editing the line in the video-ui.xml file from <container name="enterimdb"> to <container name="entertmdb">

Then I saw that the web browser, Mythbrowser was missing. After searching around I found that it has been removed from the distribution. Its a shame that the mythbuntu.org relase notes did not contain a warning about it. :(

---

### Post by David Valentine on 2009-05-12
Thanks for your post--I had wondered about mythbrowser and why I couldn't find it.  But the real reason i'm responding is because I need to edit the file you mentioned--could you specify the path to it?:P

---

### Post by funkydan2 on 2009-05-13
Seems like it may have been broken - maybe at the MythTV end [https://bugs.launchpad.net/mythbuntu/+bug/353736](https://bugs.launchpad.net/mythbuntu/+bug/353736)

Is there a nice way to use Firefox with a remote control, a bit like MythBrowser? [http://www.mythtv.org/wiki/Firefox](http://www.mythtv.org/wiki/Firefox) talks about doing this, but it looks like you need MythBrowser installed for it to work.

---

### Post by SiHa on 2009-05-13
> **David Valentine said:**
> Thanks for your post--I had wondered about mythbrowser and why I couldn't find it.  But the real reason i'm responding is because I need to edit the file you mentioned--could you specify the path to it?:P

**Video-ui.xml** is one of the theme files. I'm not at home now so I've probably remembered the path slightly wrong. It'll be something like **/home/.mythtv/themes/Theme-You-Use/video-ui.xml**.

Note that the '.' in front of mythtv means the directory is hidden, so you won't see it with a simple **ls**, ```
ls -al
``` will show all files, and their properties / permissions.

---

### Post by Captain_Bodge on 2009-05-17
Mythbrowser is based on Konqueror and as such it requires a lot of KDE libraries. Unfortunately it requires KDE3 libraries which are no longer readily available in Ubuntu repos since the switch to KDE4.

From what I can read on the web, Mythbrowser is being completely rewritten to use webkit instead of Konqueror, but this will not be available until the 0.22 release of Mythtv. The advantage should be that it will be easier to make mythbrowser play flash animations etc.

---

