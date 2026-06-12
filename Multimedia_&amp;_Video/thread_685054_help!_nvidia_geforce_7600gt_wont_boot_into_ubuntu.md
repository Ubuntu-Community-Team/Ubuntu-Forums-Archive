---
title: "help! nvidia geforce 7600gt wont boot into ubuntu"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by mikey09 on 2008-02-01
ok so i am a ubuntu noob and i partitioned my hardrive and installed ubuntu 7.10 everything is grand but... I discovered a while ago that my Nvidia geforce 7600gt will not allow my BIOS to boot from cd so i have to remove the graphics card and install ubuntu then. after installation i place back in the graphics card and while ubuntu is loading it stops and says cannot find mirocode or something like that everytime.
if i boot back into ubuntu with VGA onboard graphics it leaves me with rubbish graphics and i want to get my card working on ubuntu. I tried updating nvidia drivers and installing them
and used envy but to no avail. i really need help.

---

### Post by taurus on 2008-02-01
Can you boot into recovery mode from GRUB menu with your nvidia graphic card in there?  If you can, see if it helps if you reconfigure your X server again with

```
dpkg-reconfigure xserver-xorg
```
And once you are done with that, you can reboot to normal mode with

```
shutdown -r now
```

---

### Post by mikey09 on 2008-02-01
thanx man your a life saver cant believe that worked thank you so much

---

