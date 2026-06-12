---
title: "Sound broken with Feisty upgrade"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by jsully1 on 2007-04-20
Hi All,

I have an IBM Thinkpad T60 that I'd had Edgy (and before that Dapper) running great on.  I upgraded to Feisty yesterday and things went downhill from there.  The initial login sound plays, but after that any app that plays a sound immediately hangs.  Killing X doesn't restore order either, it requires a full reboot to get things working again.  If I just kill X and log back in it hangs right after the login prompt.

Things that crash:
Thunderbird after playing mail received sound
XMMS
VLC
Sound Preferences
  When I test any of the devices (I've tried OSS and ALSA) or play any of the event sounds it hangs and takes Gnome's menus with it.

What more information would be useful, and where should I start looking?  Thanks in advance for the help - other than this and the fact that Ubuntu Beryl doesn't support Xgl (you need to downgrade beryl-core) the upgrade went very smooth!

---

### Post by jsully1 on 2007-04-20
Fixed!

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

For some reason this also nuked GDM, so you need to do a 
sudo apt-get install gdm
as well.

---

### Post by GeneW on 2007-04-22
I'm having the same problem with my Thinkpad T42 but that uninstall -> install sequence didn't help me.

---

### Post by dustman on 2007-04-23
Well, the uninstall-install did not work for me either....When trying to start playback I get this message from XMMS:
```
failed to open audio output: ALSA 1.2.10 output plugin
```
but in dapper and edgy the sound worked fine :(

---

### Post by GeneW on 2007-04-23
I've managed to get sound to work with a reboot some of the time but then it goes away again and you need to reboot to get it working again.

---

### Post by jsully1 on 2007-04-23
Try going through this process:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

