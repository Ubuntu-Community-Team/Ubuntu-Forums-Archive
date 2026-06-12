---
title: "problem with sopcast-player"
date: 2010-04-06
forum: Multimedia Software
---

### Post by yonik on 2010-04-06
Hello.
I  installed  sopcast-player (by ubuntu-tweak), but I can not run it.

 sopcast-player
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 1780, in <module>
    pySop = pySopCast()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 368, in __init__
    self.vlc = VLCWidget.VLCWidget(*p)
  File "/usr/share/sopcast-player/lib/VLCWidget.py", line 28, in __init__
    self.player=instance.mediacontrol_new_from_instance()
AttributeError: 'Instance' object has no attribute 'mediacontrol_new_from_instance'

---

### Post by suli8 on 2010-06-10
damn i have the same problem now!
still unsolved!

but good to know im not alone!

---

### Post by ilabor on 2010-09-15
[http://ubuntuforums.org/showpost.php?p=9847168&postcount=422](http://ubuntuforums.org/showpost.php?p=9847168&postcount=422)

---

### Post by princepratt on 2010-09-15
I saw that the problem in fact is with VLC. In that thread they speak about it in page 39! and it seems I have the 1.1 orc vlc. I do not know how. May be with the system update. Any way I asked them if I can downgrade VLC and solve the issue. We will see. But its a big relief.

---

