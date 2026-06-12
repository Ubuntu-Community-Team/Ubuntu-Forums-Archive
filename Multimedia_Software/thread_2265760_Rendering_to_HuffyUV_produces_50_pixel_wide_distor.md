---
title: "Rendering to HuffyUV produces 50 pixel wide distorted horizontal strip"
date: 2015-02-17
forum: Multimedia Software
---

### Post by DJonsson2008 on 2015-02-17
Using KdenLive and OpenShot on Ubuntu 14

On some of the images I render with KdenLive OpenShot with Huffy lossless profile,
I get a pattern 35-50 pixels wide occuring at the bottom of the frame.

What is odd is some image sequences don't have this pattern and some do.

Can anyone help me define or resolve this problem. 


[img]http://urbanspaceepics.com/RenderDistortionPattern.png[/img]

[img]http://urbanspaceepics.com/RenderFrameWithDistortion.png[/img]

---

### Post by FakeOutdoorsman on 2015-02-19
It's actually kind of nice lookingl it would make a nice avatar. Can you acquire the actual ffmpeg command that is being used from the profile? It would also be very useful to see the ffmpeg console output from the encoding.

You can get a [recent ffmpeg build](http://johnvansickle.com/ffmpeg/) and test that too to see if the issue has already been resolved there.

Does it occur in all players that you're tested?

---

