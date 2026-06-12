---
title: "Dell Optiplex 760's new Ethernet Card too new for HardyHeron"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by gmoore777 on 2009-03-02
FYI:
Got a new Dell Optiplex 760 machine with an ethernet card with an Intel Corporation 82567LM-3 Gigabit chip on it.
After installing Ubuntu 8.04 on it, the machine had no network connectivity.
No eth0 interface. Just the local interface. No /etc/resolv.conf.
No IP address.

[Dell couldn't help me (which is fine) and Dell's Ubuntu (Canonical?) support refused to help me cause I had wiped off the Windows XP that came with the machine and voided the software warranty. 
]

Solution:
Browse to [www.intel.com](www.intel.com)  
search for "82567LM-3 download".
Download the driver for the Intel® 82567 Gigabit Ethernet Controller.

gunzip e1000e-0.5.11.2.tar.gz
tar &#8211;xvf e1000e-0.5.11.2.tar
cd e1000e-0.5.11.2/src
sudo make install
(will get get a non-fatal error: something about `cat man`)

sudo rmmod e1000e;


sudo insmod /lib/modules/2.6.24-23-generic/kernel/drivers/net/e1000e/e1000e.ko;
or 
sudo modprobe e1000e;
or 
for a more permanent solution:
edit /etc/modules and add:
e1000e

---

### Post by gmoore777 on 2009-03-04
some additional notes:
I am running latest and greatest HardyHeron with kernel 2.6.24-23-generic.

i was experiencing bizarre behaviour with the newly built e1000e.ko driver that I built(see previous note).

pinging the machine would sometimes result in lost packets, or sometimes host unreachable messages. pinging to this machine was 300 ms, rather than a normal 0.200 ms to other machnines. 

Running firefox on it and displaying it to another machine was fine at first then became atrociously slow.

I fixed these issue with changing the `make` command to turn off MSI and MSI-X interrupts. (see the ReleaseNotes as provided by Intel that comes with the download, for other CFLAGS and other command line flags)

sudo make  CFLAGS_EXTRA=-DDISABLE_PCI_MSI install

The machine's connectivity is behaving normal now.

---

### Post by barmanoo on 2009-04-18
Problem not "fixed"

Hi,
I have the same problem with an Optiplex 960 with 82567LM-3 with Jaunty x86_64.
I follow exactly the above procedure (include e1000e in /etc/modules) but when I reboot the version of driver (lshw -C network) is the old one (0.3.3.3-k6)

uname -a:
... 2.6.28-11-generic #41-Ubuntu ...

Thank you for any suggestion

Olivier

---

### Post by smo0th on 2009-08-25
THANKS!!! :biggrin:

---

### Post by smo0th on 2009-08-25
> **barmanoo said:**
> Problem not "fixed"

Hi,
I have the same problem with an Optiplex 960 with 82567LM-3 with Jaunty x86_64.
I follow exactly the above procedure (include e1000e in /etc/modules) but when I reboot the version of driver (lshw -C network) is the old one (0.3.3.3-k6)

uname -a:
... 2.6.28-11-generic #41-Ubuntu ...

Thank you for any suggestion

Olivier

by using
```
sudo rmmod e1000e;
tar –xzvf e1000e-0.5.11.2.tar.gz
cd e1000e-0.5.11.2/src
sudo make CFLAGS_EXTRA=-DDISABLE_PCI_MSI install
sudo modprobe e1000e

```

should work, it worked for me, did you forgot to use the rmmod command?

---

### Post by mnamutso on 2009-09-23
Thanks a bunch...i had this problem on a Desktop i had setup a system for training the next day!! I wonder what i would have done!!

You saved me...i can now smile...

---

### Post by smo0th on 2009-09-23
> **mnamutso said:**
> Thanks a bunch...i had this problem on a Desktop i had setup a system for training the next day!! I wonder what i would have done!!

You saved me...i can now smile...

good to know!! :biggrin: it also saved my day :D this is why we should be thankful to the community and keep supporting it, then we can make someone else&#347; day ^-^ thanks gmoore777 :KS

---

