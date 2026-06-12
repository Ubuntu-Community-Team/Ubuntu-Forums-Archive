---
title: "Feisty, Mythtv, IVTV, PVR-500 picture quality"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by Staudie on 2007-04-18
I'm trying to improve the picture quality of my PVR-500 by changing the temporal_filter value.
Reference links:

[http://www.gossamer-threads.com/lists/ivtv/users/33616?#33616]("http://www.gossamer-threads.com/lists/ivtv/users/33616?#33616")

[http://www.gossamer-threads.com/lists/ivtv/users/33617?#33617]("http://www.gossamer-threads.com/lists/ivtv/users/33617?#33617")

When I do a:

```
v4l2-ctl -d1 -l
```

It tells me the value is 0, so I:

```
v4l2-ctl -d1 -c temporal_filter=8
```

followed by  ```
v4l2-ctl -d1 -l
``` to make sure the change went through. This shows that the new value but when I launch MythTV there is no change is picture quality. So I exit and run a ```
v4l2-ctl -d1 -l
``` again the value has gone back to 0. It think ivtv is resetting back to defaults.

How can I get this to stick?

Thanks
-Staudie

---

### Post by backwardselvis on 2007-04-18
Same issue here! :confused:  Would love a response.

-thanks
be

---

### Post by majoridiot on 2007-04-18
is it being reset due to your capture resolution?  according to the info, that setting will *reset* if you are capturing
at a scaled resolution.

check your settings in the frontend-

setup-->tv settings-->recording groups

and make sure *both* the *Default* and * pvr* settings for capture resolution are set to 720x480- see if the
change to that filter value will then stick.

---

