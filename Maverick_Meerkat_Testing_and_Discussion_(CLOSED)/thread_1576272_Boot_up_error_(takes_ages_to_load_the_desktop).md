---
title: "Boot up error (takes ages to load the desktop)"
date: 2010-09-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2010-09-17
As soon as i boot up i get a ton of I/O errors.

It says something like Buffer I/O error on device sr0.

I've no idea what it means.

The computer takes about 5 minutes to reach the desktop.

---

### Post by VMC on 2010-09-17
> **sonicb00m said:**
> As soon as i boot up i get a ton of I/O errors.

It says something like Buffer I/O error on device sr0.

I've no idea what it means.

The computer takes about 5 minutes to reach the desktop.

Sounds like a bad burn. What did you use, Brasero? Some are having issues with that program.


Did you try the check media from the main menu?

---

### Post by sonicb00m on 2010-09-17
It's not on the cd rom it's actually been installed since the Beta was released and been fine up until yesterday afternoon. This is happening booting the actual partition. I think it's since I upgraded to the new kernel upgrade using dist-upgrade.

---

### Post by sonicb00m on 2010-09-17
it was because i had a dvd in the drive! Why would it do that on bootup to the OS though?

---

### Post by ronacc on 2010-09-17
take a look at /etc/fstab and see if maybe the OS is trying to mount SR0 at boot up , if so comment out that line in fstab .

---

### Post by cariboo on 2010-09-17
There shouldn't be anything in /etc/fstab about mounting the cdrom, it is now handled by udev, which automatically tries to mount the CD. It might be an idea to submit a bug about the order in which upstart/udev tries mount the disk. In other words, mount the disk after the desktop has loaded.

---

### Post by ronacc on 2010-09-17
I know that there "shouldn't" be an entry in fstab for a cd/dvd drive or USB stick but I have had it happen , it don't hurt to check .

---

### Post by sonicb00m on 2010-09-17
There wasn't an extra line in fstab. Thanks anyway.

---

