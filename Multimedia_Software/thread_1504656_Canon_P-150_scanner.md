---
title: "Canon P-150 scanner"
date: 2010-06-08
forum: Multimedia Software
---

### Post by cedomir on 2010-06-08
Hi,

Did anyone had success in installing Canon proprietary linux drivers for Canon P-150 scanner using Ubuntu 10.04? I have used deb package, and everything seems ok regarding files.

lsusb gives:
```
Bus 001 Device 002: ID 1083:162d Canon Electronics, Inc. 
```

but sane-find-scanner and scanimage -L returns no scanner

additional info, with debug on, sane-find-scanner returns:
```
[sanei_usb] sanei_usb_init: device 0x1083/0x162d, interface 0 doesn't look like a scanner (0/8)
[sanei_usb] sanei_usb_init: device 0x1083/0x162d: no suitable interfaces
```


Thanks,
Cedomir

---

### Post by cedomir on 2010-06-09
After more debugging, I think that the problem is in the usb interface class (lsusb  -v) of P-150 which is 8 (mass storage), and that class is considered by sanei as "not scanner device".

Any ideas for workaround (except rewriting sane-backend source ;) )?

thanks,
cedomir

---

### Post by cedomir on 2010-06-09
Solved.

Turn off the switch on the back of the device and everything works fine :)

---

### Post by MystaMax on 2010-06-09
Hello, glad you got it working.

Do you mind me asking what applications you use with this scanner on Ubuntu? I'm trying to help a family go 'paperless', and considered this scanner as starting point. 

Are you impressed w/ its speed? It'd mostly be used to scan contracts to PDF format and be mailed to customers.

Any comments or opinions is appreciated.

Thanks in advance.

---

### Post by czr on 2010-07-25
Since this is the page that people might find via google, might just as well drop a link here to my blog which contains some painful information about [canon p-150 support and Linux]("http://lowerstrata.blogspot.com/2010/07/canon-p-150-and-linux.html") .

As for the scanning speed, it's pretty decent (for 600 DPI B&W A4 duplex scanning, average page scanning speed is about 7 seconds).

---

### Post by veprus on 2011-03-31
I have this scanner, and I'm using ubuntu 10.10 64-bit. Canon original driver supports 32-bit Linux only. I've made all steps desribed in [http://lowerstrata.blogspot.com/2010/07/canon-p-150-and-linux.html](http://lowerstrata.blogspot.com/2010/07/canon-p-150-and-linux.html) and I was not succed.

Now if I run sane-fine-scanner it returns 

found USB scanner (vendor=0x1083, product=0x162c) at libusb:001:009

And after scanimage -L it returns 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

The same situation, if I run commands with sudo. Are there any suggestions?

---

### Post by atarifreak on 2012-08-09
sorry about opening this again...
but i have same issue.
cant get 32 bit driver installed on 64 bit.
Canon will not help me (they said not  64 bit Linux support, only Linux Support...) and building that sane backend from source didnt work.
Or it worked without errors, but scanimage -L didnt find my scanner.

---

