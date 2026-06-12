---
title: "RALINK RT5390 Problem"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by kw12589 on 2011-09-07
I have successfully installed the driver for the RALINK RT5390 card on my HP Laptop, for kernel version 2.6.38-8.
However, when update manager creates a new kernel (2.6.38-11 now), the wireless driver is not brought into the new kernel.
How can I get it working for the new and future kernels?

I originally installed the driver using the opensuse RPM and manually applying the patches as directed. However, with the new RPM patching fails.

Thanks, 
Keith

---

### Post by wildmanne39 on 2011-09-07
Hi, this is how you usually do it but I am not sure about rpm but it should work.
```
cd Desktop/test/2010_1216_RT5390_LinuxSTA_V2.5.0.3_WiFiBTCombo_DPO or whatever the name and path of your driver is then do
sudo su
make clean
make
make install
modprobe rt5390sta
exit
```
This has to be done after every kernel upgrade as long as the driver is compiled.
Thank you

---

### Post by praseodym on 2011-09-07
Did you install the kernel-headers metapackage and dkms?

```
sudo apt-get install linux-headers-generic dkms
```

---

### Post by kw12589 on 2011-09-08
No, I did not install either package. What do they do?

---

### Post by kw12589 on 2011-09-08
I guess I have to go back to the original RPM I used and try that.
Thanks for the help.

Keith

---

### Post by kw12589 on 2011-09-08
I checked the Ubuntu Software Center and I do have dkms and linux kernel headers for headers version 2.6.38 on x86/x86_64 installed for 2.6.38-8,10 & 11

---

### Post by wildmanne39 on 2011-09-08
Hi, that is good then if you do what I said in post 2 it should get your wireless working again.
Thank you

---

### Post by praseodym on 2011-09-08
You need those 2 packages to compile. Install them by booting into the kernel 2.6.38-8. Reboot, hold the SHIFT-button during boot and choose "previous Ubuntu versions". There you choose 2.6.38-8, install the packages and reboot into the latest kernel.

---

