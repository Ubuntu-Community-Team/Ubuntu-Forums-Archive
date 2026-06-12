---
title: "Incorrect video memory reported"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by milton1 on 2007-07-14
I am having a strage issue with my system incorrectly reporting the amount of memory on my video card. The card is an nvidia 6200, 128 MB. Using nvidia-settings, the memory is reported correctly. However, lshw reports 256 MB, and I regularly get an error in wine:

fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1831f8
returning 128MB left

for some reason the message is truncating today, but the gist of it seems to be that the system thinks that I have 256MB, and am only using 128MB.

I am currently running the 9755 drivers from nvidia (I can't seem to get the 100.14 drivers to install).

Any thoughts on why this is reporting wrong?

---

### Post by wolfen69 on 2007-07-14
run this in terminal:
```
sudo dpkg-reconfigure xserver-xorg

```
enter amount of RAM manually. example: 256MB=256000 KB

---

### Post by milton1 on 2007-07-14
I'll consider it, though I would rather not have to reconfigure what is otherwise a functional system.

A question, though,

> enter amount of RAM manually. example: 256MB=256000 KB 

would it need to be 256MB = 262144 KB?

---

### Post by milton1 on 2007-07-14
Tried the reconfigure. It didn't help. Any other ideas?

---

