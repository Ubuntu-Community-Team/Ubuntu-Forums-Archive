---
title: "&quot;ATI&quot; or How I learned to stop worrying...?"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by Trurl on 2006-06-11
I have spent hours trying to fix the MESA problem and install the ATI drivers (Radeon 9600 Mobile Pro), and have not had any success. I've tried Methods 1/2 from the Wiki, and I've tried some of the methods from the forum. Nothing works. If anyone has any amazing insights that could help me, I'm open to suggestions! However...

...I'm dual booting with XP pro with the plan to run games and Matlab on the XP side...while Ubuntu will be used for everything else. That said, is there any reason to keep trying to install the ATI drivers? Everything else in Ubuntu runs fine, so is there any need for the graphics drivers?   

Thanks for any advice,

Trurl

---

### Post by Anduu on 2006-06-11
Well if you don't mind not playing games or using 3D screensavers in Dapper then I'm sure the generic ATI driver is fine.

Otherwise you can try this...it has worked for me everytime(Radeon9600)

Boot into recovery mode

```
apt-get remove xorg-driver-fglrx
apt-get remove linux-restricted-modules
```

Then

```
apt-get install linux-restricted-modules
apt-get install xorg-driver-fglrx
```

Finally

```
aticonfig --initial
```

Reboot

---

### Post by Trurl on 2006-06-11
Sorry, but how do I boot into recovery mode? I tried safe mode from the CD but I had no internet access and my terminal didn't open to the hard drive. As you can see, I'm a new user ;) 

Thanks,

Trurl

---

### Post by campnic on 2006-06-11
Don't use the cd, but when you reboot it will say hit esc to enter the grub menu, then select the second option, which will say (Recovery mode) at the end, this will boot you into run level 3 (console mode) using safe drivers.

cheers

---

