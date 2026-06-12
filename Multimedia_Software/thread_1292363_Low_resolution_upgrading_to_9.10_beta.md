---
title: "Low resolution upgrading to 9.10 beta"
date: 2009-10-15
forum: Multimedia Software
---

### Post by jrcobain on 2009-10-15
All,

I have just upgrade my Ubuntu from 9.04 to 9.10 beta, but I'm having problems with low resolution. It only shows 800x600 and 640x480. I could fix it manually with the following command:

$ xrandr --newmode "1152x864" 83.54 1152 1184 1496 1528 864 881 890 908
$ xrandr --addmode VGA1 1152x864
$ xrandr --output VGA1 --mode 1152x864

But, when I restart the system, I get low resolution again. :sad:
Any idea on how to set up it automatically?

Thanks!

Edson Junior

---

