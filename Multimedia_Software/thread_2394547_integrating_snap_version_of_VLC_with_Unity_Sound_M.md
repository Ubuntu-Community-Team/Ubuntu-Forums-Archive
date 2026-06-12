---
title: "integrating snap version of VLC with Unity Sound Menu"
date: 2018-06-18
forum: Multimedia Software
---

### Post by nef1312 on 2018-06-18
I'm running Ubuntu 16.04.4, with the Unity desktop environment, and just installed VLC as a Snap package. I would like VLC to appear in the sound menu (e.g., as the Clementine and Pithos appear). [Note: The advantage of the new Snap version of VLC is that it works with Chromecast.]

Any help with this would be appreciated.

---

### Post by nef1312 on 2018-06-18
This was less complicated than I realized. The answer is found here. [https://forum.snapcraft.io/t/mpris-support-on-16-04-missing/2734/4](https://forum.snapcraft.io/t/mpris-support-on-16-04-missing/2734/4)

Basically, you rename /var/lib/snapd/desktop/applications/vlc_vlc.desktop as /var/lib/snapd/desktop/applications/vlc.desktop. I note, however, that the application appears under the name VLC media player. However, if you open the properties for the file, the command for the application is, before it is changed, includes the wording "vld_vlc.desktop" which you can change to vlc.desktop.

---

