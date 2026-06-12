---
title: "Lubuntu - Windows when maximised not going full screen"
date: 2015-07-04
forum: Multimedia Software
---

### Post by StevenHarper on 2015-07-04
Maximised windows were not going full screen.
They were leaving a gap on both he let and right of the screen.

Finally I found some duff panels that had been created

Some unneeded files were in the directory

```
/home/steven/.config/lxpanel/Lubuntu/panels
```

named

[LIST]
[*]top
[*]left
[*]left1
[/LIST]

Simply delete these files, log off and log back in.

---

### Post by ajgreeny on 2015-07-04
That will bring you back to the default single panel of Lubuntu, I think, without any of the configuration which you have added.  You can remove those files one by one to trash and logout to see which panel has disappeared.  If the wrong one, simply restore that from trash and try another.

---

