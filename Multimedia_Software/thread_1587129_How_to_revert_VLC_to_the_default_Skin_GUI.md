---
title: "How to revert VLC to the default Skin GUI"
date: 2010-10-03
forum: Multimedia Software
---

### Post by nogienugz on 2010-10-03
Dear All, 

I'm using VLC in ubuntu 10.10. May problem began when I DL and changed the skin of my VLC media player. After installing the new skin, the gui doesn't work. I can't open the preferences and change the skin settings from there. 

I've tried removing and re-installing VLC but, when I install it, it remembers the old skin on which I got that problem. I've tried deleting the vlc files in "/var/cache/apt/archives" and "/var/lib/dpkg/info" but, it still remembers the previous setting on which I got the this problem. 

Anybody knows how to go around with this? Thanks. 

regards,

---

### Post by mc4man on 2010-10-03
try 
```
vlc -I qt4 --reset-config
```

---

### Post by nogienugz on 2010-10-06
mc4man

Thanks!!! I Was able to reset the VLC gui. :P

regards,

---

