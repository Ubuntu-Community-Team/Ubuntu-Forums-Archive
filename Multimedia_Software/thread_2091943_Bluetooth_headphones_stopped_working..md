---
title: "Bluetooth headphones stopped working."
date: 2012-12-06
forum: Multimedia Software
---

### Post by JamesBwoii on 2012-12-06
Hi, my bluetooth headphones have stopped working, even though they do still connect fine. On the sound settings menu, on the left hand side, there used to be an option for my headphones, but I accidentally deleted it and can't figure out how to get it back. Here is a picture of the two remaining options, and the third bluetooth one used to be underneath those. [IMG]http://i1.minus.com/ibgoCJEQxmJ6YK.png[/IMG]
Thanks.

---

### Post by JamesBwoii on 2012-12-08
Can anyone please help?

---

### Post by freeaks on 2013-01-07
bluetooth headset used to work for me before.
it stopped, after upgrading to 13.04 raring ringtail (dev branch)  i think.
now i've just found a solution here:   [https://bbs.archlinux.org/viewtopic.php?id=133460](https://bbs.archlinux.org/viewtopic.php?id=133460)
> 
 in [General] section in /etc/bluetooth/audio.conf add:  
Enable=Socket

you need to restart bluetooth daemon:
> 
sudo stop bluetooth
sudo start bluetooth

hope this may help other too.

---

