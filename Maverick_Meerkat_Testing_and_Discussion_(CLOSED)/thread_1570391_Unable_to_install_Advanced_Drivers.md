---
title: "Unable to install Advanced Drivers"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by gibbylinks on 2010-09-08
Hi All,

I've just installed the Beta 10.10 on my Dell laptop which uses the Broadcom wireless chip. 

On 10.04 I just installed the restricted STA driver and it worked. (Had to be connected to net initially with Cat 5 cable to get it)

With Meerkat when I try to install the drivers (now under "Advanced drivers" I think) it gets so far downloading and then "bombs out" with a Jockey GTK error.

any one else seen this ? :sad:

---

### Post by ronacc on 2010-09-08
what is the error message you are getting ? The downloaded .deb should be in /var/cache/apt/archives  , try installing it from a terminal with dpkg .
```
sudo dpkg -i <path to package>
```

that may give you more information .

---

### Post by coffeecat on 2010-09-08
Have you tried installing the bcmwl-kernel-source  pacakge from the live CD as described here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

... and then activating the STA driver with Advanced Drivers?

---

### Post by gibbylinks on 2010-09-09
This is what I get when trying to install using apt

```
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-20-generic
Building for architecture x86_64
Building initial module for 2.6.35-20-generic
/usr/sbin/dkms: line 35: patch: command not found

Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Methinks it's broken somewhere !!

---

### Post by gibbylinks on 2010-09-09
Right I did wot I should have done to start with and searched this forum for "Broadcom"

After reading this thread [http://ubuntuforums.org/showthread.php?t=1535893&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1535893&highlight=broadcom) it looks like the "Additional Drivers" isn't pulling in all the dependencies it needs. I didn't have "build essential" anf the associated files installed.

Once I installed these in synaptic everything worked OK.

Now up and running wirelessly. ):P

---

### Post by cariboo on 2010-09-09
I just plug in a network cable, it pulls in all the needed dependencies from the repositories for the STA driver.

---

### Post by gibbylinks on 2010-09-10
> **cariboo907 said:**
> I just plug in a network cable, it pulls in all the needed dependencies from the repositories for the STA driver.

Yes in the past that's always worked for me. But not on this occasion.

---

