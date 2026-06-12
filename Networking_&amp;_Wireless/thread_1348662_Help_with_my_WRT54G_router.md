---
title: "Help with my WRT54G router?"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by JoeyF on 2009-12-07
I lost the pass to it and i want to set up my ps3.

For more info:
[http://ubuntuforums.org/showthread.php?t=1348599](http://ubuntuforums.org/showthread.php?t=1348599)

Thanks,

---

### Post by chili555 on 2009-12-07
Press the reset button and hold it for 15 seconds. Plug the ethernet cable into the router and to your computer. Open a terminal and do:```
sudo ifconfig eth0 192.168.1.2 up
firefox http://192.168.1.1
```Are you golden?

---

