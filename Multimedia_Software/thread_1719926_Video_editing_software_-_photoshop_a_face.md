---
title: "Video editing software - photoshop a face"
date: 2011-04-02
forum: Multimedia Software
---

### Post by mrmoney on 2011-04-02
Hey,

I am looking to create a short video with a friend's face overlayed the original in the video. I am not an experienced video editor so I am looking for any tips on what would be the best/easiest software to use to accomplish this task. It doesn't need to be able to produce the best ultimate quality, I am looking for ease of use and less effort into getting it done.

I have kdenlive and pitivi installed. I don't think it is possible in pitivi, but perhaps in kdenlive? I haven't figured out how to do it yet though. I am willing to try out any other free alternatives as well.

Thanks for any help, much appreciated

---

### Post by mrmoney on 2011-04-02
Also,

as an alternative, I've already ripped the frames of my video into separate images. If there was a program that could import them all and recreate a video while allowing for some simple image editing I'd be willing to try that route

---

### Post by cotcot on 2011-04-02
I guess that you want that the head of your friend moves like the head in the original video ? This is motion track.

This is not possible in kdenlive. As far as I know it is possible in blender. But not easy. I have not done this yet but searched a few times how to do this. I used a work around by trimming the movement of the head with location keyframes on the path of the video. The head is a .png image (head on transparent background; png supports the transparent or alpha channel). With "alpha over" effect in blender I layed the head over the video. Then I tried to let the head of the image follow the head of the video with location keyframes on the x and y of the "transform" effect.

---

