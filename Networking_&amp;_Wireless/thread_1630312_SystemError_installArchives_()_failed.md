---
title: "SystemError: installArchives () failed"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by LinuxFreakazoid on 2010-11-25
I've been having an issue ever since I recently installed Ubuntu 10.10. It won't connect to my network for some reason. I enter the WEP key and all the other info, but it fails to connect. I tried to install the Broadcom STA Driver under Additional Drivers but then I get an error message saying SystemError: installArchives()failed.
Is there a solution to this type of issue?

---

### Post by mejoe2 on 2010-11-25
I am having this same problem running 10.10 Netbook Edition on USB drive. I tried the solution proposed here:
[http://ubuntuforums.org/showthread.php?t=1545127](http://ubuntuforums.org/showthread.php?t=1545127)

It did not work for me.

I have also tried this with no luck:
[http://ubuntuforums.org/showthread.php?t=1593717](http://ubuntuforums.org/showthread.php?t=1593717)

---

### Post by LinuxFreakazoid on 2010-11-25
> **mejoe2 said:**
> I am having this same problem running 10.10 Netbook Edition on USB drive. I tried the solution proposed here:
[http://ubuntuforums.org/showthread.php?t=1545127](http://ubuntuforums.org/showthread.php?t=1545127)

It did not work for me.

I have also tried this with no luck:
[http://ubuntuforums.org/showthread.php?t=1593717](http://ubuntuforums.org/showthread.php?t=1593717)

For some reason, I can install the wireless drivers in Live CD mode but when I installed Ubuntu I couldn't. I just find that odd. I've tried a few solutions, but they never worked for me.

---

### Post by VE. on 2010-12-10
Is there any progress on this? I'm having the exact same problem.

---

### Post by paj792 on 2011-01-13
Found an error in the installer log /vmlinuz does not exist. It points to the wrong location. Remove symbolic link /vmlinuz :

# rm /vmlinuz

and make a new one pointing to the correct location. In my case this was:

# ln -s /cdrom/casper/vmlinuz /vmlinuz

Check your link works ok before doing anything else!

root@ubuntu:/# ls -Ll /vmlinuz
-rwxr-xr-x 1 root root 4033440 2011-01-13 21:37 /vmlinuz


Hope this helps.

---

### Post by paul.gevers on 2011-02-13
I found that on my system I needed to install lzma. Continuing from there succeeded. This should be considered a bug. I continue my investigation and will report it.

---

