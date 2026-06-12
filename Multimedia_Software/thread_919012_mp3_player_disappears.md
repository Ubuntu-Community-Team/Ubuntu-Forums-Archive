---
title: "mp3 player disappears"
date: 2008-09-13
forum: Multimedia Software
---

### Post by Razerblader on 2008-09-13
I have a  Sony Walkman mp3 player (MTP device),and I'm using rhythmbox music player, my problem is: When I connect my mp3 player to the computer it opens the folder which contains the media in it in /media/WALKMAN, but if I close the folder it disappears and i have to reboot and reconnect the device to see the folder again. would this have to do with the device being MTP or Windows prefered firmware?

---

### Post by AlesUbu123 on 2008-09-13
What if you try opening Nautilus file manager, press Ctrl + L keys and enter /media/. 
Can you now see your WALKMAN folder?

---

### Post by Razerblader on 2008-09-13
not at all. the only time I can see the folder is the first time I connect my device after booting.

---

### Post by AlesUbu123 on 2008-09-14
What does this terminal command tell you?

> cat /etc/mtab | grep /dev/

---

### Post by Razerblader on 2008-09-14
fixed it by downloading mtp-tools.

---

