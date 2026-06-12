---
title: "Editing the ProjectM visualisation settings for Clementine"
date: 2013-03-17
forum: Multimedia Software
---

### Post by jzemeocala on 2013-03-17
Hey everybody,

I was wondering if someone could help me figure out how to edit the transition duration for the projectM visualisations in clementine.
I have tried editing /usr/share/projectm/config.inp file but this has no effect. And I have also tried editing the /home/(username)/.config/Clementine/Clementine.conf file but the only parameter it has under the [Visualisation] header is:
geometry=@ByteArray(\x1\xd9\xd0\xcb\0\x1\0\0\xff\xff\xff\xf8\0\0\0\x18\0\0\x3\x33\0\0\x2\x17\xff\xff\xff\xf8\0\0\0\x18\0\0\x3\x33\0\0\x2\x17\0\0\0\0\0\0)

I did manage to add the parameter:
size=1024
which will successfully modiy the texture size.
So I know that there are additional parameters that can be added to this file to adjust the fine points of the ProjectM visuals in Clementine but I cannot figure out what I should put to control the smooth transition duration.



Thanks in advance

---

