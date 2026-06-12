---
title: "Ubuntu 11.04 boots to shell"
date: 2011-02-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tadp0le on 2011-02-14
Hi,

I've just tried installing the latest Ubuntu on my machine but it will only boot to a shell, see pic.

Other OS (WinXP/7/SuSe) will install and run correctly (and Ubuntu will run fine from a CD) but when it tries to boot from the HD (after installing) it displays the following.

Any information on how this could be overcome would be well received.

Thanks.

---

### Post by howefield on 2011-02-14
Thread moved to  *"Natty Narwhal Testing and Discussion"*.

---

### Post by VMC on 2011-02-14
> **tadp0le said:**
> Hi,

I've just tried installing the latest Ubuntu on my machine but it will only boot to a shell, see pic.

Other OS (WinXP/7/SuSe) will install and run correctly (and Ubuntu will run fine from a CD) but when it tries to boot from the HD (after installing) it displays the following.

Any information on how this could be overcome would be well received.

Thanks.

Not sure about that "uAlert" line.  Ca't see the end of the line. Did the install complete ok? Also did the ISO give correct md5sum.

---

### Post by fabricator4 on 2011-02-14
> **tadp0le said:**
> Hi,

I've just tried installing the latest Ubuntu on my machine but it will only boot to a shell, see pic.

If by "latest" you mean 11.04 Natty Narwahl, then you should be aware that that it's still an Alpha 2 release.  It won't be ready for beta testing for a month or so yet. This has been moved to 11.04 testing and discussion so something on that screen must point it it being the alpha release 

If you're interested in an OS that will be productive you should look at one of the current supported releases such as 10.10 or 10.04 LTS (Long Term Support)

From the screen it seems that the bootloader has not been able to find the kernal to boot, which most often happens if it is looking on the wrong device for some reason.  I've had this happen with installs made to a removable device.

Chris.

---

### Post by tadp0le on 2011-02-15
Thanks for the replies.

> From the screen it seems that the bootloader has not been able to find the kernal to boot,

That would make sense. When booting in recovery mode it hangs on the kernel line.

Currently it's installed on a SATA drive. I'll try installing to an IDE drive and see if I have any luck.

---

### Post by fabricator4 on 2011-02-15
> **tadp0le said:**
> 
Currently it's installed on a SATA drive. I'll try installing to an IDE drive and see if I have any luck.,

Hi, 

in addition to this, if it's a simple device pointer error then it can be possible to get it to boot by editing the device name.  When grub gives you a list of OS or kernals to boot, highlight the one you want and press 'e'.

Look for a line which will be something like:

/dev/sdb1/...

sda is the first physical HDD, sdb is the second and so on.  The number following is the number of the partition, so partitions on the second hard drive might be labelled sdb1, sdb2, sdb3 etc.

Change this to the correct device/partition and you might be able to get it to boot.  

Changes you make here are not permanent.  Once you get it to boot you should go to the command line and type

```

sudo update-grub

```

to get grub reconfigured with the current correct boot devices.

I'm still not sure exactly which Ubuntu you are using.  Are you actually trying to install 11.04 Natty Narwhal?

Chris

---

