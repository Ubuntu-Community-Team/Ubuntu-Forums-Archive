---
title: "ipod touch doesn't work outside of gnome"
date: 2010-10-15
forum: Multimedia Software
---

### Post by someitalian123 on 2010-10-15
I recently upgraded to kubuntu 10.10 and now I can't play songs and sync my ipod outside of gnome. Before the upgrade I was able to access the ipod using rhythm box, it wouldn't be detected at first but if I would click music and then import folder and then click ipod touch under places rhythm box would recognise it and it would be mounted at /home/linux/.gvfs/iPod touch. But now unlike before on kubuntu 10.04, when I plug in my ipod it is actually recognised by the device notifier, but it only recognises it as a camera it has no access to the rest of the file system where the music is located, and their is no eject button in the device notifier to unmount. And because of this I can't mount gvfs unless I unplug the ipod, logout, and log back in into gnome. I tried mounting with ifuse before on 10.04 but it didn't work right, now when i try it in kde I get a whole new error message. 

linux@linux:~$ ifuse /mnt/ipod/
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.

I tried

umount camera:/Apple iPod Touch (PTP mode)@usb:001,005/

But that just gave me 

bash: syntax error near unexpected token `('

I didn't think that command would work but I tried it because I have no idea where the hell the ipod is mounted or if it's even mounted at all. Is their any way to keep kde from detecting my ipod touch? Or anything I can do in the terminal so I can use my ipod with gtkpod or rhythmbox while in kde.

---

### Post by lvarga37 on 2011-01-01
I have the same problem as you. Did you find a solution, or just went back to gnome?
Regards,
lvarga37

---

### Post by ChuckyDuckster on 2011-01-01
> **someitalian123 said:**
> 
I tried

umount camera:/Apple iPod Touch (PTP mode)@usb:001,005/

But that just gave me 

bash: syntax error near unexpected token `('


I would try to do that in quotes. I think because there are spaces in the name, it is taking the different parts as different arguements, and it doesn't recognize the '(' as a flag.

```
umount "camera:/Apple iPod Touch (PTP mode)@usb:001,005/"
```

Having the same problem in Kubuntu 10.10, and it works when I choose to load Gnome at login. Out of curiosity, are you running 64-bit?

---

### Post by lvarga37 on 2011-01-02
Yes, I run it on amd64.
Well , I am reinstalling 10.04 and try with that, but then it seems it is rather gnome and not the version is the solution...

lvarga

---

### Post by S29K on 2011-05-03
Anyone find a solution to this problem yet?

I assume that it involves starting a gnome library on KDE startup but I don't know which one or how to do it.

---

