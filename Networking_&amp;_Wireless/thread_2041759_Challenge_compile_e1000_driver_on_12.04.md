---
title: "Challenge: compile e1000 driver on 12.04"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by bomski on 2012-08-13
Well after banging my head on a brick wall for a couple of days; i've decided to ask the community to help me solve this one...

I have an Intel 82457GI ethernet controller; which once upon a time could achieve gigabit speeds; now as the driver has moved to a kernel-only support model it can only achieve < gigabit speeds. After reading much about this, apparently compiling the drivers found here:

[http://sourceforge.net/projects/e1000/](http://sourceforge.net/projects/e1000/)

may solve the issue; but can i compile this? not a chance; i've tried allsorts... 

So... anyone figure a way to compile this (and document how they compiled it!)?

---

### Post by chili555 on 2012-08-13
It seemed pretty straightforward to me. Download the file to your desktop and right-click it and select Extract Here. Open a terminal and do:```
sudo apt-get install build-essential linux-headers-generic
cd Desktop/igb-3.4.8/src
sudo su
make
make install
exit
```I didn't actually install it but it 'makes' perfectly on my 12.04 system.

I will be surprised if it achieves gigabit speeds when the in-kernel won't.

---

### Post by bomski on 2012-08-13
igb compiles on my system too; its the e1000 driver which doesn't... 

[http://sourceforge.net/projects/e1000/files/e1000%20stable/](http://sourceforge.net/projects/e1000/files/e1000%20stable/)

I continually receive the error: 

fatal error: linux/pm_qos_params.h No such file or directory

ze plot thickens...

---

### Post by chili555 on 2012-08-13
I was just going by the link you gave me. igb doesn't work for you?> fatal error: linux/pm_qos_params.h No such file or directory
That's because linux-source-3.1/include/linux/pm_qos_params.h file exists in 3.1.x kernels but missing in 3.2.x kernels. In other words, the file you want to compile is incompatible with kernel 3.2.xx in 12.04.

---

### Post by bomski on 2012-08-14
as far as I can tell; igb does not contain the correct e1000 driver set; there's been numerous patches issued to resolve the compiling issue in 12.04; but my knowledge of applying patches is very limited...

---

### Post by DaSuperGrover on 2012-10-10
Anybody got this driver to compile succesfully?

---

### Post by chili555 on 2012-10-10
> **DaSuperGrover said:**
> Anybody got this driver to compile succesfully?They probably aren't going to, either. *e1000* is included in the mainline kernel and the file referenced above hasn't been updated to 3.2.xx kernels.

---

### Post by DaSuperGrover on 2012-10-10
Ok, thanks. I just don't understand why the transfer is so ridiculously slow, more like 100 mbit instead of 1Gbit :-(

---

### Post by icelander on 2012-10-13
Has there been an update on this? The latest version of the driver on SourceForge is from September 2012, so I imagine it's been updated for the 3.2 kernel. I managed to get it to update, but I can't seem to get it to install the appropriate driver.

I'd really hate to have two gigabit ethernet ports that are stuck at 10Mbit because the drivers are broken.

---

