---
title: "1280x1024 Resolution Not Available"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by Rineva on 2006-06-17
I am dual-booting with Dapper Drake on my PowerMac G3 B&W 400 server with a nineteen inch, 1280x1024 X2gen LCD monitor. No idea what the vidicard is. I can set the resolution to 1280x1024 in Mac OS X Server, but in Ubuntu there are no options over 1024x768 and with my monitor it's not a pretty sight.

Is there an error surrounding this? Or is there a patch of some sort? Any input would be highly appreciated.

---

### Post by tkiesel on 2006-06-17
Try the following on a terminal, and select more resolution options when prompted.

```
dpkg-reconfigure xserver-xorg
```

---

### Post by spitfireinc on 2006-06-18
seems that people forget to do this dueing install.

During ur install u get a list of resolution and i guess people highlight the res they want and hit return. But ur suppose to hit space and select all the res u want, then u hit return

---

