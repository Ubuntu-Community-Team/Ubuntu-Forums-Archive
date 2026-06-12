---
title: "vlc problem: no window + giant memory consumption."
date: 2009-02-15
forum: Multimedia Software
---

### Post by Twilight in Zero on 2009-02-15
Hi. I'm having a serious problem with VLC. I don't know why it started happening. When I open VLC, no window appears. If I try to open a video with it, I can hear the sound playing, but there's no window, so no video.

It also starts to consume memory voraciously, until there's none left and the system comes to a halt. I have to killall -9 vlc before I lose all of it, else only the power button will recover my computer.

Can anyone help me?

---

### Post by Twilight in Zero on 2009-02-16
Solved. UIM was causing problems with it. I might have been able to fix it by only removing UIM's qt module, but I just removed the whole thing since I was having another zero-reply problem with it anyways.

---

