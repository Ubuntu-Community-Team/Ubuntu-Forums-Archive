---
title: "Microtek phantom C6 - Ubuntu 10.10"
date: 2011-02-13
forum: Multimedia Software
---

### Post by kamelie1706 on 2011-02-13
hi,

I am pretty sure I have managed to get this work in the past.

sane-find-scanner returns
```

found USB scanner (vendor=0x05da, product=0x009a) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```scanimage -L returns
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```SANE project support seems to be there
[http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-MICROTEK](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-MICROTEK)
```
SlimScan C6 USB 0x05da/0x009a Complete    [microtek2]("http://karstenfestag.gmxhome.de/linux.html") (unmaintained)  [sane-microtek2]("http://www.sane-project.org/man/sane-microtek2.5.html")
Any idea where I should look to to proceed?
```

Thanks

---

### Post by linuxsyst on 2011-02-13
```
sudo apt-get install xsane
```
The Xsane program supports even more and it's better and faster it's installed to Graphics-Simple scan or Xsane Scanning program
I also had the problem with normal SANE but I found the XSANE

---

### Post by kamelie1706 on 2011-02-13
I have just tried xsane .... no devices found

---

