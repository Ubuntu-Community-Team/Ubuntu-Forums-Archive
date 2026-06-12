---
title: "Convert avi from uyvy to rgb color format"
date: 2008-09-25
forum: Multimedia Software
---

### Post by gigi becali on 2008-09-25
Hello. Can somebody help me with an information about how to convert an uncompressed avi with UYVY color format into an uncompressed avi with RGB color format?
I've tried different methods including :
mencoder Video_0000.avi -demuxer rawvideo -rawvideo w=320:h=240:format=yuy2:fps=240000/8008 -ovc raw -o out.avi
but this result in a correct color format but with the frames incomplete an while transforming the movie i receive the next message :
Frame too small! (5580<153600) Wrong format?min 0mb A-V:0.000 [36827:0]
Pos: 2.0s 62f ( 0%) 42.47fps Trem: 0min 0mb A-V:0.000 [36827:0]

Anyway, if somebody can help me with any idea I'll be happy.
Thanks

---

