---
title: "Issues with Sound and modifying Alsa files"
date: 2010-07-22
forum: Multimedia Software
---

### Post by gregc72 on 2010-07-22
I just installed 10.04 on my Alienware. If I plug my headphones in it does not mute my laptop speakers. I have lurked the forums read a few suggestions that involve modifying the Alsa-base.conf file but when I try and modify me it doesn't give me the option to save. I'm assuming because I'm not root but shouldn't it give me the option to sign in with my password to allow modification?
 
I've installed alsa and tried clicking the headphones button and it just mutes everything. If I unmute the headphones click disappears there is no sliders for the headphone option. I have a HDA Intel : Realtek ALC889A.

---

### Post by gregc72 on 2010-07-22
This is what my mixer looks like.

---

### Post by Yellow Pasque on 2010-07-22
To edit as root:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

