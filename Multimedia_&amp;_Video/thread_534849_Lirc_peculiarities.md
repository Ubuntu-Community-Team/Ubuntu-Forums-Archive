---
title: "Lirc peculiarities"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by 505 on 2007-08-25
I have some trouble with Lirc. I can get it to work, however...
Lircd only works after I run the following script:
```

#!/bin/sh
sudo killall lircd
sudo modprobe -r lirc_serial
sudo /etc/init.d/lirc restart

```
This makes lircd work, but not lircmd (the mouse driver). This one only works after a restart of X (using ctrl+alt+backspace). Also, without running the script, but with restarting X, lircd works.

Does anyone know how to fix this?

---

