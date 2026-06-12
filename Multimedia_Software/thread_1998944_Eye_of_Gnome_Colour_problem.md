---
title: "Eye of Gnome Colour problem"
date: 2012-06-07
forum: Multimedia Software
---

### Post by muralysunam on 2012-06-07
[SIZE=4]I upgraded my ubuntu from 10.10 to 12.04 step by step online
But now my Eye of Gnome is not working correctly. It displays all pictures with a reddish layer.[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=4]The Real photo is[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=4]
Thanks For any help[/SIZE]!!!!!!

---

### Post by papibe on 2012-06-07
Hi muralysunam.

I haven't seen that problem before, so I only have a couple of guesses.

First, I would try to reconfigure eog:
```
sudo dpkg-reconfigure eog
```

If that don't work, I would suspect a problem with your graphic card. Could you post the result of this command?
```
 lspci -nnk | grep -iA2 vga
```
Regards.

---

