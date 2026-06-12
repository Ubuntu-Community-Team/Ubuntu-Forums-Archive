---
title: "Linksys WUSB-300N not 64 bit = bad magic"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by Zalokin on 2011-02-08
Hi,

My USB WIFI device is Linksys WUSB 300-N.
I use Ubuntu 10.10 amd64.

I installed relevant ndiswrapper including ndigtk sucessfully.

I installed netmw245 driver under Wireless Network Drivers sucessfully.
It states "Hardware present:yes"

The above implies that the system is detecting the device... but it only goes as far as that.

When I type: -

#dmesg | grep ndis

I get the following: -

[   11.768164] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   13.056138] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   13.056177] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netmw245'
[   13.056475] ndiswrapper (load_wrap_driver:10: couldn't load driver netmw245; check system log for messages from 'loadndisdriver'
[   13.058318] usbcore: registered new interface driver ndiswrapper

The above implies that the 32 bit driver doesn't like my 64 bit Ubuntu.

I installed ia32libs and all of its components and still no luck.

Is it actually possible to run WUSB300N WIFI device on a 10.10 64 bit Ubuntu?

I'm actually determined to get this running so any suggestions would be welcome.

Thanks.

Zalokin

---

### Post by Joe of loath on 2011-02-08
Have you tried the 64 bit windows drivers?

---

### Post by Zalokin on 2011-02-08
Thanks for your helpful reply.
However, I wouldn't know what file(s) to get etc.
I have Windows 7 Ultimate 64 installed on other partition.

Zalokin

---

### Post by Joe of loath on 2011-02-08
Where did you get the drivers you're currently using?

---

### Post by Zalokin on 2011-02-08
The 32bit driver I used for Ubuntu?
It was a WUSB300N.tar from the net.

As for Windows... windows 7 64 detected the device straight away. didnt need to install a driver.

However I have a driver that came in the box of the device... however its an exe that runs in win or mac.

Is it possible to extract the windows 64 bit driver so that Ndiswrapper can use it as a functioning driver for Ubuntu?

Zalokin

---

### Post by Joe of loath on 2011-02-08
You will be using a windows driver with ndiswrapper, it allows you to use windows wireless drivers with Ubuntu.

I can't seem to find any 64 bit Windows drivers, I don't think they exist! This means I have no idea how to proceed. It may be better just to buy a new wireless adaptor, you can find them *very* cheap.

---

