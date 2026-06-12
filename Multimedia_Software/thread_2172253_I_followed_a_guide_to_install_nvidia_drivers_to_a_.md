---
title: "I followed a guide to install nvidia drivers to a system running 12.10. I run 12.04."
date: 2013-09-03
forum: Multimedia Software
---

### Post by kaedenderksen on 2013-09-03
As you can assume things aren't running smoothly anymore. Chrome and Firefox are functional but freeze up very easily, steam won't open any graphical interface and thunderbird freezes upon updating emails. 

Here is the guide i followed: [http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)

I've got a nvidia geforce 9800 gt. Dual booting windows 7 and ubuntu 12.04.
 I've restarted my computer and am posting this from windows 7. I have no sort of back up of my ubuntu install.

I'd post the screenshot of terminal right before executing **sudo /etc/init.d/lightdm restart **but unfortunately i can't upload it to imgur without my browser freezing. I got an error from one of the previous commands but i don't remember what it was. Clearly it didn't defer me from blindly pressing on. 


So should i cut my losses and reinstall ubuntu? 

And yes I'm an idiot. 

Thanks.

---

### Post by carl4926 on 2013-09-03
No guides are required
The nvidia driver is installed with

```
sudo apt-get install nvidia-current
```

---

### Post by Bucky Ball on 2013-09-04
*Thread moved to **Multimedia & Video**.*

Welcome to the forums.

You can also try an update then check Additional Drivers (jockey from your link). The drivers in the kernel already should probably work fine unless you are looking to do something exotic. ;)

It is common for people arriving from Windows to assume they are going to need to install drivers for everything. Lots of hardware 'just works' in Ubuntu. Good luck.

PS: Reinstall is generally considered a last resort.

PPS: @carl: 'sudo apt-get install nvidia-current' is clearly instructed on the link in the OP. Sounds like part of what screwed things. ;)

---

### Post by kaedenderksen on 2013-09-04
Thanks for the help. I was trying to install drivers for the sake of steam games. 

I should have been more clear. Since my mistake ubuntu will no longer work properly, additional drivers will not open. I've tried installing the nvidia driver with that command and though it was successful in installation I'm still not able to get the steam user interface to appear as well as additional drivers. Also firefox and chrome were not freezing up before, but now they are.

---

### Post by Bucky Ball on 2013-09-04
In that case, you could cut your loses and reinstall, IF you have only just installed. Next time, only follow guides specifically for your release is best, although looking through that guide I can't see much that would cause this during the install of the driver as the kernel version and release are not specifically named. ;)

Incidentally, the Steam user interface problem may have nothing to do with your drivers. If everything was working fine before, *apart* from Steam, then probably doesn't.

---

### Post by kaedenderksen on 2013-09-04
hmm it's an old install. And yeah lesson learned. I may just reinstall cause it was a dramatic change. 

I forgot to mention that when i executed [COLOR=#000000] [/COLOR]**sudo /etc/init.d/lightdm restart** i got a black screen and had to manually restart.

---

