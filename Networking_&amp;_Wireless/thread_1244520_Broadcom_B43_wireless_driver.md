---
title: "Broadcom B43 wireless driver"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by pwhipped on 2009-08-19
I like to reinstall my operating systems frequently and have some what of a problem. It turns out that the broadcom b43 wireless driver isn't included in the ubuntu live cd. I have to be physically connected to the internet through an ethernet connection to update the driver through the hardware drivers gui. Is there any way around this? Can I write an ubuntu disk with that driver on it so that when I want to reinstall it updates automatically? Is there a way to do it manually that's simple and efficent? Thanks ahead of time guys.

---

### Post by cosine352 on 2009-08-19
[http://www.remastersys.klikit-linux.com/ubuntu.html](http://www.remastersys.klikit-linux.com/ubuntu.html)

you can install it by
> sudo apt-get install remastersys

---

### Post by pwhipped on 2009-08-19
> **cosine352 said:**
> [http://www.remastersys.klikit-linux.com/ubuntu.html](http://www.remastersys.klikit-linux.com/ubuntu.html)

you can install it by

Thank you, this is exactly what I was looking for. How do I go about finding the driver though?

---

### Post by pwhipped on 2009-08-19
Also can someone explain to me why its necessary to have a wired connection to download a wireless driver? Why has this not been included in the live cd by defualt?

---

### Post by pwhipped on 2009-08-19
bump

---

### Post by amp_man on 2009-08-20
> **pwhipped said:**
> I like to reinstall my operating systems frequently and have some what of a problem. It turns out that the broadcom b43 wireless driver isn't included in the ubuntu live cd. I have to be physically connected to the internet through an ethernet connection to update the driver through the hardware drivers gui. Is there any way around this? Can I write an ubuntu disk with that driver on it so that when I want to reinstall it updates automatically? Is there a way to do it manually that's simple and efficent? Thanks ahead of time guys.

To put it simply, no. But the driver should be there in 9.04. I actually came across your post because I've just reinstalled 9.04 myself and although the driver is installed (check the Hardware Drivers app), it's not working. I remember last time I had the same problem and it had something to do with one module loading before another one, but I can't remember the specifics. I'll let you know if I figure it out.

EDIT: you need to install the firmware before the driver can work, I forgot about that. Search around for "Ubuntu b43 firmware" and you should be able to find it. The b43-fwcutter package can automatically download the firmware, but you've stated that's not an option.

---

### Post by kerry_s on 2009-08-20
what i do is copy /lib/firmware/b43 to a usb key, then just copy it to the new install, if i can't get the ethernet from the kids, damn xbox! :lolflag:

---

### Post by pwhipped on 2009-08-20
Thank you so much guys. :D

---

