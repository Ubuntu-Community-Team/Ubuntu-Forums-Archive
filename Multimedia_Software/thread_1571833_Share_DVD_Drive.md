---
title: "Share DVD Drive"
date: 2010-09-10
forum: Multimedia Software
---

### Post by vaslat29 on 2010-09-10
Is there a way I can share a DVD drive between one laptop installed with Ububtu 10.04 and a netbook on Windows 7? I would like to installed some software (that on a DVD) to my netbook using the drive available on my laptop.

---

### Post by Grenage on 2010-09-10
I've never done it, but it should be a simple case of using Samba to share the CD mountpoint.

For example: /media/cdrom0

You can do that via the GUI, by right-clicking on the directory and selecting "Sharing Options".

---

### Post by vaslat29 on 2010-09-10
> **Grenage said:**
> I've never done it, but it should be a simple case of using Samba to share the CD mountpoint.

For example: /media/cdrom0

You can do that via the GUI, by right-clicking on the directory and selecting "Sharing Options".

When I try that I get the message that I do not have permissions to chnang folder permissions - I am logged in as Admin.

---

### Post by Grenage on 2010-09-10
This is on the Ubuntu machine, right?  I'm also assuming that you aren't actually logged in as root - because that's disabled by default.

From a terminal:

```
gksu nautilus /media
```

Then try.  There are preferable, more elegant ways to go about this - but this is quick and simple.

---

### Post by Colin Keenan on 2010-09-18
I found this discussion by searching on sharing DVD drive.

Grenage, I had already tried your method (right-click on media/name-of-dvd and share it) but it doesn't work because I need to grant access to the dvd for guests without an account on my Ubuntu machine and when Ubuntu tries to change the permissions on the dvd, it can't, since the dvd is not writeable, of course.

The difference between what you suggest and my system is that there is no media/cdrom0 or whatever in media until a dvd is inserted.  Once the dvd is inserted, it is automatically mounted in the media folder as a folder with the same name as the dvd that was inserted.  That folder is write protected as is the dvd itself (being a movie, after all).

Even when I share it without granting permission to guests, I still can't access it using my user id and password.  Even though the dvd shows up in Windows Network Places, when I try to open it from Windows, put in my user id and password, it says I don't have permission to open it.  My user id does have permission to access the files according to Ubuntu though.  I also ran Samba and made sure I knew what the Samba password was for my user id, but it just won't work.

Did anyone actually succeed in sharing their Ubuntu dvd with a Windows computer?

---

### Post by Leafarpice on 2010-11-18
I was able to do it by following these steps:

1. Create a new folder: media/DVD0
2. Find out the device identifier for your DVD drive. You can check using the Disk Utility or your preferred way
In my case the DVD drive is on /dev/sr0

3. Update your etc/fstab with the following:
/dev/sr0        /media/DVD0   iso9660 ro,user,noauto  0       0

4. Mount your devices with: sudo mount -a

Step 3 will automatically mount your DVD drive always to the media/DVD0 folder. So you do not have to worry about the DVD name. Now you can share the media/DVD0 as you would any other folder. Hope this helps

---

