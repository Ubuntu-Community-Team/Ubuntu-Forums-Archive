---
title: "mismatching GLX versions"
date: 2008-10-18
forum: Multimedia Software
---

### Post by weliad on 2008-10-18
Hello, 

I have a mismatch between my server/client glx versions which are reported to be 1.4, and the GLX version which reports to be 1.3:

```
$ glxinfo | grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 2.1.2 NVIDIA 173.14.12
```

For the life of me, I have no idea what's going on. My understanding is the GLX version is the minimum between the server and client versions - so how come if both are 1.4, the resulting GLX version is 1.3?

Anyone has an idea how I can change the GLX version to 1.4?

I'm using Ubuntu 8.04.1, with an nVidia 8600GT card, and Envy installed drivers.

Thanks

---

