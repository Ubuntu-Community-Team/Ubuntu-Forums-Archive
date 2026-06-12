---
title: "Upgraded to 8.04 from 7.10 and Atheros wifi card stopped working!"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by Matt Gotts on 2009-03-17
Evening, I'm hoping you nice people can help a complete newbie here and let me get back to what I should be doing, rather than fiddling with my PC!

I installed Gutsy 7.10 from a CD a few days ago, and after some twiddling and going down the wrong paths, got my Wifi Card (which XP identifies as an Atheros 5005GS) to work and could browse the internet.

I then forgot my wife's sage advice to leave something that's working alone, and upgraded to 8.04.  After installing it the wifi was still OK, but on re-boot - nada.  Network manager doesn't even see a wireless connection.

PC is running an AMD athlon processor and I'm dual booting with XP (hence I've got internet!).  If I do the thing in terminal to show my network connections it sees both the built-in network port and the Atheros card, but the second has something like [unassigned] or such like against the name.

I've looked at various options - manually downloaded the madwifi driver in Windows, copied it to Ubuntu and tried to install - get errors saying that files are not found (this off the Howto for installing the drivers).  I've also tried to install NDISwrapper but it requires an internet connection to install!!!!  My main issue is that I'd have to move the router again to hardwire the network, which I'd prefer not to have to do, but if that's what it comes down to so be it.

Going round in circles here!  If anyone can shed some light on this it would be VERY much appreciated - I've got to get a dissertation done and this is distracting me big time;)

Thanks in advance

Matt

---

### Post by .:Justus:. on 2009-03-17
> **Matt Gotts said:**
> Evening, I'm hoping you nice people can help a complete newbie here and let me get back to what I should be doing, rather than fiddling with my PC!

I installed Gutsy 7.10 from a CD a few days ago, and after some twiddling and going down the wrong paths, got my Wifi Card (which XP identifies as an Atheros 5005GS) to work and could browse the internet.

I then forgot my wife's sage advice to leave something that's working alone, and upgraded to 8.04.  After installing it the wifi was still OK, but on re-boot - nada.  Network manager doesn't even see a wireless connection.

PC is running an AMD athlon processor and I'm dual booting with XP (hence I've got internet!).  If I do the thing in terminal to show my network connections it sees both the built-in network port and the Atheros card, but the second has something like [unassigned] or such like against the name.

I've looked at various options - manually downloaded the madwifi driver in Windows, copied it to Ubuntu and tried to install - get errors saying that files are not found (this off the Howto for installing the drivers).  I've also tried to install NDISwrapper but it requires an internet connection to install!!!!  My main issue is that I'd have to move the router again to hardwire the network, which I'd prefer not to have to do, but if that's what it comes down to so be it.

Going round in circles here!  If anyone can shed some light on this it would be VERY much appreciated - I've got to get a dissertation done and this is distracting me big time;)

Thanks in advance

Matt

I had the same problem, go to you grub menu.lst and put an # infront of the new kernel headers (title, root etc) . Then revert back to your older kernel. Kernel updates often cause this to happen, so you can use 8.04 fine but you´ll have to stick to your old kernel.
If you need a more in depth help on how to revert back to your old kernel than say so. I´m just lazy right now and am hoping that you know how to do it xD

---

### Post by .:Justus:. on 2009-03-17
Never mind missed the part where you said you were new to this.

Open up your terminal:
type in the following:
```
sudo cp /boot/grub/menu.lst /boot/grub.menu.lst.bkp
gksudo gedit /boot/grub/menu.lst
```

After you type the second command a window should appear.
Scroll to the very bottom and you´ll find some lines that look something like this:
title		Ubuntu 8.04, kernel 2.6.somethingsomething-generic
uuid		blabla
kernel		/boot/vmlinuz-2.6blabla ro quiet splash 
initrd		/boot/initrd.img-2.6.27-13-generic

Thats the new kernel you´re using.
Under it you should find the old one you were using before

#title		Ubuntu 7.10, kernel 2.6.27-scooby doo-generic
#uuid		shubidubap
#kernel		/boot/vmlinuz-2.6.27-andagh
#initrd		/boot/initrd.img-2.6.27-13-generic

Now put the # infront of the newer kernel lines like in the second example.
and take the # away from your older kernel lines.

save and close.
That way upon bootup it will run back the way it used to and ervything will be like before.

---

### Post by Matt Gotts on 2009-03-18
Thanks Justus - I checked and there were two 'live' option in the bootup menu list - selected the older one and everything works!

Many thanks again:KS.  This community is fantastic!!:P:P

---

### Post by .:Justus:. on 2009-03-18
> **Matt Gotts said:**
> Thanks Justus - I checked and there were two 'live' option in the bootup menu list - selected the older one and everything works!

Many thanks again:KS.  This community is fantastic!!:P:P

No problem glad you fixed it^^

---

### Post by Matt Gotts on 2009-03-19
OK, maybe tempting fate here, but would I gain anything by upgrading to 8.10?  Or should I stop while I've got a working system!;)

---

### Post by .:Justus:. on 2009-03-19
> **Matt Gotts said:**
> OK, maybe tempting fate here, but would I gain anything by upgrading to 8.10?  Or should I stop while I've got a working system!;)
Well, the atheros cards dont work with the new kernels, however if you download 8.10 with the kernel -7  [http://packages.ubuntu.com/intrepid-updates/i386/linux-image-2.6.27-7-generic/download](http://packages.ubuntu.com/intrepid-updates/i386/linux-image-2.6.27-7-generic/download) then it will work. 
So, first of all, download the -7 kernel, save it somewhere where youll find it again.
Then update to 8.10 and edit the grub menu.lst once again so that you are booting into the -7 kernel.
Good luck!

---

