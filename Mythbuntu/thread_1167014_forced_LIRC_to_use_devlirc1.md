---
title: "forced LIRC to use /dev/lirc1"
date: 2009-05-22
forum: Mythbuntu
---

### Post by wombo on 2009-05-22
How do I forced LIRCD to user /dev/lirc1 instead of /dev/lirc0

Currently I have to stop lircd then run this

sudo lircd -d /dev/lirc1

---

### Post by AlecJ on 2009-05-22
You need to edit your hardware file
```
sudo nano /etc/lirc/hardware.conf
```

Then you can select what ever you want.

---

