---
title: "HOWTO: Save nvidia-settings in Ibex 8.10"
date: 2008-11-08
forum: Multimedia Software
---

### Post by earthpigg on 2008-11-08
There seems to be a common problem with being able to save changes in nvidia-settings on 8.10 fresh installs.

The problem I and others have is that when set up nvidia-settings how we want and then click 'save' nvidia-settings immediately closes without giving us the confirmation window, resulting in any changes being lost on computer restart.

Here's what worked for me:

1. Rename your current /etc/X11/xorg.conf to something else:

```
sudo mv /etc/X11/xorg.conf /etc/X11/backupofxorg.conf
```

2. That it! Now, start nvidia-settings as normal:

```
sudo nvidia-settings
```

and you should be able to save any changes made, and your 2nd monitor, etc, should be up and good to go when you restart.

Credit for this workaround goes to [mickjt84]("http://www.youtube.com/user/mickjt84") from (of all places) youtube... he told me he doesn't have an ubuntuforums.org account. If he ends up making one and posting in this thread, I'll edit this post and point him out so credit can be given where due.

he described the issue to me as such:

> On 8.10, nvidia-settings also has a Segmentation fault and closes when you try to save the X.Org config.

That is greek to me, so whatever... hope this helps :)

---

