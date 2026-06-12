---
title: "pusleaudio keep changing its default port from 4713"
date: 2015-05-25
forum: Multimedia Software
---

### Post by odror on 2015-05-25
I would like to set pulseaudio as a server. Many times it changes the default port from 4713. Is there a way to prevent that.

netstat -atlpvn | grep pulseaudio:
```
tcp        0      0 0.0.0.0:38100           0.0.0.0:*               LISTEN      15906/pulseaudio
tcp        0      0 0.0.0.0:46228           0.0.0.0:*               LISTEN      15906/pulseaudio
tcp        0      0 0.0.0.0:41079           0.0.0.0:*               LISTEN      15906/pulseaudio
tcp        0      0 0.0.0.0:40825           0.0.0.0:*               LISTEN      15906/pulseaudio
tcp        0      0 0.0.0.0:52999           0.0.0.0:*               LISTEN      15906/pulseaudio
tcp6       0      0 :::34421                :::*                    LISTEN      15906/pulseaudio
tcp6       0      0 :::43677                :::*                    LISTEN      15906/pulseaudio
tcp6       0      0 :::37727                :::*                    LISTEN      15906/pulseaudio
tcp6       0      0 :::51848                :::*                    LISTEN      15906/pulseaudio
tcp6       0      0 :::45873                :::*                    LISTEN      15906/pulseaudio


```
 When I check it no other process is using that port.

netstat -atlpvn | grep 4713
```
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
```

---

