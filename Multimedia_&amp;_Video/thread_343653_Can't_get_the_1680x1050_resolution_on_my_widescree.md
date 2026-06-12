---
title: "Can't get the 1680x1050 resolution on my widescreen LCD"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by jourman17 on 2007-01-21
I just bought a 22-inch widescreen flat panel from Dell and connected it to my pc. I have  Windows XP and Ubuntu 6.10 installed on it but I do all of my stuf with Ubuntu so I'm always working with it. My Graphics card is an Asus with Geforce 7600. In windows I had no problem with having this 1680x1050 resolution on my screen but I just can't get it with Edgy.

I tried to reconfigure X but wen I restareded X after going through the settings it did't came up and gave me an error.

Any help will be appreciated.

---

### Post by taurus on 2007-01-21
Maybe you need to reconfigure your X again.

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When done, restart X with <Ctrl><Alt>Backspace.

---

### Post by jourman17 on 2007-01-21
Thanks Taurus but when I do that  I want to  restart X it doesn't work so I will have to restore xorg.conf to bring it back

---

### Post by jourman17 on 2007-01-22
Well Actually Thank you very much Taurus. I tried it and this time it worked.
I think I was using some wrong settings.

But thanks anyway

---

