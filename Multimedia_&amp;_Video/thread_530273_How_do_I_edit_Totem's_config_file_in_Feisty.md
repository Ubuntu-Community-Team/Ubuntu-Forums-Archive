---
title: "How do I edit Totem's config file in Feisty?"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by onemanwaking on 2007-08-20
Hi everyone!

I'm encountering a problem with playing screencasts made with RecordMyDesktop on Totem. I've found what I think to be the fix here: [http://ubuntuforums.org/archive/index.php/t-433090.html](http://ubuntuforums.org/archive/index.php/t-433090.html)

However, I've tried to find the config file for Totem so that I can add a line, but I don't think there is such a file in Feisty.

Can anyone point me in the right direction? Thanks!

---

### Post by tseliot on 2007-08-20
Can you post the output of this command?

```
ls $HOME/.gnome2/
```

NOTE: make sure you don't skip the "." (dot) before "gnome2"

---

### Post by onemanwaking on 2007-08-20
Hi, thanks for responding!

When I entered that command I get this:

accels   gedit-metadata.xml  nautilus-scripts  totem
gedit-2  keyrings            share             totem_config


So, I see the "totem_config" file there. How do I get it open with gedit?

---

### Post by tseliot on 2007-08-20
> **onemanwaking said:**
> So, I see the "totem_config" file there. How do I get it open with gedit?
type:
```
gedit $HOME/.gnome2/totem_config
```

or, if you want to open it from Nautilus (the file manager) you will have to select "View" from the menu and then "Show hidden files". In this way you'll see the .gnome2 folder

---

### Post by onemanwaking on 2007-08-20
Yay - it worked!

I didn't realize it was a hidden file...

Thanks for your help!

---

