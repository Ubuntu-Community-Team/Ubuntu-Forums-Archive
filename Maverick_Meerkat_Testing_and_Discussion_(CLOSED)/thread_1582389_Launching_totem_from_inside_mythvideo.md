---
title: "Launching totem from inside mythvideo"
date: 2010-09-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by FishRCynic on 2010-09-26
maverick amd64
amd x2 5000, 4gb ram nvidia 9500 500gb hardrive

installed mythfrontend to work with amd64 lucid backend
(updated lucid backend from myth dailies to fix protocol error)

The mythvideo directories are samba shares from another lucid amd64 machine
(desktop operating system though it is acting as a file server presently)

i launch totem for video playback on the lucid machines through the mythfrontend mythvideo interface  (using totem --fullscreen) for rmvb files as playback is much better with totem.

with maverick mythfrontend mythvideo
setup maverick to do the same but though totem is run and the correct file is referenced, the video does not play.  Tried to play standard avi and even mp3 loaded from the totem menu and they will not play.
the same files rmvb playback is unwatchable but avi play normally with the mythfrontend mythvideo internal player

loading totem without mythfrontend plays the file(s) without any issues.

i am not sure what would stop totem playing when launched inside mythfrontend and though i am investigating myself i would appreciate any thoughts as to cause.

Nevermind - changing mythfrontend sound to pulseaudio appears to have fixed the issue (requires mythfrontend restart)

---

