---
title: "install rum(4) in kernel"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by Mujaheiden on 2010-01-23
We have a corega cg-wlusb2go wireless key.

From the [manpage]("http://manpages.ubuntu.com/manpages/karmic/man4/if_rum.4freebsd.html") i understand that "rum(4)" supports it.

However, i need to compile it in the kernel and for that i need to put lines into the kernel config file.... Can somebody give me a hint as to where to start?

Im not at all newbie but compiling the kernel always sounds so serious to me...

---

### Post by chili555 on 2010-01-23
Where may we download and examine rum(4)? Isn't this supported by rt73usb? Can you please post:```
lsusb
```Thanks.

---

### Post by Mujaheiden on 2010-01-24
Hi,
its the first one:

```
Bus 004 Device 002: ID 18c5:0002
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by chili555 on 2010-01-24
This is supposed to work with the built-in module *rt73usb*.> chili@LAPTOP40:~$ modinfo rt73usb | grep 18C5
alias:          usb:v[COLOR="Blue"]18C5[/COLOR]p[COLOR="Blue"]0002[/COLOR]d*dc*dsc*dp*ic*isc*ip*
If you do:```
sudo modprobe rt73usb
iwconfig
```Do you have a wireless interface?

---

### Post by Mujaheiden on 2010-01-25
thanks! It almost worked with the installed 8.10 but it didnt get past wireless security. With the live CD 9.10 I managed though. Do I have to give the iwconfig at each boot?

We're relying on the wireless of our neighbours who gave their password, so its kind of cool if we can do the config without a cable connected. Ill reinstall to 9.10 and then I guess it'll be golden.

How did you see from the USB-id that its supported by RT-73? And do we then use the RUM or not at all?

---

### Post by chili555 on 2010-01-25
If it works and connects with rt73usb, then you don't need RUM. You shouldn't have to do iwconfig; Network Manager should take care of that for you. If the module rt73usb doesn't load automatically, we can amend */etc/modules*.

I connected the pci-id to rt73usb by Googling it. [http://cateee.net/lkddb/web-lkddb/RT73USB.html](http://cateee.net/lkddb/web-lkddb/RT73USB.html) especially see:> vendor: [COLOR="Blue"]18c5[/COLOR] ("AMIT"), product: [COLOR="Blue"]0002[/COLOR] ("[COLOR="Red"]CG-WLUSB2GO[/COLOR]")

Just because something is *supposed* to work doesn't mean it will work correctly. Try it and let us and the searchers know.

---

### Post by Mujaheiden on 2010-01-26
ah yes, that makes sense. 

It works in 9.10 w/o iwconfig, automatically. So problem fixed! No clue why it didnt work in 8.10, but well.

Now only a small [problem]("http://ubuntuforums.org/showpost.php?p=8723723") with grub 2 in 9.10 :sad:

---

### Post by tanyabefnf on 2011-01-16
> **Mujaheiden said:**
> We have a corega cg-wlusb2go wireless key.From the [manpage](http://manpages.ubuntu.com/manpages/karmic/man4/if_rum.4freebsd.html) i understand that "rum(4)" supports it.However, i need to compile it in the kernel and for that i need to put [[COLOR=#000000]lines[/COLOR]](http://www.violetin.net/ar/business/how-to-fix-mobile-phones-damaged-in-water.html) into the kernel config file.... Can somebody give me a hint as to where to start?Im not at all newbie but compiling the kernel always sounds so serious to me...It helps me out of the problem, Thanks for your effort!

---

