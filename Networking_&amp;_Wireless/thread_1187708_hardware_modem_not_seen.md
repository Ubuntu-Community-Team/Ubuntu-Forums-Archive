---
title: "hardware modem not seen"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by arnoldjames on 2009-06-14
I have a USRobotics usb modem.  It is not recognized in 8.04.. It is *not* a winmodem.  It is a hardware modem and hasn't needed any drivers when I used Fedora and Xandros.   Was just plug in and recognized.  I ran** lsusb** and got this line: 
**Bus 004 Device 014: ID 0baf:0303 U.S. Robotics **

which would seem to be the modem.  Searching around these forums suggests that I need **cdc_acm**, but I cannot find it and don't know exactly what I might need to do if I did.  I can't determine if it is a driver or a kernel module or what. If anyone could point me in the right direction I'd be very thankful.

---

### Post by Shazaam on 2009-06-15
Have you ran scanmodem yet? It will help you identify your modem's chipset...
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

---

### Post by arnoldjames on 2009-06-15
Yes, scanmodem told me I need the cdc_acm thing.  I plugged the modem into a Xandros linux box and it says this is indeed the driver loaded.  It hotplugs on that distro.  Evidently there is a driver somewhere that ubuntu does not have natively.  So far cannot find it generally  I have 2 other pcmcia card modems that also are hardware modems and plug& play on other Linuxes, but alas, this is a notebook computer without card slots. :(  I know that not many people need a working fax modem anymore.  But I have to fax pretty regularly.

This is the modem:   USR 5637: [http://www.usr.com/support/product-template.asp?prod=5637](http://www.usr.com/support/product-template.asp?prod=5637)

The info page: [http://www.usr.com/support/5637/5637-ug/install.html#linux](http://www.usr.com/support/5637/5637-ug/install.html#linux)  says > You need a USB modem driver (CDC ACM) compiled into a Linux kernel 2.4.20 or higher or as a loadable module for your kernel. Installation of the modem under these kernels is fully automatic provided your kernel has the Plug and Play module enabled (default). You do not need to install any drivers off the USRobotics installation CD-ROM.  But it appears not to be true.   I have plug and play installed, just missing this driver.  

Thanks in advance for any help.  Although I have used Linux for about 5 years, I have never had modem issues, so am actually pretty much in the dark about what to do and the winmodem help in these forums would not seem to apply to a hardware modem (?)  Any direction is welcomed.

---

### Post by jmdsdf on 2009-09-05
Post the outputs of these commands... maybe you have the problem I have (with 2.6.31 kernels) here is what I get:

```
df@jmdsdf:~$ uname -a
Linux jmdsdf 2.6.30-02063005-generic SMP Mon Aug 17 10:27:38 UTC 2009 i686 GNU/Linux
df@jmdsdf:~$ lsusb | grep 0baf
Bus 002 Device 003: ID 0baf:0303 U.S. Robotics 
df@jmdsdf:~$ lsmod | grep cdc
cdc_acm                15424  2 
df@jmdsdf:~$ cat /dev/ttyACM0
[no error just waits to dump text from modem, hit Ctrl-C to quit]

```

I notice that with some versions of 2.6.30, and certainly 2.6.31 I can't access /dev/ttyACM0. It throws an input/output error message. I really want to get this modem working with newer kernels, as I already had a modem and went out of my way to purchase a Linux compatible modem. I don't want to buy another one!

UPDATE: This seems fixed now by: [http://bugzilla.kernel.org/show_bug.cgi?id=14103](http://bugzilla.kernel.org/show_bug.cgi?id=14103)

UPDATE 2: Now working again in 2.6.31-12 & higher.

---

