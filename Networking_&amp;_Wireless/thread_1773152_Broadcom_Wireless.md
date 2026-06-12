---
title: "Broadcom Wireless"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by Gnorrogh on 2011-06-01
Yeah, I know, yet another thread about the wireless-issue. But hey, something different here. 

I get the wireless working by executing ```
sudo modprobe b43
```

All good so far, but it's kinda tiring to execute that command every time I restart the computer, just to get internet access. So my question here is, is there any way to make this command execute by it's own, when starting up the computer, like in the background or something. Or even better, to actually make b43 the default driver for the wireless. I've tried reinstalling both bcmwl, and b43, uninstalling bcmwl etc. But no luck.

Help would be greatly appreciated.

---

### Post by chili555 on 2011-06-01
> there any way to make this command execute by it's own, when starting up the computer, like in the background or something. Certainly. Please do:```
sudo su
echo b43 >> /etc/modules
exit
```Enjoy!

---

### Post by Gnorrogh on 2011-06-01
I just execute those commands in the terminal, right?

EDIT: Thanks! Very much appreciated, worked like a charm. =)

---

