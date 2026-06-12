---
title: "Shotwell - &quot;Cant't lock Camera&quot; error with iPhones"
date: 2012-07-27
forum: Multimedia Software
---

### Post by Gink on 2012-07-27
Hello, I've searched high and low for info on this problem. Google, shotwell bug reports, shotwell mailing list, and the forum here, hopefully someone can give me some insight into this.

Ubuntu 12.04 64-bit, have seen this problem both on an older Lenovo Desktop and a brand new Asus Laptop.

Have both an iPhone 3GS and an iPhone 4, initial use of Shotwell went okay, was able to import photos without much trouble, but after the first import any further imports don't happen due to getting "Unable to lock Camera: Unspecified Error (-1)"

I've tried various ways of connecting/mounting the iPhones with shotwell already open, or closed, using the automount dialogs, or telling the dialogs to do nothing and opening in shotwell, or unmounting/mounting through nautilus. Not sure where the problem is taking place or what else to try that would allow shotwell to lock the "camera" and import photos.

Any advice is appreciated.

---

### Post by eric-yorba on 2012-07-29
Two things to try:

1. Make sure your iPhone isn't mounted.  If it is, it will appear in the Nautilus sidebar, where you can hit the "eject" button.
2. If your phone has a password/passcode, enter it before connecting. Unfortunately the open source driver will allow the iPhone to re-lock while it's downloading photos, which can be extremely annoying, particularly if you have a lot of photos.  (I run into this one all the time.)

---

### Post by Gink on 2012-07-29
Yeah, it tends to automount in Nautilus, but unmounting it in the sidebar still doesn't allow it to lock in shotwell. No passcodes or anything on either phone. 

I was guessing the same thing though, that it has to do with it being mounted elsewhere in the system, so I'll keep trying to work that angle, maybe figure out some command line stuff to check mounted devs and unmount the phone fully there. 

Thanks for the tips though.

--------------Edit/Update---------------

Looks like our entire problem turned out to be the one USB 3.0 port on our laptop. We have three USB 2.0 and one 3.0 and of course that's what we were plugging into. As soon as I switched to a 2.0 port everything works fine. In fact it doesn't even seem to care that both the iPhone and "Documents on iPhone" are mounted in Nautilus, so far works just fine as long as I don't use the USB 3.0 port.

---

### Post by skinnersbane on 2012-09-01
> **Gink said:**
> 

--------------Edit/Update---------------

Looks like our entire problem turned out to be the one USB 3.0 port on our laptop. We have three USB 2.0 and one 3.0 and of course that's what we were plugging into. As soon as I switched to a 2.0 port everything works fine. In fact it doesn't even seem to care that both the iPhone and "Documents on iPhone" are mounted in Nautilus, so far works just fine as long as I don't use the USB 3.0 port.

Gah!  Why did I waste 45 minutes screwing around before googling this.  Thank you.  I had the same problem (USB 3.0 port did not work USB2 port did).

---

### Post by mindwarp on 2012-11-06
Just ran into this with Ubuntu 12.10, used my USB 3.0 port without any luck, but the 2.0 port works great.

---

### Post by Mike_Longbow on 2013-02-28
> **Gink said:**
> Looks like our entire problem turned out to be the one USB 3.0 port on our laptop. We have three USB 2.0 and one 3.0 and of course that's what we were plugging into. As soon as I switched to a 2.0 port everything works fine. In fact it doesn't even seem to care that both the iPhone and "Documents on iPhone" are mounted in Nautilus, so far works just fine as long as I don't use the USB 3.0 port.

What if I don't have a USB 2.0 port available? My laptop has only USB 3.0 ports, so there's no way for me o work around this issue. Is this issue been tracked already? And if it is not, where can I file a bug report?

Regards.

---

### Post by Aries86 on 2013-06-14
Yep, seems like that was the problem. Thanks!



_________________________________________________________
Aries86

---

### Post by lateagain on 2013-08-24
If you only have usb3 ports have you tried going via a usb2 hub ?
It is supposed to be backwardly compatible.

---

