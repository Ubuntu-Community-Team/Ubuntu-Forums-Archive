---
title: "NVidia and projector as 2nd screen"
date: 2009-01-24
forum: Multimedia Software
---

### Post by cronholio on 2009-01-24
What is a good way to setup a projector as a second screen to watch movies? My main screen is a 1680x1050 display and the projector's resolution is 1280x800. I want to be able to show movies full-screen on the projector. The only way I can do that is by placing both screens on top of each other and change the resolution of my main screen in the NVidia X server settings to 1280x800. Any ideas how this can be achieved in a more comfortable way?

---

### Post by IanW on 2009-01-24
If you're using Totem, have you tried Edit/Preferences/General - "TV-Out in fullscreen by Nvidia"?

For VLC, use Tools/Preferences/(show all - button at bottom left), then select Video/Output Modules/XVideo,
 and change the value in "Screen for fullscreen mode" until you have your movie on the projector.

Unfortunately, I don't know the equivalent option for MPlayer.

---

### Post by cronholio on 2009-01-24
Thanks a lot, I never knew there were options like these. I'll give it a try.

Anyone know how this could work with gxine? It's the only player that will show DVDs properly on my system.

---

