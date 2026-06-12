---
title: "ACER aspire 5750 broadband issue on ubuntu 10.04 LTS"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by mi6crazyheart on 2011-08-03
I've recently purchased a new laptop of ACER(aspire 5750). I've installed two OS(win-7 & ubuntu 10.04 LTS). Till now, on my ubuntu every things working fine except i can't able to access my cable model broadband. 

I open up the "Network connections" section & at there i saw it can't able to detect any WIRED connection. 

I've checked my all my ethernet jack & all rest of connection. All r perfect. But, don't know why it can't able to detect my broadband. But, in windows section, broadband is working fine.

NOTE: ACER aspire 5750 using Broadcom netlink 57785 gigabit ethernet PCIe

Plz, any body can give me some help to solve this problem...

Thx in advance

---

### Post by mi6crazyheart on 2011-08-04
Guys, yet now no reply... :( . BDW, is ubuntu 10.04 LTS has any issue with Broadcom netlink BCM 57785 gigabit ethernet PCIe... ?

---

### Post by rangana on 2012-02-22
i have the same issue :( ... did you solve your problem?? please tell me the method??

---

### Post by panrin on 2012-02-22
I've recently purchased a new laptop of ACER.  Till now, on my ubuntu  every things working fine except i can't able to access my 3g maneger. 

I open up the "Network connections" section 
I've checked my all my ethernet jack & all rest of connection. 

Plz, any body can give me some help to solve this problem...

---

### Post by rangana on 2012-02-22
[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-10-04-lts-in-laptop-acer-aspire-5750g-does-not-see-wired-internet-903890/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-10-04-lts-in-laptop-acer-aspire-5750g-does-not-see-wired-internet-903890/)

this link suggests a method... but i can't understand it :confused:

---

### Post by mi6crazyheart on 2012-02-23
The solution of this problem is really very easy. Just download the linux broadcom driver from following link.. 

Link: [http://www.broadcom.com/support/ethernet_nic/netlink_k57.php](http://www.broadcom.com/support/ethernet_nic/netlink_k57.php)

**Follow these steps:**
Building Driver From TAR File
=============================

The following are general guidelines for installing the driver.

1. Create a directory and extract the files:

   tar xvzf tg3-<version>.tar.gz

2. Build the driver tg3.o (or tg3.ko) as a loadable module for the
running kernel:

   cd src
   make

The driver will be compiled for the running kernel by default. To build
the driver for a kernel different than the running one, specify the
kernel by defining it in KVER:

  make KVER=<kernel version>

where <kernel version> in the form of 2.x.y-z is the version of another
kernel that is installed on the system.

3. Test the driver by loading it: 

   insmod tg3.o
or
   insmod tg3.ko (on 2.6.x kernels)
or
   insmod tg3

4. Install the driver:

   make install

See RPM instructions above for the location of the installed driver.

5. To configure network protocol and address, refer to various Linux
documentations.


For more info you can also check the "readme.txt" file which comes with that driver(TAR file).

---

