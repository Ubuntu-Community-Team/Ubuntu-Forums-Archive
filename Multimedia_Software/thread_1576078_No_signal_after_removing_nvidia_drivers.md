---
title: "No signal after removing nvidia drivers"
date: 2010-09-16
forum: Multimedia Software
---

### Post by lamadredelsapo on 2010-09-16
I executed the following and after a restart I have no signal in my monitor:

```


sudo service gdm stop
sudo apt-get remove --purge nvidia*


```

How can I fix this?

---

### Post by lamadredelsapo on 2010-09-16
I solved it booting with a live cd and following this thread:
[URL="http://ubuntuforums.org/showthread.php?t=1467074"]
http://ubuntuforums.org/showthread.php?t=1467074[/URL]

---

