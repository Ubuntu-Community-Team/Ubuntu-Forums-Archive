---
title: "Open Movie Editor"
date: 2010-04-20
forum: Multimedia Software
---

### Post by conradin on 2010-04-20
Hi all, 
I am new to viedo editing so please go easy on me. I have a bunch of avi films I want to select clips from to play with them later. I installed Open Movie Editor, and KDEnlive I still havent figured out how to remove 3 minute clips from the films. Can anyone point me to a tutorial, or give me a walk through on editing videos? I was hoping this process would be like editing audio with audacity, simple and intuitive. Is there better software I should be using?

---

### Post by WinterRain on 2010-04-20
[KdenLive Video Tutorials]("http://www.kdenlive.org/tutorial")

[KdenLive User Guide]("http://www.kdenlive.org/user-manual")

---

### Post by JamezQ on 2010-04-20
Pitivi, really simple to crop video in.

---

### Post by bryanl on 2010-04-20
There are so many options. Pitivi seems hot right now and [OpenShot Video Editor]("http://www.openshotvideo.com/feeds/posts/default")
is also getting some raves. 

For longer videos, like I get from recording movies from TV, I use avidemux. The others I have tried do not seem well suited for long video segments. Avidemux works well to cut commercials and other extraneous material. It does need to index mp2 files and I find I often need to adjust the lip sync but it does allow good control of codecs and containers in and out and scanning the video and cutting out stuff is simple.

Video has many gotchas. AVI, for instance, is one container of many that has video and audio inside it with some additional information to keep them synchronized. Both the video and audio are encoded in one of a whole mess of possible codecs. Trying to get the right audio and video codecs in the proper container for a particular playback device can be a challenge.

Then there's the problem of decompression in order to edit. This can be trivial or not depending upon the codec and it will always create some loss in fidelity. Decoding the audio and video for editing is one of the startup activities that can take a while when preparing a video for editing. This process is needed because video codecs don't just compress frame by frame, which is how you'd like to edit, but rather by groups of frames. The editor has to handle this somehow. Avidemux allows jumping by groups to make clean ends on cuts, for instance. Others may deconstruct everything to independent frames but that requires a whole lot of memory.

Video is inherently more 'interesting' than audio so editing needs a lot more computer and much smarter software to help you out. Take some time and look through Ubuntu's repositories to test some of the video editors there. Each will need some time and effort to see what they offer but you'll learn a lot about what you want to do and how to do it in the process. Have fun.

---

### Post by conradin on 2010-04-20
Thanks for the advice JamesQ! Pitivi was easy to figure out and use.

---

