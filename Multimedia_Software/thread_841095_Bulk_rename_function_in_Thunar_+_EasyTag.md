---
title: "Bulk rename function in Thunar + EasyTag"
date: 2008-06-26
forum: Multimedia Software
---

### Post by MedellinManDem on 2008-06-26
Does anyone know why once you've edited the tag of an mp3 in Thunar you cannot re-edit it in the same program or in Easytag? Basically I'm asking can you only rename an mp3's tag once?

---

### Post by tannedin on 2008-06-26
> **MedellinManDem said:**
> Does anyone know why once you've edited the tag of an mp3 in Thunar you cannot re-edit it in the same program or in Easytag? Basically I'm asking can you only rename an mp3's tag once?

is there some sort of weird permissions issue going on?
go to the directory where all those files are located and try ```
ls -al
``` and make sure you have write permissions and that you own the files... ```
man chmod
``` has a good description of what the different columns represent

---

