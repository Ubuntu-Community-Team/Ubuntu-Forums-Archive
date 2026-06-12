---
title: "Has anyone solved Flash issue w/ Samsumg Chromebook?"
date: 2013-07-04
forum: Multimedia Software
---

### Post by mvlyyc on 2013-07-04
I am running 13.04 w/ xfce on Samsung Chromebook (ARM) model 303C.

I've made numerous efforts trying the latest Pepper Flash and the older (11.2) linux flash by Adope to work.
No luck so far.

Is there anyone with the same hardware and similar software setup that has been successful with getting flash to work? If so, can you share what you did to make it work?

Thanks in advance

---

### Post by Xtyn on 2013-07-12
You just have to take the flash from Chrome OS, it should be /opt/google/chrome/pepper/libpepflashplayer.so 
You need to get it to your home folder:
```
cp /opt/google/chrome/pepper/libpepflashplayer.so ~/Downloads/
```
Next, you put it on a USB stick, boot Ubuntu, copy it to /usr/lib/chromium-browser/plugins/
After that, you need to edit /etc/chromium-browser/default and put this in it:
```
CHROMIUM_FLAGS="--ppapi-flash-path=/usr/lib/chromium-browser/plugins/libpepflashplayer.so"
```
It doesn't really matter where you put it, as long as the location is correct in /etc/chromium-browser/default

---

