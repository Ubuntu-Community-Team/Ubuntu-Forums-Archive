---
title: "Anyone any good with Audacious, got a weird issue..."
date: 2009-05-15
forum: Multimedia Software
---

### Post by listerdl on 2009-05-15
Hi, I use audacious a lot, and for some unknown reason, every time I launch it, it gives itself a new skin. I can live with that, (sort of) but the skins it gives itself are really garish, like bright red or really bright orange :shock:

Anyone have any ideas to just select one skin and it remains permanent?

Thanks!!!!!!!!!!

---

### Post by tragicglee on 2009-05-21
Open ~/.config/audacious/config in your editor of choice. You're searching  for the line that reads random_skin_on_play=TRUE -- you want to change the TRUE to FALSE. Save the file, restart audacious, and the problem should be solved.

---

### Post by listerdl on 2009-05-28
sorry for being a dumb-*** but where will the ~/.config/audacious/config be?

Thanks!!

---

### Post by andrew.46 on 2009-05-29
Hi listerdl,

> **listerdl said:**
> sorry for being a dumb-*** but where will the ~/.config/audacious/config be?

The symbol '~' is shorthand for your home directory, while .config is a 'hidden' folder within your home directory. These folders can be seen by pressing the ctrl + h keys. You can then navigate to the config file and alter it by hand. ctrl + h is a toggle so press it again and the files are hidden.

You can see your current setting using grep:

```

andrew@skamandros~$ **[COLOR="Purple"]grep 'random_skin_on_play' ~/.config/audacious/config[/COLOR]**
random_skin_on_play=FALSE

```

All the best,

Andrew

---

### Post by listerdl on 2009-05-29
How weird - thanks guys - but i tried what you all said and i found the file but alas the setting was already set to FALSE...

How weird....must be some freak command somewhere...

Odd - thanks nonetheless

---

