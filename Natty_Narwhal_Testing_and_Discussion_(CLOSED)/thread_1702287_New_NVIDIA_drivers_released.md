---
title: "New NVIDIA drivers released"
date: 2011-03-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by garok89 on 2011-03-07
i just noticed that a new set of nvidia drivers were released today.... version 260.19.44
has anyone had a chance to try them with natty yet? i am away from my natty box at the moment but will try to test them later

[http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html](http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html)

---

### Post by Harry33 on 2011-03-08
> **garok89 said:**
> i just noticed that a new set of nvidia drivers were released today.... version 260.19.44
has anyone had a chance to try them with natty yet? i am away from my natty box at the moment but will try to test them later

[http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html](http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html)

That is the latest stable version relased on 7th March 2011.
We have a newer version (270.29), but beta of course, in Natty repos already.
And that one is needed for Natty's xserver 1.10 rc2.

No need to try older versions and break the xserver system with them.

---

### Post by Linearcraig on 2011-03-08
Ooh cool. Ill need to get that working on the revo.

---

### Post by Harry33 on 2011-03-08
> **Linearcraig said:**
> Ooh cool. Ill need to get that working on the revo.

The latest beta in Natty repos (nvidia-current_270.29-0ubuntu3) depends on
 - xserver 1.10 rc2 (>=1.9.99.902-2ubuntu1~)
 - virtual package xserver-viceo-abi-9

This means it cannot be installed with the xserver1.10 final (which is not yet in repos).
The latest nvidia beta (270.30) supports it, however. (not yet in Natty repos either)

---

