---
title: "Wireless on standard Ibex, not E17"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by berZirker on 2009-02-14
I've got Ibex running on a second hd on my tower, but I have to connect with wireless.  I have an old Linksys 2.4ghz PCI wireless card, which gives me a fine connection on Windows and my regular ibex install.  I followed Rui Pais's post to play with Enlightenment ([http://ubuntuforums.org/showthread.php?t=916690&highlight=enlightenment+wireless](http://ubuntuforums.org/showthread.php?t=916690&highlight=enlightenment+wireless)) and got the wireless working for a little while.  Once or twice it even worked to reset the wireless with 
```
sudo /etc/init.d/networking restart
```
but that no longer works

I'm not very familiar with the enlightenment organization system, but I have looked around and can't find a way to work on the problem (especially since I can't be on the internet while I'm doing it except on my iphone.)

Can someone give me some clues where to look, or what to post to get more information?  Thanks in advance

---

### Post by berZirker on 2009-02-14
I'm  posting this from the E17 side, so I have internet working now.  I installed fluxbox to try something different, and wireless worked off the bat so I decided to switch back to Enlightenment just to check - and like magic it did.  I'm not posting this as solved because nothing has been solved and I'm not convinced it won't stop working in the near future.

So does anyone know why the connection/whatever might be so flaky?  I would appreciate some understanding.

---

### Post by smartboyathome on 2009-02-19
I would suggest installing WICD and seeing if that works. Network Manager (which is what Ubuntu uses by default) doesn't play very well with E17 since it needs a system tray and E17 has none.

---

