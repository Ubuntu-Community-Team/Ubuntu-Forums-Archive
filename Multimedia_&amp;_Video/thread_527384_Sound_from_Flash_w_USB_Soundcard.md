---
title: "Sound from Flash w/ USB Soundcard"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by spivak.d on 2007-08-16
Hey all,

I recently installed a USB sound card under Feisty and after some easy configuration, I get sound from VLC, Rhythmbox, etc... through USB. It seems, however, that Flash (under Firefox) believes that my old soundcard is still the way to go and, as a result, I hear no sound through my USB when I visit sites like YouTube. 

Anyone know how I might be able to go about changing the sound device that Flash sends audio to?

Thanks,
   Dima

---

### Post by spivak.d on 2007-08-16
:( No one?

---

### Post by snowdude on 2007-08-28
Yeah i have had this problem too. Anyone know of a way to fix this?

---

### Post by PatrickMB on 2007-08-31
I too am experiencing this. Any suggestions or threads to read?

---

### Post by Phurious on 2007-08-31
I had the same problem.  If you can hear sound in *SOME* applications already, this might be your fix:

```
sudo gedit /etc/modprobe.d/alsa-base
```

Set the index to "0" for which ever sound card you wish to use and save.  If that does not help I suggest reading through this post > [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound")

---

