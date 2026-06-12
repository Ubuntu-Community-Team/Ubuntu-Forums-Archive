---
title: "Can't get past blinking login termianl"
date: 2009-11-22
forum: Multimedia Software
---

### Post by le_vainqueur on 2009-11-22
I have 9.10 installed on my desktop which has been working well for a while.  My graphics card recently fried, though, so I had to switch over the the motherboard for my monitor.  However, I am not able to get into gnome.  When I get past grub, I can only get to a login terminal which is blinking incessantly.  

I tried "sudo dpkg-reconfigure xserver-xorg", but that didn't help.  I couldn't find anything else useful in other threads. What can I do? My motherboard is:

Intel D946GZIS

---

### Post by squaregoldfish on 2009-11-23
I think this may be to do with your machine trying to start X with the drivers for your graphics card, and it's crashing because the card isn't there. This confuses gdm into trying to restart the X server, giving you an infinite loop (hence the blinking).

If you can ssh into the box, do so and stop gdm:

```
sudo service gdm stop
```

This should leave you with the text login you can actually use, at which point you can reconfigure your xorg.conf file. You can test it by using the startx command - if this fails, it will just dump you back to the text console so you can figure out what's wrong.

If you don't have ssh, you could try booting from a live cd, mounting your hard drive and disabling the gdm service altogether. That way, when you boot you'll get the text login.

Hope I explained that well enough.

Steve.

---

### Post by squaregoldfish on 2009-11-23
Another thought - try simply removing your xorg.conf file (put it in a safe place though!). X may be able to get going using its own default configuration.

Steve.

---

