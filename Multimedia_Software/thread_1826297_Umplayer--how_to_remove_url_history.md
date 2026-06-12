---
title: "Umplayer--how to remove url history"
date: 2011-08-16
forum: Multimedia Software
---

### Post by beew on 2011-08-16
I know how to do it by editing umplayer.ini  but I am setting it up for someone who is not inclined to edit configuration files. There should be an option in the GUI for erasing url history, but I can't find it.

Thanks.

---

### Post by beew on 2011-08-17
Bump!

---

### Post by andrew.46 on 2011-08-19
> **beew said:**
> I know how to do it by editing umplayer.ini  but I am setting it up for someone who is not inclined to edit configuration files. There should be an option in the GUI for erasing url history, but I can't find it.

I believe that this option does not exist from within the gui which is a pity. Can you set your friend up with a simple one-line to accomplish this? The following works well on my system and does not seem to delete more than it should:

```

sed -i '/^urls=/d' ~/.config/umplayer/umplayer.ini 

```

Perhaps set it up as a desktop launcher of some sort for him...

---

