---
title: "Kaffeine Blue Screen of Death"
date: 2008-05-06
forum: Multimedia Software
---

### Post by spacefreak86 on 2008-05-06
I'm surprised, but Kaffeine gave me the blue screen of death - literally. And I was able to recreate this problem. I tried playing a movie, which loaded and ran, but then I clicked on View -> Auto Resize -> Double Size. This caused my screen to turn completely blue, although I could hear the sound of the video in the background.

Alt-Tab, Alt-F4, Ctrl-Alt-Del (or its equivalent on your system), and Ctrl-Shift-F (to switch from full-screen mode) did not work. I had to manually cold-boot the system to restart.

---

### Post by spacefreak86 on 2008-05-07
After some testing, and trying to install / uninstall Kaffeine and the gstreamer plugins, as well as testing the .mpeg or .avi files on vlc and totem as well, I am having the same problem. When I play a video, it opens and plays, but then if I resize the picture at all, it replaces my screen with a blank blue screen. I did notice the video seemed to be cropped along the top with a blue bar going across. 

I tried this with four different video files, so I know it is not the video. I tried this with Kaffeine, Totem, and VLC, so it is not the video player.
The only thing left I can think of is the plugins somewhere. Unfortunately, this is beyond my knowledge. Can someone help me debug?

---

### Post by Xiong Chiamiov on 2008-05-07
If it happens with VLC as well, then it's not a codec issue, as VLC uses internal codecs (part of why it's so awesome and crappy at the same time).

On a side note, ctrl+alt+backspace restarts X, which is a good crash recovery keycombo.

---

