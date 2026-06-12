---
title: "unwatchable video playback on Acer Revo RL70"
date: 2012-02-05
forum: Multimedia Software
---

### Post by RoyMunson on 2012-02-05
Hi,

 I have recently installed 11.10, on an acer revo rl70. The video playback of mp4 and flash is jumpy and flash video particularly bad.

 The graphics chip is Radeon HD 6320 series, Im guessing that this is culprit for my bad experience. I have tried installing the proprietary driver from AMD and it made very little difference. 

 Has anyone managed to configure this before? or can anyone help me out. My hair is close to being torn out and i have little to spare. 

 Thanks

---

### Post by buckeyered80 on 2012-02-05
Yeah it seems to be an issue with the ATI drivers and Unity. I had the issue with my Radeon HD 4650 driver and slow screen refreshes while watching video. There are a few things that should speed it up...try this:

1.Install CompizConfig Settings Manager 
2.Click on the Composite tab, and un-check Detect refresh rate.
3. Click on the OpenGL tab.
4. Uncheck Sync to Vblank.

The OpenGL "Sync to Vblank" option seemed to slow it down alot. Give that a shot. For now, I actually went back to the open-source driver until this bug gets resolved. The open source driver for my card works great.

---

### Post by RoyMunson on 2012-02-05
Thanks for the suggestion I'll give it a try. Do you think I would see any improvement if I went to 10.04 LTS as Im not particularly desperate to use unity.

---

### Post by buckeyered80 on 2012-02-12
You could try out Gnome shell. When you log in, click on the little gear next to your name, and choose GNOME. Then see how it works.

---

