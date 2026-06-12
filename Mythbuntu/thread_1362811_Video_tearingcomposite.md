---
title: "Video tearing/composite"
date: 2009-12-23
forum: Mythbuntu
---

### Post by leeko on 2009-12-23
Hi,

I'm running Mythbuntu 9.10 on a Zotac ionitx motherboard with onboard nvidia 9400M graphics. I'm having some problems with video tearing, and have tried the various fixes on the mythtv wiki, including OpenGL sync to vblank. 

The thing that fixed it for me was the command:

```
sudo nvidia-xconfig --no-composite
``` 

This turned off compositing, which completely fixed the video tearing issue. I can live without compositing, BUT - now, whenever anything appears in front of the playing video, it stays on-screen and doesn't disappear. 

For example, the xfce volume control persists after a change is made. If I alt-tab to another window, then alt-tab back to the playing video, I still see the other window, and the alt-tab dialogue in front of the video. All of these persist until I stop the video - the mythtv menus work fine. Interestingly, the transparent mythtv OSD works fine - i.e. it shows up, then fades away as it should. 

Obviously, this makes myth unusable for me. Can anyone help me figure out a way to get rid of the tearing without this redrawing issue? 

Thanks in advance,

Lee

---

