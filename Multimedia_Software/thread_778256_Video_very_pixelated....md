---
title: "Video very pixelated..."
date: 2008-05-01
forum: Multimedia Software
---

### Post by toyota_f1 on 2008-05-01
Went to 8.04 recently and my video looks horrible.  Using 1080p .mkv files that look great on my other machines but this looks dithered and low res.  Originally I was looking for a fix for horizontal flicker/sync issues and wound up adding 

```

Section "Device"
	........
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option      "TexturedVideo" "off"
        .........
EndSection

```

Which appeared to fix it... I don't recally having changed anything else... but I recently did a 

```
sudo dpkg-reconfigure xserver-xorg
```

Not realizing until afterwards how little that actually changes anymore...  after that my video is back to looking terrible.  I tried adding the same lines that I did before but it still didn't do anything.  Any ideas here?

8.04 Hardy 64-bit
ATI: x1900gt - restricted drivers

I'd welcome any ideas at this point.

---

### Post by spandanj on 2008-07-08
i reported a bug with launchpad. please write comments on there to put pressure on developers to solve this.

[https://bugs.launchpad.net/ubuntu/+s...rg/+bug/231519](https://bugs.launchpad.net/ubuntu/+s...rg/+bug/231519)

---

