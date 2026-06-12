---
title: "Sound in Ubuntu Server; Sound Not Working in Gnome Ali 5451"
date: 2011-07-23
forum: Multimedia Software
---

### Post by twin_rotor on 2011-07-23
Having a bit of trouble with my sound working under Gnome, with just the primary user. If I log into Gnome under root(shame on me), everything works fine.
 
Went through most of the Ali threads and the Ubuntu sound card documentation. All test(that I've tried) work under root only. 
 
I fear the way I set this server up is my problem. Its 11.04 in the minimal server install flavor. After running it as a file server for awhile, I decided I needed to put a GUI on it so I could use mangle while I play games. I followed Ubuntu's guide to install a minimal Gnome installation.
 
The Preferences>Sound tab under the primary user does not show any hardware. It looks fine under root.
 
Anyone have any ideas to get sound back on my primary user? I really don't want to be logged in as root for this simple task.
 
Also, this computer has had multiple versions of Ubuntu and Kubuntu installed in the past with no problems with the sound(including 11.04). However, they were desktop versions.
 
Thanks,
Ben

---

### Post by twin_rotor on 2011-07-23
Edit: mangler works while logged into Gnome as root only.  The primary user has no sound at all.

---

### Post by twin_rotor on 2011-07-24
Ttt

---

### Post by twin_rotor on 2011-07-26
Bump

---

### Post by twin_rotor on 2011-07-27
Bump

---

### Post by twin_rotor on 2011-07-28
bump

---

### Post by twin_rotor on 2011-07-29
Bump. Can anyone point me in a direction?

---

### Post by twin_rotor on 2011-07-30
Anyone?

---

### Post by twin_rotor on 2011-07-31
Fixed it with:
 
```
 
sudo adduser <username> audio

```

---

