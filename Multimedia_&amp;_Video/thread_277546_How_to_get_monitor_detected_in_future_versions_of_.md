---
title: "How to get monitor detected in future versions of Ubuntu"
date: 2006-10-14
forum: Multimedia &amp; Video
---

### Post by wsfulton on 2006-10-14
I've spent quite some considerable effort and put off using Ubuntu for many months because by default I got such a terrible resolution on my 21" monitor. I've got xorg.conf nicely set up now. However, when I install future versions of Ubuntu, I'd like it to detect my monitor correctly so that myself and others don't have to re-edit this file each time. Suse and Windows seems to detect it okay. Is a bug report the best way to go about this? I'll supply any necessary information. 

Thanks.

PS Monitor is ViewSonic P815.

---

### Post by taurus on 2006-10-14
Save your /etc/X11/xorg.conf somewhere handy in case you need to use it or just reconfigure it if the default doesn't work...

```
sudo dpkg-reconfigure xserver-xorg
```

---

