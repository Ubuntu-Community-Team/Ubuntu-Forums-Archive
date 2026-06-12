---
title: "Gmail Video Chat with Opensource Video Drivers"
date: 2010-11-13
forum: Multimedia Software
---

### Post by frogotronic on 2010-11-13
is this possible?  Or does one have to use the binary blobs?

- CH

---

### Post by frogotronic on 2010-11-15
Solution Here:  [http://www.google.com/support/forum/p/chat/thread?tid=5951487b74683e9c&hl=en](http://www.google.com/support/forum/p/chat/thread?tid=5951487b74683e9c&hl=en)

```
sudo gedit /opt/google/talkplugin/envvars
``` 

Put ```
LIBGL_ALWAYS_SOFTWARE=1
``` in file.

Save and close.

Restart Firefox

- CH

---

