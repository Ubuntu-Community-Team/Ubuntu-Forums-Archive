---
title: "MythTV - Add second PVR-150 to existing setup?"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by tfmccull on 2006-12-01
Already have one PVR-150 installed and working. Want to install second. What is process to go about doing this? 6.10 Edgy Eft Server. Thanks.

---

### Post by superm1 on 2006-12-01
Drop it in, turn on machine

stop mythtv-backend
```
sudo /etc/init.d/mythtv-backend stop
```

start mythtv-setup
```
sudo mythtv-setup
```

configure to add second tuner in capture cards section, associate with an input etc

start mythtv-backend
```
sudo /etc/init.d/mythtv-backend start
```

---

