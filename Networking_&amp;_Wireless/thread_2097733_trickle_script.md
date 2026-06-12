---
title: "trickle script"
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by amoateng on 2012-12-24
hey guys,

i wrote this script for trickle to start running 30seconds after the computer starts up(i'll add it to the startup programs). Can someone take a look and tell me if it looks all right? 

```
#!/bin/bash

sleep 30 && trickle -d 25 -u 15 firefox
```

---

