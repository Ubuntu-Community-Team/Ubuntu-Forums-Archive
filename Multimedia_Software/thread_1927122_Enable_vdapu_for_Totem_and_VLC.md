---
title: "Enable vdapu for Totem and VLC"
date: 2012-02-17
forum: Multimedia Software
---

### Post by AlexanderSupertramp on 2012-02-17
I just installed Asus nVidia GTS450, and nvidia-current. I had to set preferences in SMPLAYER so it uses vdpau to get the video playback, it was blank otherwise. Now SMPLAYER plays properly but Totem and VLC still does not show video, most probably they are not using vdpau. I have been using VLC as my default player till today. Youtube videos work properly in browser.

EDIT : SMPLAYER is not playing mkv files which were playing before installing card and drivers

Any tips?

---

### Post by Yellow Pasque on 2012-02-17
VLC doesn't have direct vdpau, but you can use the va-api -> vdpau wrapper: [http://askubuntu.com/a/100983](http://askubuntu.com/a/100983)

---

