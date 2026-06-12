---
title: "GStreamer Installation Plug-in"
date: 2010-04-30
forum: Multimedia Software
---

### Post by iggy pop on 2010-04-30
I am running Lucid Lynx 10.04 and have tried to add a new radio station in Rhythmbox. But when i tried to listen to the radio station i was informed: Your GStreamer installation is missing a plug-in.

Could someone please tell me what GStreamer plug-in i should install. 

Thanks

---

### Post by Fishscene on 2010-05-01
I'm running 10.04 and also having this problem, but for mp3 files. I can play the files in Movie Player, but not Rhythmbox. 

I tried the solution here: ( [https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/90242](https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/90242) ), however it could not find "gstreamer0.10-pitfdll". It manually installed "gstreamer0.10-plugins-bad". My hunch is that it is a Rhythmbox error, not the gstreamer plug-in.

Problem is still not solved.

---

### Post by tnt533 on 2010-05-11
I have this issue as well with playing mp3 files only in rhythmbox. I have zero issues in vlc and songbird.

It states,"Your GStreamer installation is missing a plug-in." even after the player automatically downloaded and installed gstreamer and I installed the medibuntu restricted formats package, w64codecs.

If I get this situation resolved, I'll post back.

---

### Post by tnt533 on 2010-05-11
If you haven't already done so, goto the link below and follow the tutoial on how to enable the medibuntu repository and also install the restricted codecs.

I did this and after restarting X with a logout, the issues with Rhythmbox went away. 


[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

