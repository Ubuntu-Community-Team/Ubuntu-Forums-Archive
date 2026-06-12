---
title: "Nvdia Driver Problems"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by monsieurdozier on 2007-08-22
I tried to install my Nvdia GeForce 2 MX card in my PC.  I followed the guidelines here: [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html) .  Using Method One and the second list as described in Method 1.   I start up and it loads Ubuntu then I just see a blue screen flashing against a red screen with vertical lines.

Any help please?

Monsieur Dozier

---

### Post by tseliot on 2007-08-22
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
sudo dpkg-reconfigure xserver-xorg
```

select the "nv" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vesa" instead of "nv" and try again.

---

### Post by monsieurdozier on 2007-08-22
The Vesa setting worked.  Thank you much.


 Monsieur Dozier

---

