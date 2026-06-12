---
title: "VLC HTTP Interface: No sound when no user is logged in"
date: 2010-12-20
forum: Multimedia Software
---

### Post by NCC-1701-M on 2010-12-20
Hi,

I have a pc where I run ubuntu 10.10 and on this pc i have  installed vlc and on boot i start the vlc http interface. Therefor I  created the file /etc/init.d/vlc. The file seems like this:

[http://it-futtzy.blogspot.com/2009/07/automatic-vlc-start-at-system-boot-time.html](http://it-futtzy.blogspot.com/2009/07/automatic-vlc-start-at-system-boot-time.html)

and I also updated rc.d.

Vlc  starts on boot as desired I also can send commands like in_play the  file (a playlist) is loaded and reguarding the status.xml the file is  played. But when no user is logged in I hear no sound. When I perform a  login on the machine there is first still no sound but when I send e.g.  the pl_next command or call in_play again then there is sound. Sadly the  pc shouldn't be attached to a monitor and therefor I can't perform a  login everytime so I need sound, when noone is logged in.

Why is there no sound? I hope someone can help me to hear sound even noone is logged in.

Thanks in advanced

NCC-1701-M
=/\=

---

### Post by NCC-1701-M on 2010-12-21
Hi,

I deinstalled PulseAudio and as a precaution I added the user to the audio group and now it works fine.

---

