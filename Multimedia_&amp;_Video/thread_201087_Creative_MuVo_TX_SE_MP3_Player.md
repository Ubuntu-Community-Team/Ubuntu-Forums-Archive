---
title: "Creative MuVo TX SE MP3 Player"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by Milambar on 2006-06-21
Just a few pointers, to anyone who is thinking of getting one of these devices.

They work perfectly under Ubuntu, and plugging them in automounts them as if they were a normal flash drive. You can just copy your music over to them without problems (although see note below).

However a friend of mine who worked for Creatives technical support gave me the following extra pointers, that Creative doesn't tell you...

[LIST]
[*]They are preformatted in FAT16, reformat them in FAT32 for better performance.
[*]Do NOT upgrade the firmware. The upgraded firmware reduces the volume output quite a lot, to comply with French laws.
[/LIST]

Note: After copying your files to the MuVo, type in a console: sync. If you don't, its my experience that the last file you copied over, goes missing. It shows in a ls -alh /media/usbdrive, but it doesn't seem to be seen by the players firmware until you synch it.

Hope this helps people (and sorry if it's in the wrong forum).

---

### Post by Vlatko on 2006-06-21
i have one of those and it came formatted as fat32. thanks for the tips though.

---

