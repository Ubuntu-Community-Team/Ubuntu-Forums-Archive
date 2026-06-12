---
title: "Broadcom on 2.6.34"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by zoomy942 on 2010-05-20
So i installed kernel 2.6.34 to fix my lid closing issue, and that went great.  but now when i go to reinstall my broadcom i get this error....
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.34-020634-generic
Building for architecture i686
Building initial module for 2.6.34-020634-generic

Error! Bad return status for module build on kernel: 2.6.34-020634-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
zimmerman@ubuntu-netbook:~$ 

```


and if i do it through package manager, i get an error 10?

---

### Post by zoomy942 on 2010-05-20
subscribed

---

### Post by zoomy942 on 2010-05-21
i had to go back to 2.6.32.

noone has any ideas?

---

### Post by matthew.parlette on 2010-06-10
I have the same problem, upgraded the kernel for TRIM support (for my SSD), and I've tried numerous methods to get the driver active for the broadcom device (mine is BCM4313), but every time I get some sort of error.

When I use the 10.04 live CD with 2.6.32 kernel, it installs the driver and works just fine. I'll let you know if I find anything to get this resolved, but I fear I may be moving back to that kernel version as well.

---

### Post by zoomy942 on 2010-06-10
wow!  someone finally read my thread. lol!

---

### Post by matthew.parlette on 2010-06-10
I'm glad I could bring you some joy. Sadly I don't think I know enough to actually help out, so try to contain yourself :)

I'm trying 2.6.33 as we speak, so I'll let you know if I have any more luck with that.

If that doesn't work, I'll be going back to 2.6.32 until I can find a better fix, so I'll certainly keep you updated.

---

### Post by zoomy942 on 2010-06-11
well you are awesome nonetheless.

the reason i want the newer kernel is because stand by when i close the lid on my netbook actually wrks on the nwere ones and not the old ones.

---

### Post by matthew.parlette on 2010-06-11
Now this is strange, I have three kernels available on my install, 2.6.32, .33, and .34. Now, when I boot to the Live CD (2.6.32) it lets me install the Broadcom driver and use it just fine. When I just tried to boot to the 2.6.32 kernel, it gives me an error when trying to activate the Broadcom driver (I think it was InstallPackage() failed, but that's from memory).

So that's weird. I think there is a 10.10 alpha out right now, so I might just give that a try, since I have nothing on this laptop yet, and see what happens with that. I'll let you know my results if I decide to do that, or I may reinstall 10.04 to see if it works with that.

I'll keep you updated if I can get it working on a later kernel, that lid close issue would sure be annoying.

---

### Post by simarr24 on 2010-06-14
Had the same problem. Here is what I did to fix it.

Updated Kernel to 2.6.34 following this post

[http://usablesoftware.wordpress.com/2010/05/26/switch-to-a-newer-kernel-in-ubuntu-10-04/]("http://usablesoftware.wordpress.com/2010/05/26/switch-to-a-newer-kernel-in-ubuntu-10-04/")

Notice what he/she about the Broadcom chipset.

Then I just reinstalled Bcwml-kernel-source. * Make sure you are connected via Ethernet first. Then restart and if all goes well, it should work.

```
sudo apt-get install --reinstall bcwml-kernel-source
```

Hopes this help. I know I been pretty frustrated for the last few days trying to do this. Good luck.

---

### Post by zoomy942 on 2010-06-14
do you mean this command?

cd /usr/src/linux-headers-2.6.34-020634-generic/include
sudo cp generated/* linux/

---

### Post by simarr24 on 2010-06-14
I did that command. But it didn't work for me. So just restarted the computer and did the reinstall bcwml-kernel command and restarted, and it worked.

---

### Post by the_real_bubba on 2010-06-16
> **simarr24 said:**
> 
```
sudo apt-get install --reinstall bcwml-kernel-source
```


bcmwl-kernel...

---

### Post by zoomy942 on 2010-06-16
retry it and see if it worked...  i'm going to reinstall ubuntu tonight (had lubuntu) and maybe test this too.

---

### Post by zoomy942 on 2010-06-16
i will try 2.6.35 tonight

---

### Post by RavensKrag on 2010-07-20
Did you ever solve your problem? If not, check out this thread, it worked for me.  Although, I ignored the part about blacklisting.

[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

---

