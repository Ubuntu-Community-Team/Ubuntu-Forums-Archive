---
title: "Skype 4.2 &amp; Ubuntu 12.04LTS"
date: 2013-06-10
forum: Multimedia Software
---

### Post by mcgrete on 2013-06-10
Hello,

I am posting my problem and answer; hope it helps others.

Webcam old logitech; works with Cheese, doesn't work with Skype 4.2 on Ubuntu Precise 12.04LTS.

I tried LD_PRELOADing per various posts, failed.  Found out that there are 'i386' and 'x86_64' versions to preload, e.g.

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
```

For me, Precise 12.04LTS has the 'x86_64' version, but not the 'i386'; where to find?  See this link: [http://packages.ubuntu.com/search?keywords=lib32v4l-0](http://packages.ubuntu.com/search?keywords=lib32v4l-0)

**I used Synaptic to install 'ia32-libs'**.  May be 'overkill' in terms of it loaded ~170+ libraries/files, but it will do the trick.

**Then, modified the properties of the Skype icon launcher to:**
```
env LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
```

Webcam works in Skype.  _Note: webcam will not work in Cheese and Skype at the same time._

Cheers.

---

### Post by Yellow Pasque on 2013-06-10
If you just want one 32-bit library, use this format:
```
sudo apt-get install libv4l-0:i386
```

However, you probably did need some of theother 32-bit libs that ia32-libs installs.

---

