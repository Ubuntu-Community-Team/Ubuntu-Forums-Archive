---
title: "Update failed, cannot get access to the grub"
date: 2012-06-03
forum: Mythbuntu
---

### Post by num1bryanp on 2012-06-03
Hello All,
I just built and installed mythbuntu 12.04 on a new system. It was working great till I enabled the system updates for mythtv 0.25 and mythbuntu in the Mythbuntu-Control-Center. I then started the updates which ran for about 3 minutes without errors, then about half way it just locked up and after about 1 hour I did a shut down and restated.

Now the system comes up flashing with error 130 front-end error. It looks like the screen is flashing between the desktop and mythtv failing startup screen.

I cannot seem to get access to the grub at boot to use a previous kernel, (I have tried shift, e, and Esc at boot, no grub)

Any help would be great.
Thanks,
Bryan

---

### Post by raja.genupula on 2012-06-03
i think problem is with your graphics drivers . re install the graphics drivers .

---

### Post by num1bryanp on 2012-06-03
> **raja.genupula said:**
> i think problem is with your graphics drivers . re install the graphics drivers .
Hello raja.genupula,
That sounds like a good idea, now do you have any tricks to let me do it?
Currently all I have is a system with a flashing screen. :-(
Thanks,
Bryan

---

### Post by Kr0nZ on 2012-06-03
you could try booting to a live cd or usb,
then mount your hard drive and modify grub to always show the menu
[http://www.howtogeek.com/howto/ubuntu/show-the-grub-menu-by-default-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/show-the-grub-menu-by-default-on-ubuntu/")

---

