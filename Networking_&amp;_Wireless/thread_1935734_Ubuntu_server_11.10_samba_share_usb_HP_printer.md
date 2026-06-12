---
title: "Ubuntu server 11.10 samba share usb HP printer"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by bpb_21 on 2012-03-04
I've spent literally days trying to figure this out, after abandoning the project for a while last year.

Is it possible to have one Ubuntu Server 11.10, headless, accessed by SSH, used to back up files from a Ubuntu 11.10 desktop (er, laptop) and a Windows 7 desktop, both using it as a backup drive, AND connect an HP Officejet 5610 printer by USB to the server, and have it shared on the local network so that the desktop Windows 7 PC, the Ubuntu laptop, an Android 4.0.3 tablet and an Android phone can all "see" it and print to it on the same local network?  (Granted, it would take some apps for the tablet and phone.)

I'm beginning to think this is impossible (for me).  I've read every "man" page for anything even remotely related, scoured the forums for answers, searched the CUPS and HPLIP web pages, combed through the Ubuntu Server Guide, and pulled out all the hair I have left.

Is it even worth my time, or should I just break down and buy a new network/wireless-ready all-in-one?  It seems like a waste, since there's nothing wrong with the HP 5610, but I sure can't get it to do anything.  Makes me want to replace all this junk with Apple iProducts (ok, that's going a little far)...

---

### Post by lisanels47 on 2012-03-04
For the printer issue, I would say since it's headless, install webmin on that server, and use any browser to config the printer and samba file sharing.  

[https://serveripiaddress:10000](https://serveripiaddress:10000)

---

### Post by bpb_21 on 2012-03-04
Aha!  This looks promising.  Thanks!

---

### Post by bpb_21 on 2012-03-11
> **lisanels47 said:**
> For the printer issue, I would say since it's headless, install webmin on that server, and use any browser to config the printer and samba file sharing.  

[https://serveripiaddress:10000](https://serveripiaddress:10000)

Thanks for the tip; webmin looked promising but it isn't useful for printing on this system (i.e. keeps saying "file doesn't exist" and ultimately does nothing regarding the printer module).  I'm really at wit's end; gonna break down and buy a printer I can plug directly into my router.  This is useless.  However, I sincerely appreciate your reply and suggestion.

---

