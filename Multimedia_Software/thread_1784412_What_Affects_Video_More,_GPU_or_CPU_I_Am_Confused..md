---
title: "What Affects Video More, GPU or CPU? I Am Confused."
date: 2011-06-16
forum: Multimedia Software
---

### Post by CharleyGnarly on 2011-06-16
This question relates somewhat to another question I have posted, but quite different.
I have a laptop with Ubuntu 11.04 on it. It has a built in graphics processor. I am not sure of the specs on it, but I was able to run DVDs easily on it when I had Windows XP as the OS.
I am now trying to load and edit video, but am having difficulties. My questions about that are in another thread.
My question here is this: What affects video on a computer more, the GPU or the CPU? I have received advice pertaining to the video card, but was under the impression that the CPU had more to do with the computers ability to handle video, especially getting into the hi-def range.
I recently rebuilt my desktop with a much newer processor, but with the same PCI Express video card. My old rig could not handle even 720p, but the AMD dual core I installed can play 1080p no problem. Different CPU same video card.
Sorry about the long post, but really want to get this figured out.

---

### Post by NightwishFan on 2011-06-16
Depends on what software you are running. If your video player supports gpu acceleration it will use the GPU to decode and display the video.

Video editing on the other hand probably needs more ram than just raw processing power. (except the encoding, which is probably very cpu dependant).

---

### Post by zealibib slaughter on 2011-06-16
here is a cool video by adam and jamie from the mythbusters showing the difference between video through a cpu and gpu m.youtube.com/watch?desktop_uri=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DnqdLrACBrOI&v=nqdLrACBrOI&gl=US. While this doesnt answer your question exactly it does show why a system with a powerful gpu and dedicated graphics memory excells at rendering.

---

### Post by Yellow Pasque on 2011-06-16
Your GPU is important so that you don't have to use much CPU. If your video card/driver/player doesn't support GPU accelerated decoding, then the CPU power is much more important, especially for HD stuff.

---

