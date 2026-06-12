---
title: "Webcam compression/quality issue"
date: 2012-08-02
forum: Multimedia Software
---

### Post by Jursinoff on 2012-08-02
I have a problem with webcam, where colors get distoted. I have multiple computers, and the problem exists on two of four computers. 

The two computers that don't have the problem run Ubuntu 10.04. And the Two that have the problem run on ubuntu 11.04 and 12.04.

I run a Qt-based program that streams webcam video. I'm also quite certain this issue is not caused by the Qt code since the problem can be seen with other webcam softwares aswell.

I've tried to track the problem and it might have something to do with mjpg output. Changing the camera output to RGB3 for example removes the problem but sadly that fix cannot be used in my case.

So far I've tried to find some kind of settings for MJPG compression but no luck there.

The problem is clearest when you have two bright colors against eachother in an angle, the distortion reminds of very low quality jpg distortion. 

Few images showing the issue:

Cola bottle: As you can see the hand is perfectly clear but the red label of the bottle is distorted somehow.

[IMG]http://i6.aijaa.com/b/00834/10634176.jpg[/IMG]

PostIt: Again the red color gets messed up with the white background but the rest of the image is clear.

[IMG]http://i5.aijaa.com/b/00902/10634177.jpg[/IMG]

---

### Post by Jursinoff on 2012-08-08
Would appreciate any help. Google hasn't got anything to offer to on this issue.

---

