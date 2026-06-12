---
title: "VX-1000 in skype"
date: 2010-05-02
forum: Multimedia Software
---

### Post by Twyxx on 2010-05-02
My webcam (lifecam vx-1000) doesn't load in skype. When I click "test," the green LED on the camera flashes but turns off shortly after. It works in Cheese and XawTV, however it does not work in Camorama either. Anyone else have this problem? Thanks

New install of Ubuntu 10.04

---

### Post by jelofson on 2010-05-03
> **Twyxx said:**
> My webcam (lifecam vx-1000) doesn't load in skype. When I click "test," the green LED on the camera flashes but turns off shortly after. It works in Cheese and XawTV, however it does not work in Camorama either. Anyone else have this problem? Thanks

New install of Ubuntu 10.04

Probably the V4L compatibility issue.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

I have the video working, but never the microphone.

Let me know if that works for you.

I have a little script I run that you can use if you don't want to edit the main menu entry.

```

#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
exit 0

```

Enjoy :)

---

