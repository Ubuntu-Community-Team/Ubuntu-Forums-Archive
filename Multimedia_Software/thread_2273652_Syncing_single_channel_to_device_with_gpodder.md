---
title: "Syncing single channel to device with gpodder?"
date: 2015-04-14
forum: Multimedia Software
---

### Post by jimford on 2015-04-14
I've got lots of channels on gpodder, but I don't want to sync them all to my Android 'phone, which 'sync to device' does.

Is there any way I can just sync one channel (or one episode) to a device, please?

Jim

---

### Post by tgalati4 on 2015-04-15
This is a Use Case that *gpodder* was not programmed for.  However, you can create a local folder then click on one podcast episode and right-click "send" to local folder.  You can do this with a group of podcasts, just highlight and right-click.  Then there are several ways to copy those podcasts to your phone including folder-sync apps.

---

### Post by jimford on 2015-04-15
Thanks for the reply 'tgalati4'.

I went with the 'send to local folder' option. With the 'phone file system mounted via usb I was able to send the files to the 'phone.

Jim

---

### Post by tgalati4 on 2015-04-15
I wish there was an easier way, but *gpodder* was programmed before smartphones.  You will find many popular podcasts have Android apps, so you can listen to individual episodes that way as well.  

If you are clever, you can create a local mount point and write a udev rule to always mount the correct phone directory to that local mount point.  Then you can use the same "send to local folder" option.  This can be tricky to set up with some phones.

I have not tried it, but there is a *gpodder* for Android.  That way you can load the podcasts directly to your phone.  [http://gpodder.org/news](http://gpodder.org/news)

---

### Post by jimford on 2015-04-15
> **tgalati4 said:**
> 
If you are clever, you can create a local mount point and write a udev rule to always mount the correct phone directory to that local mount point.  Then you can use the same "send to local folder" option.  This can be tricky to set up with some phones.

My 'phone (Moto G with Android Lollipop) automounted on the Ubuntu file system when I connected it with USB.  I was then able to browse to the download directory when I did 'send to local folder' on gpodder. Works a treat!

Jim

---

