---
title: "Help with Nvidia please!"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by naruto650 on 2008-01-18
Well heres the situation. I installed envy so i could install the nvidia drivers and it did that. I restarted it and when i chose the nvidia settings, when it opened it said this 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 


So how do i fix this problem, im still a newbie at this. By the way im using ubuntu 7.04 and the video card i want to use is Geforce Fx 5500

---

### Post by RomeReactor on 2008-01-19
Hi. To run the command, open a terminal (Applications->Accessories->Terminal) and write or paste:
```
sudo nvidia-xconfig
```
Using **sudo** before the command allows you to issue it with administrator privilege (root). It will ask you for your password, but you won't see any characters when writing it; this is a security feature and it's normal. To restart your display (the X server) press CTRL+ALT+BACKSPACE.

---

