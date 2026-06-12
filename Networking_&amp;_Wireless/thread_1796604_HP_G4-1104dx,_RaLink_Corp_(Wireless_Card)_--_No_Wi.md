---
title: "HP G4-1104dx, RaLink Corp (Wireless Card) -- No Wireless Detection"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by anuradavijay13 on 2011-07-04
Hi, my brand new HP G4-1104dx with a Ralink Corp wireless card refuses to display any wireless connections. It is not recognizing my wireless card. 

I went to the Ralink site, downloaded the patch for the wireless card model (for Linux) and did a 'make' in the folder. All went smoothly, but still no connection. 

What do I do?? Please help.

---

### Post by anuradavijay13 on 2011-07-04
Addtionally, lspci -v | less gives me the the following (for more precise information):

01:00.0 Network controller: Ralink corp. Device 5390
        Subsystem: Hewlett-Packard Company Device 1636
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at c2500000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

Thanks.

---

### Post by chili555 on 2011-07-04
Please check here. If yours is not a 64-bit system, simply omit the x86_64 patch.

[http://ubuntuforums.org/showthread.php?p=10924640#post10924640](http://ubuntuforums.org/showthread.php?p=10924640#post10924640)

Post back if you get stuck or need more help.

---

### Post by anuradavijay13 on 2011-07-04
chili555, I got it done! Excellent! Thank you for the help!

---

### Post by chili555 on 2011-07-04
Outstanding, sir or madam, as the case may be. Glad it's working. Have fun.

When Update Manager gives us a later kernel version, known as linux-image in Ubuntu-land, you'll need to rebuild the module agaimst the later kernel:```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su 
make clean 
make
make install
modprobe rt5390sta
exit
```As always, post back if we can help you further.

---

### Post by ATMOS_SKY on 2011-08-05
How do we make a configuration that includes this wireless driver update after every fresh kernel?

I would like to have to do nothing when a update my kernel and have it included in the kernel "install".

Could we code a bash script on the place it on the tool bar so whenever the kernel  is updated the user would click the script and it would install the wireless driver?

I think that would be better than locking the kernel.  Any other ideas?

Thank you for helping solve this!

---

### Post by chili555 on 2011-08-05
I am quite sure you could. I am no bash coder, so someone a bit more adept than me will have to do the not very hard work. We look forward to your results.

---

### Post by ATMOS_SKY on 2011-08-05
Not to re-invent what it looks like you already solved but what do you think of using this driver provided by HP for SUSELinux?

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&swItem=ob-92830-1&jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&swItem=ob-92830-1&jumpid=reg_R1002_USEN)

---

### Post by ATMOS_SKY on 2011-08-05
> **ATMOS_SKY said:**
> Not to re-invent what it looks like you already solved but what do you think of using this driver provided by HP for SUSELinux?

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&swItem=ob-92830-1&jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&swItem=ob-92830-1&jumpid=reg_R1002_USEN)

What am I thinking... It looks like you have taken the SUSE and modified it for Ubuntu...

Thank you for your excellent support!!

Appreciate you helping us newbies

---

### Post by chili555 on 2011-08-05
When it's untarred, it is an rpm, the file format for packages in Suse, Red Hat and others. If you converted it to .deb with *alien*, you'd find version 2.4.0.1 of the driver. The process above installs 2.4.0.4 and 2.5.0.3 is now available. I'm not sure the best way is to convert an rpm to deb and then end up with an older version unless you are running an older kernel; 2.6.32 perhaps.

---

