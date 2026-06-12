---
title: "samsung 940bw + nvidia problem"
date: 2008-09-12
forum: Multimedia Software
---

### Post by xmagixx on 2008-09-12
Hello
i have these 2
well i wanted to have a highere refreash rate 
when i use 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
md5sum /etc/X11/xorg.conf |sudo tee /var/lib/x11/xorg.conf.md5sum
sudo dpkg-reconfigure xserver-xorg
```

i can then see when i change resulution it has found my samsung
and i can then set the refreash rate
how ever it have disabled my nvidia restricted driver
when i enable it and restart the monitor goes back to been unknow monitor
how can i make it remember my monitor AND have the nvidia driver going ?

---

