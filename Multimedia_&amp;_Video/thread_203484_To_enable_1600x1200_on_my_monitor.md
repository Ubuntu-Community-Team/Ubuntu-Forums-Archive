---
title: "To enable 1600x1200 on my monitor"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by bocmaxima on 2006-06-25
Would I just edit the resolution into my xorg.config? I have the latest nVidia drivers and my monitor supports the resolution. I just dont want to cause a catastrophe if I dont ask first. :)

---

### Post by taurus on 2006-06-25
If your monitor suports that resolution, then you can edit /etc/X11/xorg.conf by hand.  Otherwise, you can also reconfigure X again with
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by tseliot on 2006-06-25
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")
If that doesn't work try point 10

---

