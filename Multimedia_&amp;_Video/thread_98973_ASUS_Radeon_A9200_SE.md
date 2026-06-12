---
title: "ASUS Radeon A9200 SE"
date: 2005-12-04
forum: Multimedia &amp; Video
---

### Post by modem on 2005-12-04
Hi,

I've just installed Ubuntu Breezy Badger 5.10 and I can't get it to work. The installation seemed to be ok, but when I start XServer, I get a "dirty" screen. I can't see anything clear but my cursor.
I'm posting this in this section, since I have had the same problem with Mandrake. I was told at the time, that the problem was probably due to my Video Card. I wasn't able to solve the problem, though.
Does anyone have a suggestion (and no, I don't want to just buy another Video Card ;) )

tanx

---

### Post by grimmson on 2005-12-04
I had some problems with ati's in 5.04. It's been a while but try this. To get a functional screen hit f7 at "dirty" screen and log into console. Type "sudo dpkg-reconfigure xserver-xorg" and manually select mesa drivers at lower res (I think vesa are older nvidia drivers). at reboot if you get a good screen try 
[http://www.linuxquestions.org/questions/t383625.html](http://www.linuxquestions.org/questions/t383625.html)
[http://wiki.serios.net/wiki/Debian_ATI_proprietary_display_driver_installation](http://wiki.serios.net/wiki/Debian_ATI_proprietary_display_driver_installation)
My personal advice is don't get ati. Historically nvidia has worked with linux while ati really hasn't. If you make it work, remember this the next time you build a system or a friend tries to give you an ati. Best of luck.:smile:

---

### Post by modem on 2005-12-05
thanks, I'll try this

---

