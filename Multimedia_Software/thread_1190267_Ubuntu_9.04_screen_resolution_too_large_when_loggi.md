---
title: "Ubuntu 9.04 screen resolution too large when logging in"
date: 2009-06-17
forum: Multimedia Software
---

### Post by kavoura on 2009-06-17
I recently installed Ubuntu 9.04. When it boots and I log in, I get a very large screen resolution which makes everything too small. I think it is 1280 x something. I want it set to 1152 x 864, and every time after logging in I have to access the Nvidia settings to change the resolution. If I disable the Nvidia driver, then Ubuntu starts at the correct screen resolution.

The monitor is an old CRT screen, 41 cm viewable diagonal size. 1152 x 864 seems to work best, anything bigger is no good. The CPU is an AMD64, and I have 4 GB RAM.

So how do I get Ubuntu to remember my choice of resolution for the next time I boot?

---

### Post by kavoura on 2009-06-20
I fixed it by running the Nvidia settings as root, I think I used

```
sudo nvidia-settings
```

which caused the changes in resolution to be permanently stored.

---

