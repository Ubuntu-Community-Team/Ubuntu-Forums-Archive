---
title: "J type Picture Not Supported"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by Terry S on 2008-03-20
Hi 

I cannot play wmv files in either Totem Movie Player, Mplayer, VLC Media Player or Gxine. I have used Automatix to download all available plugins, I think!. I have also tried Gstreamer and Xine in Movie Player.

I am running Ubuntu 7.10 AMD64 on an AMD4000 64 chip with 3 meg memory with a Nvidia 7800GT Graphic card with the Ubuntu 'supplied'  Nvidia drivers.

The error message I get on Mplayer is J Type picture not supported. The other player just distort the image.

Can anyone help?

Terry S:confused:

---

### Post by erginemr on 2008-03-21
Did you download the win32 codecs from Automatix (if available) as well? What is the outcome of:
```
dpkg -l w32codecs
```
from the terminal.

Otherwise, you can add Medibuntu repo to your software sources and download that package to see if it makes any difference:
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

